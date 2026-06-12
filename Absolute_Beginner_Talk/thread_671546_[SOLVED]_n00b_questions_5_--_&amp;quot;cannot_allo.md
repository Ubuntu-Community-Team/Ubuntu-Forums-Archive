---
title: "[SOLVED] n00b questions 5 -- &amp;quot;cannot allocate resource region...&amp;quot;"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ZOOstation on 2008-01-18
When I boot up it says briefly, before the splash page:

```
Cannot allocate resource region 7 of bridge 0000:00:1c.0
Cannot allocate resource region 8 of bridge 0000:00:1c.0
Cannot allocate resource region 9 of bridge 0000:00:1c.0
```

Does this mean anything of concern?

---

### Post by PeterJS on 2008-01-18
That's a real good question. Which leads us to another question what is the device at that address? To find out try running this in a terminal:
```

lspci | grep 00:1c.

```
What lspci does is list all of the devices on the pci bus. The | symbol called a pipe tells the program on the left to feed it's output in to the program on the right. The second program, grep, is used for searching text, in this case the output of lspic, for a portion of  the address to cut down the output to just the part that we care about for figuring out what's going on.

Post the results here, and we'll see if it's anything critical.

---

### Post by ZOOstation on 2008-01-18
Thanks!

```
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

```

---

### Post by PeterJS on 2008-01-18
Look's like 1 PCIx slot. Do yo know how many PCIx slots the system is supposed to have? Generally PCIx is used for graphic's cards do you have an nVidia, or ATI card?

---

### Post by ZOOstation on 2008-01-18
I have an ATI Mobility Radeon X600 graphics card. I don't know how many PCIx slots I'm supposed to have -- how do I find that out?

---

### Post by PeterJS on 2008-01-18
> **ZOOstation said:**
> I have an ATI Mobility Radeon X600 graphics card. 
Yep that would do it. ATI and nVidia's cards don't work to their fullest with the open source drivers, one symptom of this is that they sometimes lock out portions of their card until the proper drivers are loaded, which would cause errors like this.

> I don't know how many PCIx slots I'm supposed to have -- how do I find that out? Your best bet would be look up the specs on the manufactures website.

---

### Post by ZOOstation on 2008-01-18
Now what do I do? The Restricted Drivers Manager asked me first thing when I installed Ubuntu to activate the ATI accelerated graphics driver, so I did. It still says it's in use.

I can provide any further information you need.

---

### Post by PeterJS on 2008-01-18
It's a matter of timing, the error is generated very first thing when they system starts up in it's initial probe of the system hardware. The drivers don't load until after that initial hardware probe. There's nothing wrong with the system, that's just the way it is, by the time you're aware of the problem it's probably been fixed, and if not it will be take care of long before you have a chance to do anything.

---

