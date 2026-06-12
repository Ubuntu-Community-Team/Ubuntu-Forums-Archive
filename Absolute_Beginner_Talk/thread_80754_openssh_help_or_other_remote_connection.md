---
title: "openssh help or other remote connection"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by shutupchuck on 2005-10-22
I have a ubuntu machine running an apache web server. 
I have a windows machine that I do most of my work off of.
I would like to be able to access the linux machine remotlely using the Windows machine.

My first instinct was openssh because that's what I've used in the past but when I tried installing it on the linux machine, i must've done something wrong because it didnt work and whenever i update ubuntu it gives an error message along the lines of:
error: openssh subprocess1

If anyone could help me undo what I did to the openssh daemon or suggest a different program to use, I would greatly appreciate it. Thank you.
-Chuck

---

### Post by Kyral on 2005-10-24
Well I have no clue what you did to the openssh server, but I can give you a Wikipage that shows you how to do it right ;D

[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

---

### Post by lreyes6 on 2005-10-25
I'm doing the same as you... this is what i did on ubuntu...

[LIST]
[*]sudo apt-get install openssh-server

[*]and on the windows machine i downloaded a program calle Putty from here [http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe) 

[*]then i just put the ip address of my ubuntu box on putty and hit connect
[/LIST]

---

### Post by ChrisTheGeek on 2005-10-25
It's always good advice but make sure you use strong passwords (at least 8 characters, different case, numbers, punctuation) for all accounts on your Ubuntu machine.  This is much more critical when allowing remote access via SSH since SSH servers are often subjected to 'dictionary' attacks where programs repeatedly try and guess a username/password that allow them access using a dictionary of common passwords.

The SSH server allows you many options to secure it further such as limiting access to particular users or even to set up public key encryption.   There is no need to be paranoid, but it's worth being aware of the security implications of running SSH.

---

### Post by Kyral on 2005-10-25
[QUOTE=ChrisTheGeek]It's always good advice but make sure you use strong passwords (at least 8 characters, different case, numbers, punctuation) for all accounts on your Ubuntu machine.  This is much more critical when allowing remote access via SSH since SSH servers are often subjected to 'dictionary' attacks where programs repeatedly try and guess a username/password that allow them access using a dictionary of common passwords.

The SSH server allows you many options to secure it further such as limiting access to particular users or even to set up public key encryption.   There is no need to be paranoid, but it's worth being aware of the security implications of running SSH.[/QUOTE]
Or setting up IPTables to only allow SSH connections from IPs you will be connecting from :D

---

### Post by cydizen on 2005-10-25
Another option that quite a few people at my work use is PuTTY.   Here is a link:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)


Regards,
Bruce

---

### Post by shutupchuck on 2005-10-25
Thanks for the replies everyone-
I tried doing **apt-get install openssh-server** but it said a bunch of stuff about **Could not load host key: /etc/ssh/ssh_host_rsa_key**. I won't paste all of it here unless someone wants it for clarification.
So I typed [B]ssh-keygen ssh_host_rsa_key
Generating 2048-bit dsa key pair
   9 oOo.oOo.ooOo
Key generated.
2048-bit dsa, chuck@mothership, Tue Oct 25 2005 18:18:10 -0400
Passphrase :
Again      :
Private key not written !
Public key not written !
[/B]

then i tried doing the apt get again but it did the same thing. 
please help.
-Chuck

---

### Post by iluminate on 2005-11-03
Hi all,

I'm trying to set up OpenSSH and I must admit that I'm a newbie when it comes to this and Linux :)
Have followed some tutorials and How-To's. By default is the port set to 22?
The thing is that I'm using Putty to test to see if everything is working but when I'm trying to login everythings goes really slow (takes approx 5 min to recieve "login as" in Putty.
So obviously something is wrong.
Do I have to open up port 22 in Ubuntu? (port 22 is open in the hardware router)
Any info would be appreciated!
Cheers

EDIT
Thanks anyways, but it all workes fine now.

---

### Post by iluminate on 2005-11-08
Hi,

I did a complete reinstall of Breezy because I messed things up and found it more easy to do a fresh install than fixing the problems I had.
Now I still have problems with the darn SSH.
It should be straightforward to get it to work,but I really don't know what the hell is going on.
In the router I have configured and forwarded the PORT 22 to the Ubuntu Server (192.168.0.5)
But when I try to connect from a win machine by using PUTTY I get "server unexpectedly closed the connection"
This I recive all the time.....
Someone else with the same problem??

---

### Post by patrick295767 on 2005-11-08
[QUOTE=shutupchuck]I have a ubuntu machine running an apache web server. 
I have a windows machine that I do most of my work off of.
I would like to be able to access the linux machine remotlely using the Windows machine.

My first instinct was openssh because that's what I've used in the past but when I tried installing it on the linux machine, i must've done something wrong because it didnt work and whenever i update ubuntu it gives an error message along the lines of:
error: openssh subprocess1

If anyone could help me undo what I did to the openssh daemon or suggest a different program to use, I would greatly appreciate it. Thank you.
-Chuck[/QUOTE]
     
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

---

### Post by patrick295767 on 2005-11-08
[QUOTE=shutupchuck]Thanks for the replies everyone-
I tried doing **apt-get install openssh-server** but it said a bunch of stuff about **Could not load host key: /etc/ssh/ssh_host_rsa_key**. I won't paste all of it here unless someone wants it for clarification.
So I typed [B]ssh-keygen ssh_host_rsa_key
Generating 2048-bit dsa key pair
   9 oOo.oOo.ooOo
Key generated.
2048-bit dsa, chuck@mothership, Tue Oct 25 2005 18:18:10 -0400
Passphrase :
Again      :
Private key not written !
Public key not written !
[/B]

then i tried doing the apt get again but it did the same thing. 
please help.
-Chuck[/QUOTE]
  
  
with mc, u can delete the folder :
.ssh
that will make u another key for doing ssh ...
(in case u messed up with ur user .ssh stuffs)
  
or adduser USER1
  
then do: 
ssh IP_PC -l USER1
then, it should help u...

let us know about ur progresss !
  
Pat'

---

