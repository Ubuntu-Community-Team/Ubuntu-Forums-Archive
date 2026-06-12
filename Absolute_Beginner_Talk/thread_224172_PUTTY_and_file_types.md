---
title: "PUTTY and file types"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by tc3racer on 2006-07-27
i anm thinking of downloading putty for lunux but i don't know which option to choose i have read about it on the putty website but like normally when you download files for windows it will normal comes down as an exe or zip etc.. could someone please tell me how putty works and which option is best for remote desktop coverage and also what do linex files types are for programs and installion programs eg exe for windows;)

---

### Post by KillrBuckeye on 2006-07-27
My understanding is that Putty is a client software that allows you to access other computers remotely using the SSH protocol.  I think you'd be better off telling us what exactly you want to achieve before asking questions about what to download.  For instance, if you just want to access your Linux machine from a Windows machine, you only need Putty on the Windows machine.  On the Linux machine, you would just install the SSH server.

---

### Post by tc3racer on 2006-07-27
how do i put a ssh server on linux what it is i have never used linux before my aim is to create a webserver for web pages and ftp with ubuntu server 6

---

### Post by tc3racer on 2006-07-27
sorry  to bother you all can some one have a look at the putty and an file types thread as i am not sure what ssh id what i do with putty on windows how it works and is it easy to configure how to i start an ssh on linux i have never used linux before and does linux have a gui interface for remote control or is it all  command line:confused:

---

### Post by KillrBuckeye on 2006-07-27
Well, the main reason you'd want to use SSH is if you want to be able to administer your Linux computer/server remotely.  This way you don't have to keep a keyboard, mouse, and monitor hooked up to it.  However, if you plan to keep a keyboard, mouse, and monitor hooked up, then there's really no need to set up SSH unless you want to administer the computer while you're away from your house or office.  SSH is not used for setting up a web server or ftp server, only for more convenient administration.  At least that's my understanding based on limited knowledge.

---

### Post by tc3racer on 2006-07-27
can i set up ftp and user it as a web server with ubuntu server 6 and what is ssh

---

### Post by KillrBuckeye on 2006-07-27
I don't have experience setting up web or ftp servers, sorry.  SSH is a protocol for secure communication between machines.  You install SSH server on a machine that you want to control/administer remotely, then you install an SSH client, such as Putty, on the machine from which you want to access it.  So, as I said before, if you want to control your Linux machine from a Windows machine, you should install the SSH server on the Linux machine, and install Putty on the Windows machine.

---

### Post by tc3racer on 2006-07-28
ok would you be able to install an ssh client or whatever its called on linux is it already installed on linux or not;)

---

### Post by avtolle on 2006-07-28
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=136](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=136) links to a forum on networking which likely contains the answers to your questions. Good luck.

---

