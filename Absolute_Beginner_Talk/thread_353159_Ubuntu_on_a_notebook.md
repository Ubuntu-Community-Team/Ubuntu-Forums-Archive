---
title: "Ubuntu on a notebook"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by Jose.Delay on 2007-02-04
Hello guys,

I'm really new to linux, but I think ubuntu is a great alternative to Windows... By reason of this I downloaded the version 6.10 and tested it on my notebook.

But I have a strange problem and hope you can help me.
There is the cpu fan. I have the feeling that it's cracking up. The fan works the whole time at 100% even if I have no applications running or something like that. And because of this my notebook ist getting damn hot after 20-30 minutes... Does anyone have a similar problem?

My notebook is a intel centrino (pentium m 1,7ghz)...

---

### Post by shareMenaPeace on 2007-02-04
You might want to have a look at xubuntu - designed for low systems.
Almost the same as ubuntu but optimized for performance/low comuters and has a diffrent Desktop Manager xfc4.
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by Jose.Delay on 2007-02-04
Hi,

you mean 1GB Ram, a intel pentium m @ 1,7ghz and an ati 9600 pro is to low for ubuntu???
Even Vista runs on this hardware without problems ;-)

---

### Post by matt_risi on 2007-02-04
Yeah you definitely have a strong computer, perfectly equipped for running Ubuntu and THEN some. As you can see in my sig, my laptop's almost half the performance of yours and I'm running it very comfortably. As for the fan issue though, it may have something to do with the temperature settings within Ubuntu. Anyone who knows more about tinkering with this sort of thing will be able to help you out I'm sure. Good luck!

---

### Post by shareMenaPeace on 2007-02-04
Oopps i just read 1,7 ghz and thought oh how low :) (im new to lappis!)

Well actualy i use a notebook and i run it like 24h and have beryl, azureus, browser, gimp, amarok, openoffice.

I found when i play quake it really fast becomes hot. Also depending how i hold the notebook (on legs). After 30 mins it gets hot aswell than i open the window let in cool air and quiet quake than it regulates :)


But for you this sounds to be without heavy cpu usage happening. Maybe there are cooler check utilities?

---

### Post by tcrroadie on 2007-02-04
> **Jose.Delay said:**
> Hello guys,

I'm really new to linux, but I think ubuntu is a great alternative to Windows... By reason of this I downloaded the version 6.10 and tested it on my notebook.

But I have a strange problem and hope you can help me.
There is the cpu fan. I have the feeling that it's cracking up. The fan works the whole time at 100% even if I have no applications running or something like that. And because of this my notebook ist getting damn hot after 20-30 minutes... Does anyone have a similar problem?

My notebook is a intel centrino (pentium m 1,7ghz)...

Were you running just from the live cd?  One of the things to keep in mind when using the live cd is that all of the software on the cd is compressed, and as you load applications from the cd the system uncompresses the software packages and loads them into your environment.  This is one thing to keep in mind but really should not cause you system cpu usage to remain at 100%.

Is your cpu usage really near 100% at all times.  You can check your resource usage with the command *top* in a terminal.  Open a terminal and type

```
top
```

Will look something like this.

```
kris@edgy:~$ top

top - 10:07:09 up 24 min,  2 users,  load average: 0.08, 0.21, 0.18
Tasks:  81 total,   1 running,  79 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.7%us,  0.2%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1554020k total,   463460k used,  1090560k free,    15108k buffers
Swap:        0k total,        0k used,        0k free,   273008k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4507 kris      16   0  165m  60m  23m S    7  4.0   2:34.68 banshee            
 4099 root      15   0 55812  22m 6412 S    1  1.5   0:22.73 Xorg               
 4580 kris      15   0  177m  49m  21m S    0  3.2   0:22.34 firefox-bin        
 4895 kris      16   0  2248 1116  844 R    0  0.1   0:00.02 top                
    1 root      16   0  1632  536  448 S    0  0.0   0:01.10 init               
    2 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    6 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1   
```

You can easily monitor system resource use with the top utility.  To exit top, just press the q key.  You can find out more information about top my reading its' man page.

```
man top
```

You may also need to load the correct  video driver for your video card.  Typically when you run Ubuntu from the live cd it will just use the vesa drive which will cause your system cpu to do all of the video processing instead of your video card chipset. 

You can find more information on how to install the correct video driver needed for you laptop my visiting the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Graphics_Card"). 

I hope this information helps you some.  And welcome.  :)

---

### Post by Jose.Delay on 2007-02-04
Hello,

> **shareMenaPeace said:**
> Also depending how i hold the notebook (on legs).

You shouldn't hold your notebook on your legs... The temperature can decrease your virility ;-)

@ tcrroadie
Yes I used the live cd... Wanted to test it first. But I'm going to install Ubuntu in a few minutes and maybe after the installation the cpu problem is gone... (hope so ;-))

Thanks at all for the help!

---

### Post by tcrroadie on 2007-02-04
Since you just posted back on the video card in you laptop, I am adding a link for the installation of ATI drivers for Ubuntu.  

An application called Automatix will easily install any third party software (media codecs, video card drivers) on your Ubuntu system.  Please see the link below.  

[Automatix Bleeder]("http://www.getautomatix.com/wiki/index.php?title=Automatix_Bleeder")

---

