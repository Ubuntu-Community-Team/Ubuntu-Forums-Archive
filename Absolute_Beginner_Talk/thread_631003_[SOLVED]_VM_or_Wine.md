---
title: "[SOLVED] VM or Wine"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-12-03
Whats a better option for running lots of XP based applications Wine or just simply run a VM of XP ?

I am planning on building a new machine Quad Core, so I shouldn't be limited by the resources.  What is the best virtualization software to use in Ubuntu?

---

### Post by marpstar on 2007-12-03
it depends... check the compatibility of your programs at [http://appdb.winehq.org]("http://appdb.winehq.org")

I prefer to run Wine if I just need a couple programs, but if you're going to be running a lot of programs, you might be better off with virtualization.... 

I can't recommend anything for virualization, because I don't use it all that often.

---

### Post by wigglydiggly on 2007-12-04
I have been running both for a little while.  I'm my case I need to use IE to connect to works website.  I installed IE4Linux which uses WINE and works fine.  I also installed Virtual Box through the repos so now I can run a full version of XP.  Both work in my situation to get the job done.  IE4Linux is much quicker to load but runs slower, perfect for me.  There are certainitly application that would work better with Vitualization.  Your milage may differ depending on what you need/want to get done.

---

### Post by hyper_ch on 2007-12-04
if you have quad core, enough ram and diskspace there's not much objection to running it in a vm and keep the vm running all the time...

---

### Post by bodhi.zazen on 2007-12-04
In general, the more complex and diverse the windows applications you want to run the better off you will be with VM (or virtualbox or QEMU).

Why are you running all those windows programs on Linux anyway ? I would think it best to either migrate to Linux native applications where at all possible as a good first step. Dual booting is also an option.

---

### Post by BassKozz on 2007-12-04
Yah, I am planning on Dual-Booting, but I want to slowly migrate completely over to Linux, and if I can just boot into Ubuntu and only use a VM for necessary situations (where similar apps don't exits for linux) then I'll be happy :)

So is Virtual Box the best Virtualization software available for Ubuntu?

---

### Post by hyper_ch on 2007-12-04
I prefer VmWare... I just couldn't ssh from VB into my host system and vice-versa... furthermore I tend to think USB support in Vmware is also better - but that's my opinion.

---

### Post by subs on 2007-12-04
if u are running quadcore..... hav a lot of ram and are into using a lot of windoze apps..... then u shld go in4 vmbox..... its the thing 4 u!!:guitar:

---

### Post by Sethalos on 2007-12-04
> **hyper_ch said:**
> if you have quad core, enough ram and diskspace there's not much objection to running it in a vm and keep the vm running all the time...

I have Ubuntu on my Work Laptop, and wanted to use my Work Applications (Which were XP applications) to run all the time. I decided to use VirtualBox and I used this set of instructions for setting it up with XP.  Now it is totally integrated, and I can switch back and forth by using my Workplace Switcher.

I think this is what is ultimately your best option:

[http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

Enjoy

---

### Post by BassKozz on 2007-12-04
Ok thanks for all the feedback :D another quick question...
I am planning on installing the 64bit version of Ubuntu so that I can max out my system ram (4gigs and above in the future), can I run a 32bit version of WinXP in a VM? 
Also could I run 32bit winXP applications in Wine using Ubuntu 64bit ?

---

