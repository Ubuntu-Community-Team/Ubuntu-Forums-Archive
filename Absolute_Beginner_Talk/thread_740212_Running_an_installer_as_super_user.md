---
title: "Running an installer as super user"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Luffer on 2008-03-30
Hi,

Totally Ubuntu newbie here, I just installed it and managed to follow instructions to get my WLAN working which is an Atheros AR5007EG. Just followed the instructions to the letter and it worked, so I'm very happy about that!

Now I am attempting to get the ATI Radeon HD2600, I was told to get the driver from the ATI site which I've done. It's called:

ati-driver-installer-8-3-x86.x86_64.run

First of all I tried to run it and got an error:

"gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again"

After a bit more research I managed to solve this by going to permissions and allowing it  to execute as a program. But now I get the error:

"You need to run this installer as the super user"

But how do I do that? I discovered that it should be possible to go to the Terminal and run it from there, so I did the following:

$cd Desktop
$sudo ati-driver-installer-8-3-x86.x86_64.run

After entering my password that throws up the error:

"sudo: ati-driver-installer-8-3-x86.x86_64.run: command not found"

So I just have no idea what the next step is... the file is definitely on the Desktop, Here's the whole Terminal window posted:

james@james-laptop:~$ cd Desktop
james@james-laptop:~/Desktop$ sudo ati-driver-installer-8-3-x86.x86_64.run
[sudo] password for james:
sudo: ati-driver-installer-8-3-x86.x86_64.run: command not found
james@james-laptop:~/Desktop$ 
james@james-laptop:~/Desktop$ ls
ar5007eg-32-0.2                          fglrx-install.a11483
ati-driver-installer-8-3-x86.x86_64.run  ndiswrapper-1.51
james@james-laptop:~/Desktop$ 

It's all far too much for my poor brain to understand.......

---

### Post by Michael.Godawski on 2008-03-30
try in terminal
```
sudo upx -d filename.run
```

you might have to install upx via synaptic

---

### Post by Luffer on 2008-03-30
> **Michael.Godawski said:**
> try in terminal
```
sudo upx -d filename.run
```

you might have to install upx via synaptic

Hmm, i'll try, but can I ask what that command means? sudo is superuser right? But what's the upx -d bit mean... I am a newbie. Also how do I install upx via synaptic if I need to?

---

### Post by jcarlock on 2008-03-30
First, be sure that you want to be installing the 64-bit version of this driver.  I'm assuming your aware of whether your machine has a 64-bit processor.  Eitherway you need to put a ./ in front of any command you want to execute that is not in your executable PATH, for example, outside of /usr/bin /bin, etc...

you would need to run the following assuming the file is on your desktop, also a side note ~ represents your home folder, /home/<username>/...



cd ~/Desktop
sudo ./ati-driver-installer-8-3-x86.x86_64.run

I'm guessing you just double clicked it the first time, when it told you to run it as a super-user.

---

### Post by Michael.Godawski on 2008-03-30
upx:
> 
an efficient live-compressor for executables
UPX is an advanced executable file compressor. UPX will typically
reduce the file size of programs and DLLs by around 50%-70%, thus
reducing disk space, network load times, download times etc. The
current version can compress executables for DOS, Linux/ELF (i386,
amd64, ppc32) and some other files for different OS.

NOTE: This package is based on the UCL library, which is licensed under GPL.

Homepage: [http://upx.sourceforge.net/](http://upx.sourceforge.net/)
taken from the synaptic package description
just type into the search field of synaptic upx and check the box next to the entries for installation.

---

### Post by Luffer on 2008-03-30
Eeeek, no I want a 32bit version, which was what I thought I got from the ATI site.... Oh dear, back to the drawing board!

Yes, I did just double click originally.

---

### Post by jcarlock on 2008-03-30
Sorry.  It may not be only for 64-bit, but I would double check...  It says x86.x86_64, normally you want an i386 or similar, the _64 usually means its for 64-bit, but it may autonegotiate for either and would most likely tell you its not for that architecture.

JC

---

### Post by Luffer on 2008-03-30
Okay, just gone back to the ATI site, and it's given me the same file.... is that definitly the 64bit version? I don't understand much of this, Getting the 64bit version gives me the same file.... or at least they have the same name?

---

### Post by Michael.Godawski on 2008-03-30
You might also want to try envy which will install the ati drivers automatically for you.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Luffer on 2008-03-30
Thanks guys, just installed it using:

$ sudo ./ati-driver-installer-8-3-x86.x86_64.run

It auto-detected 32bit and installed the correct version, just need to hope everything still works after a reboot!

The help here is amazing, such fast responses.

Oh, and when I searched for upx in synaptic it didn't find any results....?

---

### Post by jcarlock on 2008-03-30
envy is a good option.  But works better for nvidia.  AMD is doing a better job of supporting the linux community.

JC

---

### Post by valpobro on 2008-04-11
i have the same problem but i can't get it to work i need a step by step how to

---

