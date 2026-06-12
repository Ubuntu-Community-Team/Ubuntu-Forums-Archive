---
title: "User Accounts"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by KOTAPAKA on 2007-11-10
Hello I made a very dumb thing which I regret now but :). What I made is that I changed the permissions for my account from the user accounts menu so now I have no permissions to do anything. How do I change it - I am the root user but I can't log in as root and have GUI. So tell me how to do it from the Terminal and please tell me how to login as root every time because I am sick of messages that I have no permission to do something whatever it is.
I have Ubuntu 7.10.

---

### Post by ardchoille42 on 2007-11-10
> **KOTAPAKA said:**
> Hello I made a very dumb thing which I regret now but :). What I made is that I changed the permissions for my account from the user accounts menu so now I have no permissions to do anything. How do I change it - I am the root user but I can't log in as root and have GUI. So tell me how to do it from the Terminal and please tell me how to login as root every time because I am sick of messages that I have no permission to do something whatever it is.
I have Ubuntu 7.10.

You can't log in as root because the root account is locked, unlocking the root account can cause more problems. Please learn how to care for your system the correct way by using sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by KOTAPAKA on 2007-11-10
10x man I fixed it. Cheers

---

### Post by warmwaddle on 2007-11-10
Sounds to me like your screwed. Sorry about that, I did that once with Xubuntu on Virtualbox, and had to wipe the hard drive clean and restart.

---

### Post by KOTAPAKA on 2007-11-13
Hi all. I have the following problem: I put linux on mu computer (UBUNTU 7.10) and in the first load it was OK - I could do anything I wanted no limitations. Then I started getting messages such as "You cant move the folder - you have no privileges" or something of the sort and it says only the root can move it as he is the owner. Well ok But I AM the owner I am the root. I cant unmount a volume for the same reason. Any suggestions?

---

### Post by arpanaut on 2007-11-13
Here's a couple of links that will help you out, 


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by mysticrider92 on 2007-11-13
On Ubuntu, there is no root account by default. Your user has sudo privleges, but not root access without a password.

What specific files are you trying to move? You should always have full permissions in your /home/<user> folder. 

As for unmounting volumes, is it mounted on /mnt/*** or /media/<name of mounted device>? You have permissions to do anything in /media, but /mnt/ requires root access.

---

### Post by Myssei on 2008-02-01
That's not too comforting... I did the same thing as the OP user, the problem, though, is that the user I'm now logged in as doesn't have rights to change computer configuration. I tried using sudo, but the commands simply don't work (after I hit enter, next line appears - and that's all).

Do I really need to reinstall the system? I DO know the root password, it's just the system wouldn't even ask me for it...

EDIT: I just tried to open Rhytmbox via gksudo, just to check. It asked me for password, but then said that sudo configuration for my profile does not let me open this application as root. So, is reinstalling really the only option...?

---

### Post by Myssei on 2008-02-02
Bump.

Sorry, I just don't want to start a new thread.

---

### Post by jken146 on 2008-02-02
If you reboot and choose 'Recovery Mode' from the GRUB menu, you will be logged in as root.

---

