---
title: "System Info"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by gravediggers on 2005-11-02
:confused: 
Ok. I'm only new to Ubuntu and relatively to Linux. I need to know some system level stuff, and short of pulling the case open and physically looking, I was wondering if there is a utility to use, or file to look at, that tells me things like CPU bus clock speed and type of memory installed, etc. I need to get some more memory for this old PII and want to get it right!

---

### Post by LHZ on 2005-11-02
System->Administration->Device Manager

It lists a lot of stuuf though, so you might have to browse around a bit.

---

### Post by gravediggers on 2005-11-02
That was the obvious place that I tried first, but it told me that it didn't know!

---

### Post by LHZ on 2005-11-02
Well, I've googled aropund a bit, and I can't find anything. If you dual-boot with Windows you can use [this]("http://www.lavalys.com/products/overview.php?pid=1&lang=en") to find the info.

Anyone else?

---

### Post by Mustard on 2005-11-02
```
sudo lshw  # lshw - list hardware

```

On running the lshw command it gives a warning that the command should be run with superuser privileges, so use sudo lshw [OPTIONS] when entering it in terminal.

Read the manual for more specific hardware listings like lshw -businfo.

The command to view the manual in terminal is below.
```
man lshw #manual for lshw command
```

---

### Post by SilentCacophony on 2005-11-02
Another windoze utility that detects most RAM is [cpu-z]("http://www.cpuid.com/cpuz.php").

Best place to look is the motherboard manual, or manufacturer's website.

If all else fails, the memory modules usually have the info printed on them.

---

### Post by gravediggers on 2005-11-02
Thanx all!

Mustard,
Does the lshw tool come with Ubuntu (I've got 5.10) or do I need to download it? Either way, I will have a look tonight and see if it tells me what I want to know.

-----------
I'm fairly sure that I've got the bus clocking at 100MHz on the old box, which means 128MB of PC133 SDRAM should be what I need to get. I hate pulling the PC apart just to check these things. That's what system utilities are for!

---

### Post by SilentCacophony on 2005-11-02
[QUOTE=gravediggers]Thanx all!

Mustard,
Does the lshw tool come with Ubuntu (I've got 5.10) or do I need to download it? Either way, I will have a look tonight and see if it tells me what I want to know.[/QUOTE]

lshw is a basic tool installed by default on ubuntu. it has limited success displaying my hardware correctly, but you may have better luck. :)

---

### Post by gravediggers on 2005-11-03
Thanx SC,

lshw told me lots of good stuff, but not really what i wanted to know. However, I'm sure that I know what extra mem i need, so will buy tomorrow.
64M is not enough to run deeeskktop installation with any speed, so adding 124M will boost me to 192M which should be plenty. Pity i can't afford to get a new machine to fully take advantage of this great linux distro! 

Thanx for all you're help ans see u on some other threads!

---

### Post by duckboy on 2005-11-18
cool, this is exactly what I was looking for:)  I was in the same situation. Who wants to take apart there computer just to find out how fast there computer is or how much memory that you have. I new how to check the memory but the cpu was not listed where it should be in the Device Manager.

---

### Post by lexor on 2005-11-18
> sudo lshw  # lshw - list hardware

very handy :KS

---

