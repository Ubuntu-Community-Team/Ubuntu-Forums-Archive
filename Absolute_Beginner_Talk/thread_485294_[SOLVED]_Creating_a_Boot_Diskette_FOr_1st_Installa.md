---
title: "[SOLVED] Creating a Boot Diskette FOr 1st Installation"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by MelL on 2007-06-26
Hello, everyone! I'm new to Ubuntu and, wanting to get into Linux, decided to give it a go on an older machine I have sitting around, a Dell Optiplex GXMT 5133. The problem I have is this: since I cannot boot from a CD, I've had to et up a boot diskette. I used rawwritewin-0.7 to select sbm.bin on the CD I made for this operation.

Now, when I try to boot up with the CD and Diskette inserted, I get a blank screen. I am totally at a loss since the CD-diskette combo work just fine on another computer.

Are there any ideas or am I just out of luck with that machine? :(

---

### Post by louieb on 2007-06-27
You may be out of luck. Are you getting the Smart Boot Manager menu? 
or is it when you select your CD drive that things go blank? 
I've used it on some old machines in the past. Can't say why it not working for you. [Nuts on Smart Boot Manager]("http://louboldt.com/ilinuxsbm.htm")

---

### Post by the.phantom on 2007-06-27
what version of Ubuntu are you going to use?
i did a quick google and it looks like a pretty old system !
how much memory do you have in it?

and you say you can't boot from the cd?
did you look in the bios?
i saw that there is your system with cd drives

i doubt if you have enough memory for the standard Ubuntu?
it requires 256meg 
Xubuntu requires less but don't know how much you have on your system?

i have a 4oomhx with 384 and it is pretty slow but works

just trying to prevent a big mess and can't get it working ;-D

---

### Post by logos34 on 2007-06-28
> **MelL said:**
> Hello, everyone! I'm new to Ubuntu and, wanting to get into Linux, decided to give it a go on an older machine I have sitting around, a Dell Optiplex GXMT 5133. The problem I have is this: since I cannot boot from a CD, I've had to et up a boot diskette. I used rawwritewin-0.7 to select sbm.bin on the CD I made for this operation.

Now, when I try to boot up with the CD and Diskette inserted, I get a blank screen. I am totally at a loss since the CD-diskette combo work just fine on another computer.

Are there any ideas or am I just out of luck with that machine? :(

I had the same experience.  Also used rawwritewin (gui and dos mode).  The problem is an unreadable .img on the floppy.  I did mine on x64 windows so I chalked it up to some problem with 64-bit platform.

You might take a look at t[his page]("http://www.fdos.org/ripcord/rawrite/").  Try **fdimage** first.  You'll have to use it in the DOS mode.  Or if you can access a linux machine, you just use[ 'dd' and it works.]("http://http://linux.simple.be/tools/sbm")

---

### Post by ginestre on 2007-06-28
This helped me

[http://ubuntuforums.org/showthread.php?t=438153](http://ubuntuforums.org/showthread.php?t=438153)

---

### Post by speeddemon8803 on 2007-06-28
If you suddenly think that ubuntu isnt "booting up" because the bar isnt scrolling around...your computer just might not have enough RAM in it. I know this was the case with mine...if you have a few bucks..go and get more ram...if not..and im hoping you actually try this first..get Xubuntu...the website is [http://www.xubuntu.com](http://www.xubuntu.com). It is a great alternative to the normal Ubuntu dist. I have it on an older machine, has not failed since I installed it.

Anyways, enough of my blabbering, I hope my post helps fix this, if not, I will be back! Happy ubuntuing!

---

### Post by MelL on 2007-06-28
I'm thinking it was a memory issue: the machine has 64mb of RAM. :p

I was trying to install 7.04 Server Edition. I know, it sounds insane on a 64mb system, but I did at one time have Windows 2000 Advanced Server running on it as a web server.

Alas, I decided to put that system aside and try a more powerful system I had gathering dust.

Thanks for the help guys and see you in my next post asking for help! :)

---

