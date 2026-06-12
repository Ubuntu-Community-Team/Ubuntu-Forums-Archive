---
title: "How do I get rid of it?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by Runestave on 2006-11-15
Okay, so I've installed Ubuntu 6.06 on my slave drive, while XP still runs on my master. I'm fighting to get my wireless card to work. If I can't get the thing working, I'll be wanting to unistall Ubuntu, because I won't be able to get anything else working, and even if I do, so much of my life is online that it doesn't matter -- without internet access, a computer is a paperweight to me.

So if I decide I want to get rid of it now, what do I do?

I know I can't simply format D: from XP, because XP doesn't even see that drive anymore.

---

### Post by macdo on 2006-11-15
You'll need to reformat the drive to a windows-compatible format. You can do that with GParted, for example, which is on the live CD.

What's up with the wireless card ?

---

### Post by mahy on 2006-11-15
Or you can use something like PartitionMagic. However, the best solution would be to get wifi working, post the specifications of your computer including the card and someone (maybe even me) can help you out. Wifi is not a killer unless you have a SPARC :mrgreen: which i doubt is your case.

---

### Post by nickpaton on 2006-11-15
To help you with your wireless problem please can you post the following, with the wireless connection switched on:

In a terminal type:

```
iwconfig
```

```
ifconfig
```

```
sudo lshw -C network
```

The last is quite long but contains your wireless chipset information.

Also, please could you give some information about your PC, processor, graphics, amount of memory.  It may seem irrelevant at this point, but every little helps!

Good luck and please don't give up - I'm currently typing this on a wirelessly connected laptop and it proves it works.

---

### Post by Runestave on 2006-11-15
Where do I find GParted? Will it restore everything so that when I start up, I won't see that choice of operating system anymore?

---

### Post by Runestave on 2006-11-15
Too late, I have given up. I want it gone.

---

### Post by macdo on 2006-11-15
First of all, put in a live CD and reboot. Then, when you get to the live Desktop, choose in the menu the program called Gparted. Choose the partition Ubuntu is currently on, and reformat it as NTFS or FAT. 

To get rid of the start-up options, you need to do things with your MBR - no doubt if you use your Windows disk, there is an option that will allow you to do that. I can't help you on that, I'm afraid, as I don't run Windows. 

It's a pity that you won't take the help that's been offered to you for your wireless card, though I do understand your annoyance - my wirelss card won't run with Windows, which is one of the reasons I dropped that OS. 

You'll be back soon, I hope...

---

### Post by nickpaton on 2006-11-15
Regarding the Wireless part of it, you have another post running about this and I've posted a possible solution there:

[http://ubuntuforums.org/showthread.php?p=1763030]("http://ubuntuforums.org/showthread.php?p=1763030")

Can I suggest that anyone wanting to contribute to the wireless part go there.

---

### Post by bodhi.zazen on 2006-11-15
> **Runestave said:**
> How do I get rid of it?

You can't

[indent]It will grow
[indent]And grow
[indent]And grow[/indent][/indent][/indent]

It is no use to deny,

[indent]You have Ubuntu fever :p [/indent]

---

### Post by Seine on 2006-11-15
> **Runestave said:**
> Too late, I have given up. I want it gone.

Food for thought: [http://headrush.typepad.com/creating_passionate_users/2006/03/how_to_be_an_ex.html](http://headrush.typepad.com/creating_passionate_users/2006/03/how_to_be_an_ex.html)

---

### Post by nickpaton on 2006-11-15
> **bodhi.zazen said:**
> You can't

[indent]It will grow
[indent]And grow
[indent]And grow[/indent][/indent][/indent]

It is no use to deny,

[indent]You have Ubuntu fever :p [/indent]

Oh no - I think I've got it!!:-D 

Is there any known cure??:neutral: 

Urgent solution needed:(

---

### Post by Runestave on 2006-11-15
Tried the GParted route -- repartitioned and reformatted my drive, then couldn't start up in Windows because it looked for the stuff in the boot sector and couldn't launch what it wanted to. Had to re-install Ubuntu to be stable. Used a very small partition for Ubuntu this time, so it isn't taking up much space, and when I next re-install WinXP (probably this week!) I will wipe it out.

---

### Post by d3v1ant_0n3 on 2006-11-15
1)Format the Ubuntu partition using Gparted (GNOME PArtition Manager- You can find it under Systems>Administration on the livecd) 

2)Boot your computer with the windows XP install disk in the cd drive (You may need to set the bios to boot from cd)

3)Continue until you are given the option to repair an existing installation

This will drop you into a command line interface. The command you need is fixmbr 

Follow through the process and restart the computer. Windows should be back to normal.

---

### Post by K.Mandla on 2006-11-15
Sorry it didn't work out for you. :( 

> **Runestave said:**
> I will wipe it out.
If you do decide to wipe it clean, I'll make my standard endorsement for [Killdisk]("http://www.killdisk.com"), which paints the drive surface with zeroes, making it pristine and new. Next best thing to a brand-new drive. ;)

---

