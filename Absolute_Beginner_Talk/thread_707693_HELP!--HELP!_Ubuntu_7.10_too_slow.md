---
title: "HELP!--HELP! Ubuntu 7.10 too slow"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by coldleader1 on 2008-02-25
My Ubuntu 7.10 was slow when i was booting it on live cd befor installing. Even after the installation, it takes 2-4 minuits to boot and even after logging it takes 2-4 minuites. And when i click mozillah, i have to wait say 20 secconds. When iright click and click appearence, it takes half a minuit for the window to appear! My internet was working fine after I set up the static ip address and , etc, but now it aint working. I disables that 4 digit thing--I forget the name--and still no internet--ubuntu too slow. Now This is my first time with linux, and I dont know anything about linux. So please be easy with me and please provide solutions. thank you.

---

### Post by A4006 on 2008-02-25
Post your system specs.  Probably all you need to do is upgrade your RAM.

---

### Post by icechen1 on 2008-02-25
How much RAM(memory)do you have?The more you have the faster it will be.

---

### Post by coldleader1 on 2008-02-25
I have 1gig ram, On my Widows xp, everything is fast.

---

### Post by Bruce M. on 2008-02-25
> **coldleader1 said:**
> I have 1gig ram, On my Widows xp, everything is fast.

Are you running Compiz?

---

### Post by Crafty Kisses on 2008-02-25
Actually can you post the following output:
```
top
```

---

### Post by LowSky on 2008-02-25
what ar you computer specs?  Brand and parts please!

---

### Post by crjackson on 2008-02-25
> **coldleader1 said:**
> I have 1gig ram, On my Widows xp, everything is fast.


Just a guess here, but it sounds like your HD isn't in DMA mode or the controller isn't being recognized and supported properly.

---

### Post by coldleader1 on 2008-02-25
> **Bruce M. said:**
> Are you running Compiz?

No I just installed ubuntu. Whats compiz? I told you, I have no knowledge of linux.

" Actually can you post the following output:
Code:

top"

What? Post this code where?

"what ar you computer specs? Brand and parts please!"
--Here is my computer information:
[B]
CPU Model: [/B]AMD Sempron(tm) 2800+
** memory:** 1023 MB (1.00 GB)
**Video Adapter:** RADEON 9200 SERIES
**CPU Speed:** 1992 MHz (1.99 GHz)
I have a 200 gb hard drive--50gig for ubuntu (4 gig for swap and 46 gig for /)

"Just a guess here, but it sounds like your HD isn't in DMA mode or the controller isn't being recognized and supported properly."
--Again I dont know much about ubuntu. I dont know what an HD, nor DMA mod, nor "the controller" is.

again please bare with me, I dont know anything about linux. Sorry for the late replys.  all oyu help is greatly appreciated.

---

### Post by tango_ninja on 2008-02-25
Sorry to piggyback on the thread.....but I have a very similar (if not identical) problem.

After a boot (or a log in) it takes me about 30-34 seconds from hitting enter until my desktop with the menu & panels are loaded. Running Terminal for the first time takes about 50 seconds, and running Appearance Manager takes roughly 60 seconds.....

The second time and onward isn't so bad....for example closing Terminal and running it again takes a couple seconds only.....

I doubt that this is normal....applications such as Terminal can't take THAT long to load... especially since i don't have junky hardware (ok it's not the top of the line but its not junk).

**Computer Specs:**
Gateway MX6958 notebook
120 Gb HD
1 Gb RAM
1.6 GHz Intel Centrino Duo (dual core)

any suggestions ??

---

### Post by PhoenixP3K on 2008-02-25
It's really hard to figure out what causes the problem. The specific problem you guys are describing usually happens when you don't have enough memory but 1GB or RAM is more then enough to run Ubuntu. 

I wonder if your PC is an HP or Compaq? At my school they had those and Ubuntu would take for ever to load on them, despite running Windows pretty well.

---

### Post by tango_ninja on 2008-02-25
mine is a Gateway... not HP/Comaq

I use a couple gDesklets to continually monitor my CPU and RAM usage....during these slow load times the CPU isn't running at more than 4-5% and my RAM usage is around 320Mb (30% or so of my 1Gb available)......

it's rather annoying because Firefox, Pidgin, or whatever app I'm using will grey out and I'll have to wait for a while ...

---

### Post by coldleader1 on 2008-02-25
Well actually, if it is made by Compaq or HP doesnt really matter. Me and my dad made this computer from scratch (bought all the parts and power supply and case and put the whole thing together) But I guess the reason is that Ubuntu may not support the hardware I have. Maby i nead some driver for some of my hardware.
Her are my computer parts that some one here asked for:
**Computer:** ACPI Uniprocessor PC
**Disk Drives:** ST3200822A
**Display adapters:** RADEON 9200 drives
**IDE ATA/ATAPI controllers:** Primary IDE Channel, Secondary IDE Channel, VIA Bus Master

---

### Post by coldleader1 on 2008-02-25
same here my cpu is using no more then 4-5 % of my cpu during these slow loading. Ubuntu only uses 130-150 mb ram.

---

### Post by A4006 on 2008-02-25
Sounds similar to when Vista freezes because I used up a whole 5% of my 3 Ghz CPU (curse you Bill Gates)...  Post the make and manufacturer of your motherboard.

---

### Post by tango_ninja on 2008-02-25
I'm not sure what other info I can give...
I know it is a Gateway MX6958 notebook motherboard (31MA7MB0000) with Mobile Intel 945GM Express Chipset Controller

---

### Post by coldleader1 on 2008-02-25
ok this is weird, my Ubuntu is running fast all of a sudden. My internet connection working again for some reason. My problem is solved. Just before I booted from xp to ubuntu, I prayed to god and asked him if he could solve my problem. And simply My problem is resolved. Anyway it weird my ubuntu is up:KS:):):):):)
now i dont have to go to gentoo.

Oh, Tango ninja, are you sure you arnt hibronating? Restatr a couple times. Maby 5 times. Whatever it is, i rHybronated, ubuntu still slow, restarted, ubuntu still slow, restarted, ubuntu still slow booted xp and went on this forum, booted to ubuntu, and suddenly for some reason its fast when i didnt do anything!

---

### Post by A4006 on 2008-02-25
It seems that miracles do happen every day then :). Glad you solved your problem.

---

### Post by tango_ninja on 2008-02-25
@coldleader yes I have been restarting for days..... I installed 2 weeks ago and have been restarting at least once daily since (not hibernating)

---

### Post by SSBal on 2008-02-26
Hi Friends,

I am facing similar problem. My PC specs are as follow:
Processor type: Intel Celeron
Processor speed: 2.4 Ghz
System bus speed: 400 Mhz
System Memory Speed: 266 Mhz

L2 Cache RAM: 128 KB
Total Memory: 255 MB

Memory Bank 0 256 MB (DDR266)
Memory Bank 1 Not Installed

I have installed ubuntu 7.1 and its really slow. Will increasing the RAM solve my purpose? Also will it be better if I add another RAM of 256 MB in other alot or add 1 GB or may be 2 GB RAM in 1 slot. I am not sure if the videocard has any effect on the speed, I am mentioning this as earlier I had windows XP on this desktop and the graphics were horrible at that time. Now the graphics are fine but speed is too slow.

Thanks in advance.

regards,

Bal

---

### Post by Bruce M. on 2008-02-26
> **coldleader1 said:**
> No I just installed ubuntu. Whats compiz? I told you, I have no knowledge of linux.

Upon seeing your spec's I don't think Compiz is your problem, but lets make sure it is set to **None** for now anyway.
Go to:
[LIST=1]
[*]System > Preferences > Appearance
[*]Then click on: Visual Effects - and make sure None is set.
[/LIST]
> **coldleader1 said:**
> " Actually can you post the following output:
Code:

top"

What? Post this code where?

In Terminal ( Applications > Accessories > Terminal ): type: top

Copy and paste what you see here.
Click on the # at the top and paste it betweem the CODE & /CODE ( they will be inside [ ] )
Here is a sample:
```

bruloo@bruloo:~$ top

top - 10:42:47 up  1:21,  2 users,  load average: 1.18, 0.77, 0.58
Tasks:  96 total,   2 running,  94 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  1.3%sy,  0.0%ni, 94.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    514620k total,   384812k used,   129808k free,    18804k buffers
Swap:  1100412k total,        0k used,  1100412k free,   220224k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7883 bruloo    15   0  146m  48m  20m S  3.3  9.6   2:31.20 firefox-bin        
 5019 root      15   0 89224  16m 6860 S  1.7  3.3   6:11.61 Xorg               
 5373 bruloo    15   0 16408 4740 3768 S  0.7  0.9   0:11.47 gnome-screensav    
 8915 bruloo    15   0  2364 1136  876 R  0.3  0.2   0:00.06 top                
    1 root      15   0  2952 1852  532 S  0.0  0.4   0:02.29 init               
    2 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S  0.0  0.0   0:00.04 top                
    1 root      15   0  2952 1852  532 S  0.0  0.4   0:02.29 init

```


> **coldleader1 said:**
> "what ar you computer specs? Brand and parts please!"
--Here is my computer information:
[B]
CPU Model: [/B]AMD Sempron(tm) 2800+
** memory:** 1023 MB (1.00 GB)
**Video Adapter:** RADEON 9200 SERIES
**CPU Speed:** 1992 MHz (1.99 GHz)
I have a 200 gb hard drive--50gig for ubuntu (4 gig for swap and 46 gig for /)

"Just a guess here, but it sounds like your HD isn't in DMA mode or the controller isn't being recognized and supported properly."
--Again I dont know much about ubuntu. I dont know what an HD, nor DMA mod, nor "the controller" is.

HD is your Hard Drive and you can read about [DMA here]("http://en.wikipedia.org/wiki/Direct_memory_access").  I don't know how you can check or change the settings, but I'm sure someone will help.

> **coldleader1 said:**
> again please bare with me, I dont know anything about linux. Sorry for the late replys.  all oyu help is greatly appreciated.

It'a a thing with Ubuntu ... we like to help eachother.
Bruce

---

### Post by sayakb on 2008-02-26
Whenever we open an application, Linux loads all the dependent libraries and then starts the app. That takes some time. To speed up this, install preload:

```
sudo apt-get install preload
```

This caches all the libraries of the mostly opened programs. After a few days, the apps would start opening faster. Just give this a try. :)

---

### Post by tango_ninja on 2008-02-26
**@linuxisinnovation** sounds like a good idea... however in the case of my laptop, where I am shutting down and booting a couple times a day, would it may any difference? It seems like it would make more sense for a desktop/server that runs continually.

---

