---
title: "[SOLVED] installing valgrind"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mouko on 2007-11-09
~/Documents/cs306/lab4> valgrind
The program 'valgrind' is currently not installed.  You can install it by typing:
sudo apt-get install valgrind
bash: valgrind: command not found

~/Documents/cs306/lab4> sudo apt-get install valgrind
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package valgrind
~/Documents/cs306/lab4> 

wtf?  Anyone know what is going on here?

On a side note, I installed drivers for my BCM4318 card (gasp! type "ubuntu BCM4318" in google for two eternities of reading) and it definitely is seeing the card, but there are no visible networks under "Wireless Networks."  I used to see some in Windows all the time.  Is something wrong?

---

### Post by skymera on 2007-11-09
sudo apt-get update && sudo apt-get upgrade

sudo apt-get install valgrind

---

### Post by meborc on 2007-11-09
hmm... valgrind is there... i did a quick apt-cache search... and it is there... are you sure you have all the repos enabled? open your /etc/apt/sources.list file and take # off from those lines ONLY that start with deb...

the sudo apt-get update and sudo apt-get install valgrind

---

### Post by mouko on 2007-11-09
Thanks guys, it's all good now.  I even installed it while ssh'ing in from the computer lab next door. :)  

Might've been all for nought though.  I don't wanna sound like one of those idiotic newbs (even though that's what I am) when I say that, with all these problems I'm having with my wireless card, I'm not sure linux is the right choice.  When I go home over Thanksgiving and then Christmas break, the only connection I can get is wireless, and if I can't get a connection, then that is a HUGE minus in the ubuntu column.  

I've followed all the steps and still am not seeing any wireless LANs.  If I can't get this thing working in the next week, I'll have to welcome back XP onto my computer.  Sure, it lacks tremendously next to Ubuntu, but definitely not in the networking department.

---

### Post by mouko on 2007-11-09
Nothing?  I thought my "windows > linux" tangent would attract all the linux defenders.  I'll tell you what, I'll let anyone who can help me with my wireless ssh into my computer!  YOU HEAR THAT?!?!? You can ssh in and solve the problem for me!!!!!  And install a rootkit while you're at it!  I don't even mind, I just want my wireless to work.

No, seriously though, if I can't get this to work I will get a full-chest tatoo of the Windows logo, a Tux tatoo will that cute little penguin hanging dead on a rope, and run through the streets proclaiming the superiority of Windows!  So what do you say?


[quote=mycomp]eth1      IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/quote]

Do those zeros in the third to last line indicate a problem?

---

### Post by mouko on 2007-11-09
I suppose I'll mark this one as solved and just open a new thread.  Nothing beats clutter.

---

