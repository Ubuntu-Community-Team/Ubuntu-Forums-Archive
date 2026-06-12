---
title: "Finding computer specs"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by IusedTObeSOMEONEelse on 2006-09-25
I see alot in the forum about small systems and running slow and what not. Where can I find info about my old system to post and have some one let me know what I am working with? I am using Edgy and I went to Administration/System Monitor and the following was shown--/dev/hda1--Type-ext3-- Total-37.0 GIB--Free-33.1 GIB--Available-31.2 GIB--Used-3.9 GIB 11%--I don't know if all this is good as I got machine quite some time ago. Also I don't know how much RAM or other things about system. Any input would be most appreciated

---

### Post by po0f on 2006-09-25
Post the output of the following commands:
```
$ cat /proc/cpuinfo
$ free -m
$ lspci
```

---

### Post by bodhi.zazen on 2006-09-25
For ram:```
free -m
```
Which will print out the size of your ram in Mb.

For CPU```
cat /proc/cpuinfo | grep name
```
Which will give you basic info on your CPU.

> odhi@Arch:~$ cat /proc/cpuinfo | grep name
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
bodhi@Arch:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2025       1932         93          0        278       1022
-/+ buffers/cache:        631       1394
Swap:         1906          0       1906
bodhi@Arch:~$

I have a P4, 3.2 GHz CPU and 2 Gb RAM (2025 Mb "Mem:").

What else do you want to know? :)

---

### Post by po0f on 2006-09-25
How does your post help the OP?

---

### Post by IusedTObeSOMEONEelse on 2006-09-25
~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Intel(R) Celeron(TM) CPU                1300MHz
stepping        : 4
cpu MHz         : 1303.152
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 2608.36

~$ free -m
             total       used       free     shared    buffers     cached
Mem:           249        244          4          0          3         88
-/+ buffers/cache:        152         96
Swap:          729         79        649
~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 05)
01:00.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

---

### Post by bodhi.zazen on 2006-09-25
> **po0f said:**
> How does your post help the OP?

You talkin to me? Shows command, output, and how to interpret. Don't know if it will help.

---

### Post by IusedTObeSOMEONEelse on 2006-09-25
I didn't get what the "GHz" was.

---

### Post by bodhi.zazen on 2006-09-25
Not a bad box. A little low on RAM. Do you understand how to read the output?

---

### Post by po0f on 2006-09-25
MustangSallydd,

Looks like you have a Pentium 3 based Celeron clocked at 1.3Ghz with 256 MB RAM and integrated Intel graphics (i810).  A very modest system, but it can still get things done.  I used to have almost the exact same setup a couple of months ago.

I would definitely suggest at least doubling your RAM.  It is most likely PC133, just FYI.  Maybe an older graphics card if you are into gaming at all.

---

### Post by bodhi.zazen on 2006-09-25
> **MustangSallydd said:**
> I didn't get what the "GHz" was.

Your box is 1.3 G Hz (1303 M Hz).

---

### Post by IusedTObeSOMEONEelse on 2006-09-25
Thanks poOf. Al I knew was that it's an IBM machine I had put together for me quite some time ago. No I don't do much gaming just some simple things (Mahjong) which I have on the windows machine as I can't get wine to get it to work which is another whole nightmare for me. I will grab some more RAM and I basically use this machine for music I love amarok and I finally got frostwire to work in edgy. Thanks so much for the info- Peace`

---

