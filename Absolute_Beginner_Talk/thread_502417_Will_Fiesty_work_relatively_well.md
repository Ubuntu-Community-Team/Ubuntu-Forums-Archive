---
title: "Will Fiesty work relatively well?"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by ARandomKid on 2007-07-16
I don't mind if it's slightly slow, as I can very easily et used to that, but will it run at all on my computer?

Here are the specs I get when inputting various commands:

cat /proc/cpuinfo

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 1
cpu MHz         : 4MemTotal:       125284 kB
MemFree:          3440 kB
Buffers:           928 kB
Cached:          28868 kB
SwapCached:      52624 kB
Active:          93476 kB
Inactive:        16164 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       125284 kB
LowFree:          3440 kB
SwapTotal:      361420 kB
SwapFree:       187004 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:         101460 kB
Slab:             6688 kB
CommitLimit:    424060 kB
Committed_AS:   294644 kB
PageTables:       1184 kB
VmallocTotal:   901112 kB
VmallocUsed:      6220 kB
VmallocChunk:   894624 kB
HugePages_Total:     0
HugePages_Free:      0
Hugepagesize:     4096 kB
47.853
cache size      : 256 KB
physical id     : 0
siblings        : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov patpse36 mmx fxsr sse
bogomips        : 882.68


&& cat /proc/meminfo

> MemTotal:       125284 kB
MemFree:          3440 kB
Buffers:           928 kB
Cached:          28868 kB
SwapCached:      52624 kB
Active:          93476 kB
Inactive:        16164 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       125284 kB
LowFree:          3440 kB
SwapTotal:      361420 kB
SwapFree:       187004 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:         101460 kB
Slab:             6688 kB
CommitLimit:    424060 kB
Committed_AS:   294644 kB
PageTables:       1184 kB
VmallocTotal:   901112 kB
VmallocUsed:      6220 kB
VmallocChunk:   894624 kB
HugePages_Total:     0
HugePages_Free:      0
Hugepagesize:     4096 kB


The fact that I only have 125MB of RAM is the main factor that concerns me...but am I just being paranoid (I think I read somewhere that it requires 256MB or something)? Oh, and here's what I get with the "free" command:

>              total       used                free     shared    buffers     cached
Mem:                   125284     121604       3680          0        784      26784
-/+ buffers/cache:   94036      31248
Swap:                    361420     173732     187688


---

### Post by steevols on 2007-07-16
Well... what are you running now? I'd say that Xubuntu or Flubuntu is much more likely to run well than, say, XP, but you're not going to get amazing results!

---

### Post by stchman on 2007-07-16
> **ARandomKid said:**
> I don't mind if it's slightly slow, as I can very easily et used to that, but will it run at all on my computer?

Here are the specs I get when inputting various commands:

cat /proc/cpuinfo



&& cat /proc/meminfo



The fact that I only have 125MB of RAM is the main factor that concerns me...but am I just being paranoid (I think I read somewhere that it requires 256MB or something)? Oh, and here's what I get with the "free" command:

Yes, you need at least 256MB RAM.  I recommend 512MB.  I run Feisty on a P3-450 with 256MB RAM.  It is a little slow but it does work.

---

### Post by agurk on 2007-07-16
It will work, though, as you say, a bit of more RAM wouldn't hurt, it would save your harddisk some serious thrashing.
You'll need to use the 'alternate' CD (text based installer) to install, as the desktop CD (graphical installer) requires 192 MB RAM.

---

### Post by TheTaylorEffect on 2007-07-16
I run Xubuntu on a machine with the same processor and less ram.

It works fairly well for surfing the internet and listening to music. 

Its much faster then XP for basic tasks. 

I ran into a few issues when I was trying to install it (I couldn't run the LiveCD or the Alternate CD).

But other then that, its been humming right along ever since. Its a great extra computer, but I certianly wouldn't rely on is as a primary machine.

But go with Xubuntu for sure!

In order to get it on, I had to install Ubuntu Server Edition, reboot, connect to the internet, and download and install the xubuntu-desktop package from the server command line.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by ARandomKid on 2007-07-16
I'm currently running Knoppix 3.8 (Kubuntu). I ran Ubuntu Breezy with no problems except when I tried to upgrade...which is why I'm running Knoppix at the moment.

Heck, I already ordered a Fiesty CD, might as well just put that in and see what happens. If it screws things up, I'll juist reinstall this, then try Taylor's method. ;^.^

"Its a great extra computer, but I certianly wouldn't rely on is as a primary machine"

Meh. I mainly use this for internet browsing. Ordered feisty because getting .avi, .mp3, etc. files to play is frustrating.

Actually, I'll try Taylor's method now. IF it doesn't work, I'll get back to you.

Nope. Couldn't find package xubuntu-desktop. Which repository is it under? Which brings me to another question, how the heck can I modify sources.list?

Everytime I try kdesu kwrite /etc/apt/sources.list, I get:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0


;_;

---

### Post by Yasumoto on 2007-07-16
I say using TheTaylorEffect's idea sounds good. I had a really old laptop that was running Edgy Eft, but then switched over to Xubuntu Feisty, so Xubuntu should be good. :)

---

### Post by Frak on 2007-07-16
Go for Xubuntu.

---

### Post by TheTaylorEffect on 2007-07-17
[QUOTE=

Nope. Couldn't find package xubuntu-desktop. Which repository is it under? Which brings me to another question, how the heck can I modify sources.list?

Everytime I try kdesu kwrite /etc/apt/sources.list, I get:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0


;_;[/QUOTE]


Did you install Ubuntu Server Edition? 

Try using the -d switch in the apt-get command:

```
sudo apt-get -d install xubuntu-desktop
```

---

