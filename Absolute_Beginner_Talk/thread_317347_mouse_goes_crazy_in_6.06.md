---
title: "mouse goes crazy in 6.06"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by 3rdgear on 2006-12-12
I have installed Dapper Drake 6.06 on one of my machines. I have a switch that allows me to use one keyboard, mouse, and monitor on up to 4 machines. 

My basic optical mouse will now randomly move all over the screen, clicking and selecting things. Mostly I get screen background changes. This is a new installation. I had it installed previously without problems, but added a hard drive and decided to completely reload again.

I have been trying to find answers on the forum, but most date back quite a ways, and most try different mouse(s?)etc. I have already tried a regular wheel mouse and get the same results, so it is not that.

---

### Post by sjnovick on 2006-12-12
I have run Ubuntu on 4 different computers.  My older laptop (256MB, Pentium 3, 600MHz) exhibits the same crazy mouse problem.  I have not found a solution to this problem.  On this particular laptop, I have successfully installed and used:  Kanotix 2005&2006, Debian 3.1 testing, PCLinux 0.93, and a few others.  Only Ubuntu causes the mouse problem.

One difference that sticks out (which I have not tried) is that the Ubuntu linux kernel is for x386.  The others are for x586 and x686.  Please try changing the kernel to use x686 (or whatever is optimal for your computer) and report back.

I have read other posts that suggest it may have something to do with "powernod".  I haven't tried this either, but pass it on as something to try.

Note:  I would try these myself, but have settled happily on running Debian testing on my laptop.  It works well and doesn't need any tweaking.

Good luck!

---

### Post by brn on 2006-12-12
I had the same problem several months ago with my Dell laptop.  I found the fix on this forum.  Here it is:
> Found the solution. It was in /usr/share/powernowd/cpufreq-detect.sh
 Changed it so it always load PIII_MODULE=speedstep-ich.


---

### Post by sachincool on 2006-12-12
actually i want help from u
is 6.06 is the only os u have
i have problem installing it for dual booting
I have winxp installed
i have started installing dapper for dual booting and ve come upto partitioning
but its showing me only2 options
1.completely erase h/d
2.manually edit partition

i selected 2nd one now its not showing me partition table
its showing me only one partition
what could b the problem
pls help me
Edit/Delete Message

i have put thread for this problempls see it

---

### Post by 3rdgear on 2006-12-13
> **sachincool said:**
> actually i want help from u
is 6.06 is the only os u have
i have problem installing it for dual booting
I have winxp installed
i have started installing dapper for dual booting and ve come upto partitioning
but its showing me only2 options
1.completely erase h/d
2.manually edit partition

i selected 2nd one now its not showing me partition table
its showing me only one partition
what could b the problem
pls help me
Edit/Delete Message

i have put thread for this problempls see it

I'm sorry, but I am not trying to do a dual boot. I have several machines, some with xp, and the others I am trying to load linux, so I don't have to pay exhorbitant fees to Micro Soft for XP.

I am guessing that the choice you made took the free space from the drive to make your linux partition, leaving your xp partition in place.

---

### Post by 3rdgear on 2006-12-13
> **brn said:**
> I had the same problem several months ago with my Dell laptop.  I found the fix on this forum.  Here it is:

Thanks for the feedback, will try it as soon as I get a chance.

---

### Post by 3rdgear on 2006-12-13
> **sjnovick said:**
> I have run Ubuntu on 4 different computers.  My older laptop (256MB, Pentium 3, 600MHz) exhibits the same crazy mouse problem.  I have not found a solution to this problem.  On this particular laptop, I have successfully installed and used:  Kanotix 2005&2006, Debian 3.1 testing, PCLinux 0.93, and a few others.  Only Ubuntu causes the mouse problem.

One difference that sticks out (which I have not tried) is that the Ubuntu linux kernel is for x386.  The others are for x586 and x686.  Please try changing the kernel to use x686 (or whatever is optimal for your computer) and report back.

I have read other posts that suggest it may have something to do with "powernod".  I haven't tried this either, but pass it on as something to try.

Note:  I would try these myself, but have settled happily on running Debian testing on my laptop.  It works well and doesn't need any tweaking.

Good luck!

Thanks for the feedback. Will try it as soon as I get a chance.... Off to work.

---

### Post by louieb on 2006-12-13
I have one of those PS-141B 4 port KVM switches that I got on EBAY. The mouse occasionally weirds out. Mostly when switching to the XP machine. ScrollLock ScrollLock M cures it most of the time. Other times I just have to switch to another machine then back.  What KVM switch are you using?

---

### Post by 3rdgear on 2006-12-16
> **brn said:**
> I had the same problem several months ago with my Dell laptop.  I found the fix on this forum.  Here it is:

:-k :-k I finally got around to trying this solution. Don't know if it will take care of it completely yet........

---

### Post by 3rdgear on 2006-12-16
> **sjnovick said:**
> I have run Ubuntu on 4 different computers.  My older laptop (256MB, Pentium 3, 600MHz) exhibits the same crazy mouse problem.  I have not found a solution to this problem.  On this particular laptop, I have successfully installed and used:  Kanotix 2005&2006, Debian 3.1 testing, PCLinux 0.93, and a few others.  Only Ubuntu causes the mouse problem.

One difference that sticks out (which I have not tried) is that the Ubuntu linux kernel is for x386.  The others are for x586 and x686.  Please try changing the kernel to use x686 (or whatever is optimal for your computer) and report back.

I have read other posts that suggest it may have something to do with "powernod".  I haven't tried this either, but pass it on as something to try.

Note:  I would try these myself, but have settled happily on running Debian testing on my laptop.  It works well and doesn't need any tweaking.

Good luck!

Well, I tried the other solution (powernod) :confused: given to me, apparently without luck. One thing to remember about ME is.... I am still an ABSOLUTE BEGINNER. How do I change the kernel?

---

### Post by brn on 2006-12-20
Sorry to hear the powrnowd entry didn't help.  One thing that sort of kept me on line while I was having this problem was to start in* rescue* (or is it *recovery*) mode from grub (I have a dual boot arrangement. I don't know what yours is or if this option is available except from grub. I'm a newbie too even though I've been using Linux for almost ten years.)  Anyway, from here I couild bypass the gnome desktop login and start with an old-fashioned 24x80 text screen.  Once the system was up and running, I could type "startx" which brought up a GUI of sorts from which i coulld run everything offered by gnome from the command line.  "Mousey" applications like browsers and email clients then did not exhibit the problem.

---

### Post by nix4me on 2006-12-20
The problem is your KVM switch.  Unfortunately all KVMs are not compatible.  I had this problem a long time ago with 2 different models; a belkin and a GWC.

I bought an IOGear KVM and the problem was solved.  There is quite a bit of information on this problem on the net, use google to confim.

nix4me

---

### Post by K.Mandla on 2006-12-20
Just to recap, I've also had problems with the powernowd package, but it was limited almost exclusively to older Dell laptops, and yanking that package solved it immediately. You can give it a shot with *sudo aptitude remove --purge powernowd* and if it doesn't solve it, you can put powernowd back with *sudo aptitude install powernowd*.

The KVM switch is also a culprit. A few years ago I had a cheap KVM that didn't retain a signal to the PC when it was switched away, and as a result I also got bizarre mouse movement when I changed back to a machine (this was under Windows, too). 

Try unplugging the KVM and using one machine at a time, just as a test measure. If you're still getting crazy mouse action, your KVM is probably okay. If the problem disappears, you might do well to invest in a newer switch.

Good luck. :D

---

### Post by sjnovick on 2006-12-27
Without powernod (# apt-get remove powernod), will the CPU runs full throttle all the time?  Is that bad?

---

### Post by sjnovick on 2007-05-03
It looks like the powernowd problem for my laptop was finally solved in 7.04!

In versions 6.04 and 6.10, enabling powernowd caused the mouse on my laptop to go crazy, moving up and down the screen and clicking on everything in sight.  Then after a few seconds, I would gain control of the mouse and have to close everything that became opened.

Doing  "apt-get remove powernowd"  took care of the problem in 6.04 and 6.10.

But, NOW with 7.04, powernowd works without causing the same problems on my laptop.  Unfortunately, on my poor old laptop, it uses too much RAM to do its job.  So, again, I removed it.  :D

---

