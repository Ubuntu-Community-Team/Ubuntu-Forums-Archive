---
title: "Overheating with Fawn"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by awong42 on 2007-06-19
I was wondering if there is reason to believe that fawn is making my computer overheat.
I don't know much about computers, but I do believe that my IBM T41 with windows was a lot cooler.

I have 7.04 Feisty, IBMT41 Type 2378-DMU

Does this contribute to the lack of battery life I get?

Help?

---

### Post by Crafty Kisses on 2007-06-19
> **awong42 said:**
> I was wondering if there is reason to believe that fawn is making my computer overheat.
I don't know much about computers, but I do believe that my IBM T41 with windows was a lot cooler.

I have 7.04 Feisty, IBMT41 Type 2378-DMU

Does this contribute to the lack of battery life I get?

Help?

It depends, Ubuntu has a lot more effects than Windows, so if you're running effects you can be making your computer running a bit harder than Windows. So you should try to turn off any desktop effects you have.

---

### Post by skymera on 2007-06-19
monitor your CPU temperatures with this...its a small programme that works in terminal.

```
 sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp 
```

---

### Post by diatribe on 2007-06-19
> **Codename said:**
> It depends, Ubuntu has a lot more effects than Windows, so if you're running effects you can be making your computer running a bit harder than Windows. So you should try to turn off any desktop effects you have.

I've run one of my computers with beryl for the longest with a lot of effects, its never run harder than XP did for me.

---

### Post by angryfirelord on 2007-06-19
Is your power management working? Type this in a terminal:
```
sudo powernowd
```
If you don't get an error, then that's working. Here's what my output looks like:
```
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 1000Mhz - 1667Mhz (3 steps)
powernowd:   cpu1: 1000Mhz - 1667Mhz (3 steps)

```

---

### Post by Golyadkin on 2007-06-19
> **skymera said:**
> monitor your CPU temperatures with this...its a small programme that works in terminal.

```
 sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp 
```

lol that script doesn't really work well with dual core processors:
```

~/Downloads/mactel-linux/trunk/tools/temperature$ sudo ./coretemp 
CPU 0: 100 °C
CPU 1: 36 °C

```

The CPU1 temp is the correct one :)

---

### Post by phr0ze on 2007-06-19
heh, yeah I hope you aren't running at 100c. That would fry the chip and be a waste of energy.

---

### Post by oilchangeguy on 2007-06-19
> **awong42 said:**
> I was wondering if there is reason to believe that fawn is making my computer overheat.
I don't know much about computers, but I do believe that my IBM T41 with windows was a lot cooler.

I have 7.04 Feisty, IBMT41 Type 2378-DMU

Does this contribute to the lack of battery life I get?

Help?

if your computer is not freezing, or rebooting, it's not overheating. the os would not be the cause of the computer overheating. laptops run hotter than their desktop cousins. i'd suggest not using a laptop as your main computer, if you can avoid it.

---

