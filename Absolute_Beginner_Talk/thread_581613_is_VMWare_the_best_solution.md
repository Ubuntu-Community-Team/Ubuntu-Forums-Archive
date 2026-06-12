---
title: "is VMWare the best solution?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-19
I'm going to need a little help here.
After a few months trying Ubuntu, i think i'm ready to quit windows for good. But there's still some things that keep me from deleting windows from my hard drive.

1st - quicktime. I can't play a lot of files that need quicktime. I tried all the solutions presented, but none of them work

2sd - Internet Explorer. There are still many sites that only allow IE. I have IE4Linux, but still it's not the same.

lately, i have been reading about VMWare. But i don't really understand how to work with it. There's the server, there's the player and there's the workstation.
I just want to keep it simple and be able to run IE and Quicktime. What's the best solution?

I have Ubuntu Feisty 7.04

---

### Post by Frak on 2007-10-19
Use VirtualBox with Seamless Integration, that should solve your needs and save you ALOT of money. 
VMware costs alot of money, and is difficult for some users to install.
VirtualBox is precompiled, free, and has more features.
[http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb](http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb)

---

### Post by zhanglini on 2007-10-19
Is virtualbox better than Wine?  I might replace wine if it is.

---

### Post by loganm10 on 2007-10-19
vmware is a little tricky if you are new

What you want is vmware workstation:
[http://www.vmware.com/download/ws/](http://www.vmware.com/download/ws/)

You have to sign up on their site and whatever, but download that, choose the linux version, and get the "tar" version, not rpm, and 32bit or 64bit, whatever you have

So download that and extract it to whereever

You need a package called "build-essential" look for that in synaptic package manager and install it

then open a terminal (I know this will be a bit hard if you are new) and navigate to the folder that has all the vmware stuff you need (if you put it on the desktop the command "cd ~/Desktop/vmware*" without quotes would do it)

then type this: sudo ./vmware-install.pl

this will take a while and ask alot of questions, just keep pushing enter, it will display a license, you have to type yes, and then some more enters

once that is done you have vmware workstation on your computer!
It shows up in Applications>System Tools

From there is fairly straight forward, you need a windows install cd to use it, but ive typed too much already, there is alot out there on how to use vmware

---

### Post by loganm10 on 2007-10-19
virtual box/vmware is pretty different from wine, wine is used to run single programs, sometimes works sometimes doesnt

virtualbox/vmware emulate a complete windows system, all programs will work for sure, but its a little slower (you are running 2 OS's at once)

Also vmware workstation does cost alot, you get a 30 trial, but vmware player is free, so as long as you have your virtual machine setup in those 30 days, you can run it through the player for as long as you like

---

### Post by Frak on 2007-10-19
Seriously, just save the trouble of VMware and go for Virtualbox.
Its Free
More feature rich
Open Source (means security flaws are patched usually within a day)
For most users its Faster
Lighter interface

And it can run your Windows applications alongside your native Linux apps via Seamless Integration which VMware cannot do (at least yet)

---

### Post by loganm10 on 2007-10-19
VMWare FTW!

lol actually ive never used virtualbox, i think i might give it a try, I didnt even know there was an opensource alternative

---

### Post by Frak on 2007-10-19
> **loganm10 said:**
> VMWare FTW!

lol actually ive never used virtualbox, i think i might give it a try, I didnt even know there was an opensource alternative
Yes, Qemu and Virtualbox, Qemu Emulates (means creates ALL new hardware) and Virtualbox Virtualizes (Only emulates RAM and Processor).

Virtualbox has been considered a Professional Alternative.

---

### Post by Pulka on 2007-10-19
thank you all. I tried Virtual Box. Now i have questions concerning that use :)

[http://ubuntuforums.org/showthread.php?t=581763](http://ubuntuforums.org/showthread.php?t=581763)

---

### Post by Pulka on 2007-10-20
I'm amazed with virtual box. It's fast, works and solved my problems. Thank you all. I can drop windows partition for good.

---

