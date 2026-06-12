---
title: "can't copy to remote server"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by dronug on 2005-11-09
im trying to ftp to my xbox when i go to places-> connect to server and i type in my xboxs ip address everything works fine.  i can see all the files on my xbox,  but i cant copy files to the xbox i can copy files from the xbox no problem.

i tryed to change the file permissions on the folder that pops up on the desktop,  but it says im not the owner and i cant change any permissions.

any help would be greatly appreciated.

---

### Post by KingBahamut on 2005-11-09
Probably because you dont have the proper permission to put files into your Xbox. Is your Xbox vanilla or modded? Installed linux on it?

---

### Post by dronug on 2005-11-09
its soft modded unleash x dashboard

ive ftped to it before in nautilus but it wont work anymore

---

### Post by n0ah420 on 2005-11-10
Try gftp. I've been using it with my xbox for a while without issues. Mainly to xfer a Xbox Media Center each time there is a new cvs snapshot. You can find it in synaptic. I also use FireFTP sometimes which is an extention for firefox. Make sure you have the proper IP address for your box and then connect, default username and password are usually xbox.  The FTP server on most modded boxes is a bit picky about which client you use to connect.

---

### Post by pochonox on 2005-11-10
me too i connect with ip static  i see the xbox but i can see the files ......my xbox is modded too help plz

---

### Post by n0ah420 on 2005-11-10
With what program are you connecting?  If your FTP server writeable and are you not logged in as annonymous?  The problem with using Nautilus is that by default it will connect read only unless you supply a username and password.  This is why I suggest using an actually FTP program like gftp.

---

### Post by pochonox on 2005-11-10
i try with gftp, the xbox with static ip ........but no connect ............help tell me a mini tutotial jejejejeje

---

### Post by pochonox on 2005-11-11
help plz

---

### Post by patrick295767 on 2005-11-11
-------------------
with mc:
-------------
with proftpd, u have rights by defaults to copy into the user folder : 
for instance : 
with mc:
/#ftp:user_lambda@IP_address
  
then enter ur passwd
then u'll have permissions in :
/home/user_lambda
   
---------------------
or u can use the ssh to send files ...(too)

---

### Post by n0ah420 on 2005-11-11
gftp is pretty straight forward. Put in the IP then username and passord and click connect. For most boxes this would be username : xbox password: xbox. If you are unable to determine the IP or login information check out:

[www.xbox-scene.com]("http://www.xbox-scene.com") 

for information regarding your particular dashboard.

---

### Post by arphe_el on 2005-12-06
here is my situation i want to copy other files to other linux ubuntu computer

computer_a with ip address 192.168.1.101 (my computer)
computer_b with ip address 192.168.1.102

the first thing i do is to type to the terminal this command
#ssh computer_b@192.168.1.102
password prompt:***
and ask me to connect yes/no: yes

then i can now access the computer_b

but i want to copy /home/computer_b/public (all folders and files into public folder)
so i type this command

computer_b:~/public$ scp -r /public computer_a@192.168.1.101:/home/computer_a/

after i enter the command it says that "port:22 connection refused lost connection"

any suggestion or what is the error is there anything wrong with my command ? 

i also try the gftp 

host:computer_b@192.168.1.102
user:computer_b
passwd:***

it says for FTP/HTTP
"Cannot look up hostname computer_b@192.1.168.108: Name or service not known"

it says for SSH2
"3: Protocol Initialization" and you have too wait long...

it says for FSP
"Waiting 30 seconds until trying to connect again"

of course for local it just go to your local desktop

any help shall be greatly appreciated

thanks for all the help GODspeed!

---

### Post by arphe_el on 2005-12-08
PTL! I already resolved the issue of copying files to remote computer

to connect to remote server

local_computer~#ssh root@ipaddress
passwd:*** (type your passwd)

to copy files from local computer to remote

local_computer~#scp root@ipaddress:/home/user /home (from target file to file to be saved)
password:*** (type your passwd)

from remote to your local computer

remote_computer~#scp /home/user root@ipaddress:/home (from target file to file to be saved)
Password:*** (type remote passwd)

note: you should do this using both root permissions (you should know the passwd of the root server)

hope this will help you. GODspeed! :-)

---

