---
title: "Networking questions"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by Swoop on 2005-06-06
Okay, first off let me start by saying hello.
Im pretty new to linux in general, at least to sticking with it. Had several linux distros installed on my laptop over the last 2 years, but none ever got used much and slowly got faded out in favor of windows because i didnt know how to accomplish the simple household tasks i needed in linux yet and thus needed to use windows most of the time anyways :(

Anyways now i took the big sted and switched totally to ubuntu on the laptop, with no xp.. so no options exept the linux way .. better get it down now ;)

Anyways i have a couple of questions that i hope i can get some good clean simple answers to.. im pretty new to almost everything, and so far searching and googling only got me a little more confused.. ;)

Ubuntu here is on my laptop...
My stationary computer is (untill i know ubuntu better on the laptop) winxp
My friend has a server (just a regular machine that i will have access to) also running ubuntu.

What i need is answers to the easiest ways to do the following.

Transfer files back and forth between each machine. Assuming SAMBA is the way to go on the laptop vs. home machine, but how does that go with the remote machine ? How about FTP servers .. which to choose, and how to setup.. remember really newbie at this please ;)

Secondly the remote machine is going to be running Azureus (pr example) that i also need to be able to control remotely. Thus i can login to the server and setup files for downloading, clear out downloads ect. 
How do i accomplish this easiest ? Here im looking for solutions for both sides.. 
My guess is that im going to ssh to his machine but how do i get the graphical interface then ?

Thirdly i would love it if there was some kind of graphical interface to help control ftp users ect, monitor people logged onto the ftp server ... again im really new to linux, and usually in windows each program has eveything needed.. in linux it seems to me things are split up more... 

Anyways i hope some kind people will be able to lead me down the correct path here, after reading my little novel ;)
Sorry if posted in the wrong forum, but i thought beginner was the place to begin.

Again thanks for the help in advanvce :D

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=Swoop]Okay, first off let me start by saying hello.
Im pretty new to linux in general, at least to sticking with it. Had several linux distros installed on my laptop over the last 2 years, but none ever got used much and slowly got faded out in favor of windows because i didnt know how to accomplish the simple household tasks i needed in linux yet and thus needed to use windows most of the time anyways :(

Anyways now i took the big sted and switched totally to ubuntu on the laptop, with no xp.. so no options exept the linux way .. better get it down now ;)

Anyways i have a couple of questions that i hope i can get some good clean simple answers to.. im pretty new to almost everything, and so far searching and googling only got me a little more confused.. ;)

Ubuntu here is on my laptop...
My stationary computer is (untill i know ubuntu better on the laptop) winxp
My friend has a server (just a regular machine that i will have access to) also running ubuntu.

What i need is answers to the easiest ways to do the following.

Transfer files back and forth between each machine. Assuming SAMBA is the way to go on the laptop vs. home machine, but how does that go with the remote machine ? How about FTP servers .. which to choose, and how to setup.. remember really newbie at this please ;)

Secondly the remote machine is going to be running Azureus (pr example) that i also need to be able to control remotely. Thus i can login to the server and setup files for downloading, clear out downloads ect. 
How do i accomplish this easiest ? Here im looking for solutions for both sides.. 
My guess is that im going to ssh to his machine but how do i get the graphical interface then ?

Thirdly i would love it if there was some kind of graphical interface to help control ftp users ect, monitor people logged onto the ftp server ... again im really new to linux, and usually in windows each program has eveything needed.. in linux it seems to me things are split up more... 

Anyways i hope some kind people will be able to lead me down the correct path here, after reading my little novel ;)
Sorry if posted in the wrong forum, but i thought beginner was the place to begin.

Again thanks for the help in advanvce :D[/QUOTE]
 For exchanging files between laptop and server, I'd suggest using sftp (secure version of ftp, based on ssh). You will need to install sshserver on ubuntu server, then you can use Nautilus the file manager to connect to ssh server, using "connect to server" in Places menu. There are also windows clients for sftp. 

There are also solutions for automatically synchornizing files on two Linux machines. My favorite is unison. 

As for running graphical program on server via remote login, it can also be done by logging through ssh: it can send the graphics through the network so that an app is running on the server but the window shows on your laptop (it is called "forwarding", or "tunneling"). I do not remember precise syntax, though. Beware: unless you have a very fast connection, it will be slow as hell: you click a mouse, and a button reacts in several seconds. 

If I have time later, I'll post more detailed instructions.

---

### Post by Swoop on 2005-06-07
Thanks i hope you do post some more detailed instructions.
Im gonna start looking around for sftp, and how to setup sshserver on both laptop and server machine ;)

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=Swoop]Thanks i hope you do post some more detailed instructions.
Im gonna start looking around for sftp, and how to setup sshserver on both laptop and server machine ;)[/QUOTE]
 For running graphical apps remotely: assuming your server is runnign an ssh server, you can just type on your laptop 
ssh -X <username>@<servername.domainname>
(e.g. ssh -X [email]me@my.computer.com[/email])
it will give you a terminal. You can now launch any graphical application by typing the corresponding command (e.g. "firefox") and the application window will open on your laptop display. 

Installing ssh server is discussed here: [http://ubuntuguide.org/#sshserver](http://ubuntuguide.org/#sshserver)
You only need to do it on the server: on laptop, you only need ssh client, not server.

---

### Post by Swoop on 2005-06-07
Well i actually figured out the ssh part.. even think i got sftp down ... 

My big problem is getting any ftpd running.. well at least configuring for anything else exept anonymous access.
I just dont get why config files need to be edited manually which to me seems like a really unefficient way ot managing users and their permissions on the server.

Tried to install Webmin with the proftpd but i cant seem to login to webmin.. tried to use the .pl script that changes the admin password, but nothing helps. Just keep getting told that login is incorrect, and after 3 tried get locked out for 5 mins :(

Just dont seems resonable that with all the ftpd i have found none have gui or antyhing alike to help newbies or just people manage multiple users to ftp :(

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=Swoop]Well i actually figured out the ssh part.. even think i got sftp down ... 

My big problem is getting any ftpd running.. well at least configuring for anything else exept anonymous access.
I just dont get why config files need to be edited manually which to me seems like a really unefficient way ot managing users and their permissions on the server.

Tried to install Webmin with the proftpd but i cant seem to login to webmin.. tried to use the .pl script that changes the admin password, but nothing helps. Just keep getting told that login is incorrect, and after 3 tried get locked out for 5 mins :(

Just dont seems resonable that with all the ftpd i have found none have gui or antyhing alike to help newbies or just people manage multiple users to ftp :([/QUOTE]
 Do you really need ftp server? If yes, you probably need to ask the question in [Ubuntu server forum](http://ubuntuforums.org/forumdisplay.php?f=45)

---

### Post by Swoop on 2005-06-08
Well i guess not since i cant get it working anyways...  so not really an option.. dont like wasting my time on such a simple thing that should really just be working ;)

Anyways thanks for the help :D and i will find correct forum from now on ...

---

