---
title: "Ubuntu installation#3 has failed. No longer boots"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by S.D.K. on 2006-12-29
](*,) ](*,) ](*,) 

I have to use these symbols, as I don't think filling this entire thread with as many curses I can think of isn't going to help me.

I have played with Ubuntu 6.06 Drake for three days. Ever one of those days I have had to Reinstall Ubuntu because it no longers boots up for me.

This is gotten so bad that I'm ready to cancel using Linux and just stick to Windows.

However, it would be premature of me to do so I'm hoping to give it another chance as I honesty have no idea why Ubuntu keeps refusing to boot for me.

My last installation of Ubuntu I used the Alt. Installation Disk for Ubuntu 6.06 as it was suggested that the errors could be from me installing from a LiveCD.

Here are the specs of my Computer

Emachine T6216

Processor: AMD Athlon 64 3200+ [2.0 GHz]
RAM: 1.12 Gigabytes
Graphics Card: nVIDIA GeForce 6100
Master HHD 160 GB Windows XP
Slave HHD 100 GB Ubuntu 6.06

This is the error I get:

/bin/sh: can't access tty; job control turned off

Why do I get this error?
Each of the three times I have had Ubuntu fail on me was after I installed the updates needed, reset, gotten back on Ubuntu and used easyUbuntu [which it isn't for me] installed a few programs, reset computer and got back on Windows XP for little sister to do what ever she does, kick her out so I can got  back to Ubuntu.

This is the point where Ubuntu for all intent and purpose, dies on me.

Please help me.

---

### Post by Sef on 2006-12-29
Here's [Gentoo forum thread]("http://forums.gentoo.org/viewtopic-t-152855.html?sid=657f0bbf1fe140faf141b965bbf161ad") that talks about it and solutions.   Go down a bit and they will talk about GRUB.

---

### Post by NeoLithium on 2006-12-29
This is just my opinion, but i'd like to help you to have a good linux experience, not every time goes smooth, but BELIEVE us, it is worth the work.

Make sure you're using the X86_64 install disk, even if its the install; you have a 64 bit so it'll help you in the long run; and as far as I know, when you install you should use the generic Versa graphics driver until you can install the proper ATI card. Basically, I'd just say wait a few posts for the real super-guru's to be on and guide you; but just be patient, everyone can have some flaws with the install, but you'll end up not regretting the work for linux in the long run.

---

### Post by S.D.K. on 2006-12-29
So I should use the X86_64 install disk?
I would really not want to have to reinstall Ubuntu again unless I have to.
I'll leave it as a last resort.

Still why am I having these problems?
Some bug that I have?
Downloading stuff?
Using easyUbuntu?

---

### Post by Sef on 2006-12-29
> Still why am I having these problems?
Some bug that I have?
Downloading stuff?
Using easyUbuntu?

Click on the link that I provided in my last post and it will help you resolve your problem.  If you don't understand something, then post where you get stuck.

---

### Post by S.D.K. on 2006-12-29
Sef thanks for the help, but I have no idea what the post is discussing. :confused: 

Here are some of the things that come up with Ununtu fails to load:

17179586.460000 EXT3-fs error (device hdb1) ext_check_descriptions Invalid bitmap 
for group 384 not in gray (block 2147483647)!

Mount /dev/hdb1 on root failed: Invalid argument

mount /root/dev                     No Such file
          /sys                            No Such File
          /proc                           No Such file

Target filesystem doesn't have /sbin/int

---

### Post by confused57 on 2006-12-29
> **S.D.K. said:**
> Sef thanks for the help, but I have no idea what the post is discussing. :confused: 

Here are some of the things that come up with Ununtu fails to load:

17179586.460000 EXT3-fs error (device hdb1) ext_check_descriptions Invalid bitmap 
for group 384 not in gray (block 2147483647)!

Mount /dev/hdb1 on root failed: Invalid argument

mount /root/dev                     No Such file
          /sys                            No Such File
          /proc                           No Such file

Target filesystem doesn't have /sbin/int

Try install Ubuntu again, install the updates; however, use your system for awhile before attempting to use easyUbuntu to install programs(just to see if the problem occurs without using easyUbuntu)...I personally use automatix2(which works well for me):
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Install maybe 1 or 2 things at a time, rather than all at once...if I understand correctly, the problems occur after installing updates and using easyUbuntu.

---

### Post by S.D.K. on 2006-12-29
...crap...

I'll install it again, do the system updates and such, and just install codecs, flash, and java.

If after that I get another "can't access tty" error...

Well, I'll just be frustrated of all those hours to adjust Ubuntu would have been for nothing.
[:mutter:Christ, even Windows Me was more stable than this:mutter:]

---

