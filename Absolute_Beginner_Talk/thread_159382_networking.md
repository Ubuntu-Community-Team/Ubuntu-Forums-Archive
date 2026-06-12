---
title: "networking"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-12
i would like to know how to net work to ubuntu systems and 2 windows systems 

the windows ones keeps asking for a username and password same with ubuntu but the to ubuntu systems can't see each other..

any ideas?

---

### Post by Zimmer on 2006-04-12
Hi, try this guide, it solved my Samba issues.
[http://ubuntuguide.org/#sambaserver](http://ubuntuguide.org/#sambaserver)
Also , I have a few threads about which illuminate the Samba User issues.

You need a Samba User on the Linux box.
See these links for Info... post #10
[http://ubuntuforums.org/showthread.php?t=108950](http://ubuntuforums.org/showthread.php?t=108950)

This may be useful for you, too
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
and of course the troubleshooting section at Samba.org
[http://us4.samba.org/samba/docs/man/...diagnosis.html](http://us4.samba.org/samba/docs/man/...diagnosis.html)

---

### Post by WoodyMahan on 2006-04-12
I had this same username question.  What I did was go to Places->Connect to Server
Then I chose to connect to a Windows Share.  Then I had to enter a password.  I couldn't get it to accept my user and password.  Then I started looking closer at the messages and noticed that it was asking for a password to my ubuntu machine, I hit cancel and it asked for another user-password-domain.  The machine it was looking for in the second popup was the machine I was connecting to.  I entered the pertinent domain infor there and it mounted the drive on my desktop.  Started working fine.  Hope this helps.

---

### Post by aktiwers on 2006-04-12
I just got our network between our 2 Ubuntu computers up running today, and found out that in Ubuntu you will need to type in the password to connect.

For an example.

When Computer 1 connects to computer 2, I would have to type in the password that my user on computer 2 use to logon, from computer 1.

and

When Computer 2 connects to computer 1, I would have to type in the password that my user on computer 1 use to logon, from computer 2.

Understand what I mean?
Have you tried to do this?

Im not sure if its currect with windows networks, but it works fine here on Ubuntu to Ubuntu.

---

### Post by Herman on 2006-04-12
Try reading [this web page]("http://www.users.bigpond.net.au/hermanzone/p11.htm") and see if that helps you or not. 
That should tell you how to connect the two Ubuntu computers.

---

