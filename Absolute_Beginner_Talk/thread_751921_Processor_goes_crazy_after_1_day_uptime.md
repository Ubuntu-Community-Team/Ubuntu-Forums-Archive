---
title: "Processor goes crazy after 1 day uptime"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Jarramundi on 2008-04-11
Hey guys, I'm an absolute Linux Newbie (and loving it!) but I've noticed something strange. After one days uptime my computers processor just starts to go through the roof (constant 100%). I am using a 3.4 Ghz P4 with 1GB RAM, which I'm told should be more than enough to run Xubuntu Gutsy.
 
This is what my top says is using all trhe processor.
4949 root      25   0  313m 115m 9216 R 98.9 11.5 114:36.65 Xorg


Xorg is using 98.9 % of my processor? constantly? Surely that's too much, please help.

---

### Post by quinnten83 on 2008-04-11
Ok, not my area of expertise, but xorg might be broken or you might have hardware connected that might be giving it trouble. Check to see that all of your hardware is compatible.
there is a command to reconfigure Xorg.conf. You could make backup of this one and then run the reconfigure. If it does not work you can always put the old one back.
Sorry I can't be of more help, but for the life of me, I would not know what is amiss.

---

### Post by Jarramundi on 2008-04-11
Quote: there is a command to reconfigure Xorg.conf. You could make backup of this one and then run the reconfigure. If it does not work you can always put the old one back.

Ok, please explain to me the code to do this. (extreme newbie)

---

### Post by kesman on 2008-04-11
To make a backup of your current XORG settings:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

```
and to reconfigure your xorg:
```

sudo dpkg-reconfigure xserver-xorg

```

also you could run updates just to see if there's an updated version of xorg:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
those are two separate commands. Copy only one line at a time.

---

### Post by Jarramundi on 2008-04-11
jarramundi@Jarramundi:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for jarramundi:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080411160453

Still at 100%

---

### Post by buried on 2008-04-11
Must be a bug...espicially on Xubuntu?

---

### Post by kesman on 2008-04-11
Of course you must either restart your computer or restart XORG for the changes to take effects. To restart xorg, press ctrl+alt+backspace or in terminal, type
```

sudo /etc/init.d/gdm restart

```

---

### Post by buried on 2008-04-11
Xubuntu shouldn't be using up all resources even if you have 3.2 ghz, It is very extremely unlikely to happen.

---

### Post by NightwishFan on 2008-04-11
This happens to me if I install with a bad cd. As in I install, notice the problems and run a disk check and realize there are errors. Perhaps check the integrity of your live cd.

---

### Post by Jarramundi on 2008-04-11
Ok. Now, I've made a mess of it. When I restarted everything was Ok, processor was back to 1-2 %, but the problem never show up until after 1 days uptime anyway. BUT, I must have configured the mouse settings wrong because my mouse has stopped working. I'm writing this on my housemates computer because I have absolutely no idea how to navigate xubuntu without a mouse. can someone tell me how to get a terminal up without a mouse? Also please tell me what the correct configuration should be for a USB mouse. 

Damn!

---

### Post by kesman on 2008-04-11
Hit alt+f2 and run xterm to open terminal.
You should select imPs/2 or whatever the default is for mouse. Did you change the setting from what it was? Luckily you took a backup from your xorg.conf, since now would be a great time to restore it.
```

sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

```
and then restart your xorg.

---

### Post by Jarramundi on 2008-04-11
Yep, that worked. Thanks a lot. I guess the only thing now is to see whether or not the problem is solved, which may take 24 hrs.

---

### Post by kesman on 2008-04-11
did you run
```

sudo apt-get dist-upgrade

```
as I suggested?

---

### Post by Jarramundi on 2008-04-11
jarramundi@Jarramundi:~$ sudo apt-get dist-upgrade
[sudo] password for jarramundi:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jarramundi@Jarramundi:~$

I have noticed that quite often my proc. hits 100% even on simple tasks...  Beginning to wonder.

---

### Post by Jarramundi on 2008-04-14
Ok still having problems... Seems to be between Xorg and Gnash.... Would really like a solution because suffering hard crashes. Please oh wise buntu gurus.

---

### Post by Jarramundi on 2008-04-15
top - 20:30:06 up 1 day, 36 min,  1 user,  load average: 1.27, 0.68, 0.43
Tasks: 111 total,   4 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s): 99.3%us,  0.7%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027508k total,   841892k used,   185616k free,    46496k buffers
Swap:   714852k total,    11120k used,   703732k free,   387496k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4951 root      25   0  281m 100m 8496 R 99.9 10.0  30:26.09 Xorg
18279 jarramun  15   0  2364 1152  876 R  0.3  0.1   0:00.02 top
    1 root      18   0  2952 1856  532 S  0.0  0.2   0:01.10 init

HELP!!!!

---

### Post by jcr1 on 2008-04-15
I've noticed a lot of the time mine runs very high...gets physically hot too. 

Top of the CPU list seems to be trackerd... what it this?

---

### Post by quinnten83 on 2008-04-15
have you tried de-installing gnash and installing flash?
I love OSS as much as the next guy, but gnash is a bit buggy. And i know that when firefox is running a flash page the processor will shoot up. Do you keep your FF open when you are on the computer?
i would try running from the live CD for a day to make sure that this isn't a case of incompatible hardware.

are you running a 32 bit or a 64 bit system?
and do you have any hardware other than keyboard and mouse attached to the PC?

---

### Post by Jarramundi on 2008-04-15
> **quinnten83 said:**
> have you tried de-installing gnash and installing flash?
I love OSS as much as the next guy, but gnash is a bit buggy. And i know that when firefox is running a flash page the processor will shoot up. Do you keep your FF open when you are on the computer?
i would try running from the live CD for a day to make sure that this isn't a case of incompatible hardware.

are you running a 32 bit or a 64 bit system?
and do you have any hardware other than keyboard and mouse attached to the PC?

No, even if i have zero webpages open, and gnash is not running. The problem only appears after exactly 24hrs uptime. Just a keyboard and mouse. 32 bit system.

---

### Post by Jarramundi on 2008-04-15
Also, it isn't spiking. Just constantly sits on 99.9% CPU.
This is what it usually looks like, before 24 hrs...

Tasks: 112 total,   2 running, 110 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027508k total,   752316k used,   275192k free,    51824k buffers
Swap:   714852k total,    11120k used,   703732k free,   441452k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
18318 root      15   0  200m  19m 8416 S  0.3  1.9   2:28.49 Xorg
18644 jarramun  15   0  132m  42m  19m S  0.3  4.2   0:57.38 firefox-bin
    1 root      15   0  2952 1856  532 S  0.0  0.2   0:01.10 init

Notice, xorg = 0.3% compared to 99.9% as in post #16? 

It isn't as if restarting the machine every 24hrs is a big deal, but often I leave it going for longer than that, and I don't like the idea of my processor running that hard for any amount of time.

---

