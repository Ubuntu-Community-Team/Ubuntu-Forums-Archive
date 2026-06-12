---
title: "owner issues that only root owns"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by ahrimano on 2007-02-04
Completely new to linux (have been drinking and tired and pissed) - trying to update to firefox2 on Dapper but the "**/opt**" directory says I have no permission (it is owned by "root" in group "root" for write only) - but I've only set one user/admin account - sooooo WTF do I need to do to get root access that I don't have as admin?  I hope this is a stupid question!

1)  What do I need to do to update firefox to 2.0.0.1?  I've been refering to [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

2)  What is the /opt dir for?

3)  I have 2 HD's but don't know their names/lables (it's a maxtor 6L080j4 but thats besides the point - it only comes up / next to "access path" in partition prop in disk manager). /C in a terminal comes up blank/no such directory etc -  is it /dev/hda1 as it is seems to be labeled in disk manager?

4)  Automatix - doesn't have an option to install firefox - wants me to use opera (I like mozilla - opera I thought was mac based - I'm techtarded here - but doesn't firefox kick more ***?)

5)  Is Edge any better - do I need to break down and buy a user manual for linux?

6)  I am going to drink the rest of this bottle of vodka - does linux and vodka mix?

THNX

---

### Post by yabbadabbadont on 2007-02-04
Use the sudo command as shown in the instructions to which you linked when extracting the tarball to /opt.

(It's not a stupid question if you don't know the answer...  :D)

---

### Post by ahrimano on 2007-02-04
THNX for the kindess!

This is what I get with the "sudo tar firefox-2.0.0.1.tar.gz -C /opt" cmd:

"
tar:  firefox.2.0.0.1.tar.gz:  Cannot open:  No such file or directory
tar:  Error is not recoverable:  exiting now
tar:  Child returned status 2
tar:  Error exit delayed from previous errors
"

firefox2 is on my deskt top - I'm going to take another shot.

wont let me cut or paste into the /opt dir either

I need to read some more but any help to jumpstart me would really help - I'm BASIC raised hehe. C64
,

---

### Post by aysiu on 2007-02-04
This will help you get Firefox installed automatically:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

This will help you understand how to work with permissions and ownership:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by closetpirate on 2007-02-04
at the start of the shell it usually defaults into the home dir /home/usrname
try: 

cd Desktop

then unpack the tarball

---

### Post by aysiu on 2007-02-04
Make your life easier.

Use the installation script I linked to in my last post.

Or... if you must use the [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) page, just copy and paste the instructions into the terminal. If you copy and paste those terminal commands as is, you shouldn't run into root/ownership issues. Retyping is for the birds.

---

### Post by yabbadabbadont on 2007-02-04
> **ahrimano said:**
> THNX for the kindess!

This is what I get with the "sudo tar firefox-2.0.0.1.tar.gz -C /opt" cmd:

"
tar:  firefox.2.0.0.1.tar.gz:  Cannot open:  No such file or directory
tar:  Error is not recoverable:  exiting now
tar:  Child returned status 2
tar:  Error exit delayed from previous errors
"

firefox2 is on my deskt top - I'm going to take another shot.

wont let me cut or paste into the /opt dir either

I need to read some more but any help to jumpstart me would really help - I'm BASIC raised hehe. C64
,
```
# extract the tar file into /opt (you should make sure /opt already exists)
 sudo tar xzvf firefox-2.0.0.1.tar.gz -C /opt
```
Do you see what you left out?

---

### Post by sacedric on 2008-01-03
Oh geez. Per the instructions on this page([http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)) under the Feisty section I ran 
sudo rm -rfd ~/Desktop/usr
Is that bad? :-( Dos this explain why root now owns my desktop?

---

