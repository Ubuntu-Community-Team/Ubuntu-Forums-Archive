---
title: "superuser priviledge, how- where?"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by EvilBill on 2005-11-06
I need to know how to get this 

I "su" in the command line & it asks for a password. I put in my normal one that seems to work for other stuff but it does not here. I have MPlayer mostly installed & need to install w32codec all, it is ready, the other thing I did worked. 

[see post here for details](http://www.ubuntuforums.org/showthread.php?t=75817&page=2&highlight=mplayer)

I a am getting close, I can feel it. :eek: :???:

---

### Post by aysiu on 2005-11-06
Have you read this?
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by gord on 2005-11-06
try using 'sudo' instead of su, its a nicer way of doing things :)

---

### Post by EvilBill on 2005-11-07
I typed in sudo, it gives me the same thing about super-user priviledges. I have those codecs ready, I wish I could install them. I got MPlayer [most I think] installed it didn't ask for any su or sudo.

This is massive brain strain on my almost 50 year old brain.:( 

I read that page, I can't make any sense out of it. How do I get it to accept a password?

---

### Post by gord on 2005-11-07
that page is just a fancy complicated way of saying 'use sudo, not su' ;)

could you give more info on what specific command your having trouble with?

if its the command 'dpkg -i w32codecs_20050412-0.0_i386.deb' your having trouble with, make sure your file permisions are set right by typing ```
sudo chmod 754 w32codecs_20050412-0.0_i386.deb
```

---

### Post by EvilBill on 2005-11-07
> **gord]that page is just a fancy complicated way of saying 'use sudo, not su'  said:**
> 
I am trying to install this codec pack so I can play an mp3 with Amarok, and I think MPlayer needs them as well. 
> 
Install them with
Code:

dpkg -i w32codecs_20050412-0.0_i386.deb

.........and I am trying to install MPlayer plug- ins as well

[quote]1.2 install it

Code:

dpkg -i mplayerplug-in_3.11-1_i386.deb



[original thread is here](http://www.ubuntuforums.org/showthread.php?t=75817&page=2&highlight=mplayer)

---

### Post by aysiu on 2005-11-07
```
dpkg -i mplayerplug-in_3.11-1_i386.deb
``` isn't going to work. You need to do ```
sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
``` Use the password of the first user you created when you installed Ubuntu--that's the sudo password. There is no root by default.

---

### Post by EvilBill on 2005-11-07
It unpacks then asks me for a command 
I put in my root password, & it says no way.

The only things I have is 

-full username
-username
-password

I have tried them all, nothing works.

But on the bright side I got XMMS player to play my mp3 files, that useless Amarek won't, I don't know why I even d/l'd that thing, I knew it would never work.

---

### Post by aysiu on 2005-11-07
Why do you have a root password at all? Did you do an expert install?
If you do a regular installation of Ubuntu, you should not have a root password.
You should have one user with one password and that user's password is the password for sudo commands.

---

### Post by EvilBill on 2005-11-07
I did the simple install, not expert.
I have one password, that I use. I use it for permission in "Synaptic Package Manager" & it allows me.

It is the same one I log in with after my username. Although I went & cjhnged that to auto log-in.

There was a big long # at the start of the install, something about internet # or I don't know, I just pushed enter with the # the machine put there intact.

---

### Post by aysiu on 2005-11-07
Okay, if your password works with Synaptic, it should work with dpkg as well. Please post the exact output of the following commands. Don't describe the errors. Post the exact errors. Just copy and paste what's in your terminal:

```
ls
sudo sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
```

---

### Post by EvilBill on 2005-11-07
william@S010600508d4b91ba:~$ ls
Desktop                         mplayerplug-in_3.11-1_i386.deb.1
Files - Audio                   Ubuntu 5.10
Files - Video                   w32codecs_20050412-0.0_i386.deb
mplayerplug-in_3.11-1_i386.deb
william@S010600508d4b91ba:~$ sudo sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
(Reading database ... 65566 files and directories currently installed.)
Preparing to replace mplayerplug-in 3.11-1 (using mplayerplug-in_3.11-1_i386.deb) ...
Unpacking replacement mplayerplug-in ...
Setting up mplayerplug-in (3.11-1) ...
william@S010600508d4b91ba:~$ detroit
bash: detroit: command not found
william@S010600508d4b91ba:~$

---

### Post by aysiu on 2005-11-07
[QUOTE=EvilBill]
william@S010600508d4b91ba:~$ sudo sudo dpkg -i mplayerplug-in_3.11-1_i386.deb
(Reading database ... 65566 files and directories currently installed.)
Preparing to replace mplayerplug-in 3.11-1 (using mplayerplug-in_3.11-1_i386.deb) ...
Unpacking replacement mplayerplug-in ...
Setting up mplayerplug-in (3.11-1) ...[/quote] Okay, reading this output, it says to me that mplayerplug-in was successfully installed.

> 
william@S010600508d4b91ba:~$ detroit
bash: detroit: command not found
william@S010600508d4b91ba:~$ Why are you typing *detroit*? What is detroit?

---

### Post by EvilBill on 2005-11-07
william@S010600508d4b91ba:~$ ls
Desktop                         mplayerplug-in_3.11-1_i386.deb.1
Files - Audio                   Ubuntu 5.10
Files - Video                   w32codecs_20050412-0.0_i386.deb
mplayerplug-in_3.11-1_i386.deb
william@S010600508d4b91ba:~$ sudo sudo dpkg -i mplayerplug-in_3.11-1_i386.deb





It says that before I press any keys............:???:

---

### Post by EvilBill on 2005-11-07
Why are you typing ? What is 

"xxxxx

---

### Post by aysiu on 2005-11-07
I highly recommend against giving out your password over the internet. Please change it to something else now. Everybody on these forums now knows your password.

So. Problem solved, right? The plugin installed.

---

### Post by EvilBill on 2005-11-07
> Files - Video w32codecs_20050412-0.0_i386.deb

Even these guys are installed? I went & looked in the area where it shows everything imstalled, I found all the MPlayer stuff, I didn't see the codecs listed, but if my wmv files are playing as well as mp3 files, I guess it means a.o.k.



* I changed my password. I guess that was not too bright to say that,  :???: :razz: 

Thank you for the help. This is the first time in 7 years of computer use, I ever installed anything this way. I was previously using SuSE & those rpm's.....those are pretty simple.

---

### Post by aysiu on 2005-11-07
[QUOTE=EvilBill]Even these guys are installed? I went & looked in the area where it shows everything imstalled, I found all the MPlayer stuff, I didn't see the codecs listed, but if my wmv files are playing as well as mp3 files, I guess it means a.o.k.[/quote] No. You see how you type sudo dpkg whatever for the mplayer plugin? You have to do a separate sudo dpkg whatever for all the other individual .deb files.

> 
Thank you for the help. This is the first time in 7 years of computer use, I ever installed anything this way. I was previously using SuSE & those rpm's.....those are pretty simple. Yeah, there are some helper apps that can supposedly manually installed .deb files graphically, but they're not naturally part of Ubuntu. Fortunately, most stuff you'll need (not proprietary codecs) are in the repositories, and you can install them easily through apt-get. For more info on different ways to install software in Ubuntu read [this](http://www.psychocats.net/linux/installingsoftware.php).

---

