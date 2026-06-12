---
title: "Is this Normal in Ubuntu"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by nerves on 2007-01-13
Hi
I am new to Ubuntu and Linux. When I SHUT DOWN, my Ubuntu closes down, but my tower doesn't switch off. 

Is this normal?

Or is there something I can do to fix it?

Everything  has seemed toload okay?

---

### Post by L Campbell on 2007-01-13
> **nerves said:**
> Hi
I am new to Ubuntu and Linux. When I SHUT DOWN, my Ubuntu closes down, but my tower doesn't switch off. 

Is this normal?

Or is there something I can do to fix it?

Everything  has seemed toload okay?

Hi, if you could provide some information about your tower, it might give some of the experts here some clue as to what it could be.

It does sound like unusual behavior.

---

### Post by matthew on 2007-01-13
It isn't normal on most computers. That said I have an old PIII laptop that I gave to my kids (with Edubuntu installed) that has the same problem. In that case it has to do with unsupported hardware that is old and uncommon and proprietary so no open source drivers exist. You could have the same issue(s) with your hardware, but more details would be needed for anyone to hazard a guess if that's the case or something else.

---

### Post by nerves on 2007-01-13
Will try and find out about tower, it was an old one given to me.

It has an AMD 700Hz processor, 256MB DRam 100 HZ.

---

### Post by nerves on 2007-01-13
WHAT INFORMATION IS NEED? Is this enough?

CASE BADGE: CFL SYSTEMS

KX - 133  K7 Chipset

Processor AMD 700MHz

RAM 256MB DRAM 100Hz

HARD DRIVE 10 GIG BYTE

If not what information is needed, and how do I get it?

---

### Post by L Campbell on 2007-01-13
> **nerves said:**
> WHAT INFORMATION IS NEED? Is this enough?

CASE BADGE: CFL SYSTEMS

KX - 133  K7 Chipset

Processor AMD 700MHz

RAM 256MB DRAM 100Hz

HARD DRIVE 10 GIG BYTE

If not what information is needed, and how do I get it?

That looks like helpful information.

To find information about the hardware on your machine, open a Terminal and type sudo lshw

If your machine tells you 'lshw' is not installed, go to Synaptic, enter lshw in Search, then install it.

Hope this helps you.

---

### Post by matthew on 2007-01-13
What you've given is enough to tell me it's from a similar era as my laptop I mentioned above. Another thing that may be affecting it is how the actual hardware receives shutdown messages. The communication systems for that sort of thing have changed over the years.

Anyway, the preliminary news: everything else seems to work, right? And you can always just push the case switch after the software shutdown sequence completes. 

I'm not sure much can be done to help further, however that's not an absolute. There are lots of people around here that know a lot more than I do so we can give them a chance to see this thread and comment if they have ideas. To help them you might want to open a terminal (from the menu select Applications->Accessories->Terminal) and type this, then post the output.```
lshw
```

---

### Post by K.Mandla on 2007-01-13
Some older computers, like the 550Mhz machine I'm working on now, weren't meant to be shut off automatically. This one will go through a power-off sequence, then stop and sit there. You're supposed to press the power button and click it off completely.

You should still take the time to power it down properly, though. :-?

---

### Post by Jamesbowden on 2007-01-13
To be honest, this doesn't rely sound like much of a problem anyway, if ubuntu shuts down and un-mounts every thing properly turning your tower off from the switch shouldn't be a problem should it?

---

### Post by bigken on 2007-01-13
you might have to hold the button for about six seconds I have had this problem with windows xp also so it not a specific ubuntu thing ;)

---

### Post by lpmasterblow on 2007-01-13
My 5 yr old pIII laptop does the same sort of thing, just let it go through the power down sequence, the progress bar should go completely black, then I just click it off on the on/off switch. Probably something to do with how power down signals are communicated on more modern systems.

---

### Post by pebo on 2007-01-13
You could try adding 
```
acpi=force
```
as a grub boot option.
Apparently newer kernels (~ version 2.6.12) disable acpi for motherboards that are made before the year 2000 so this solution may help.

---

### Post by sloggerkhan on 2007-01-13
I put xubuntu on a friend's machine and I tried tha acpi=force and a number of other options, and in the end nothing realy helped. It just behaved like one of those old computers that would finish the shut down sequence and then you'd have to kill the power yourself.

kinda like the "It is now safe to switch of your macintosh" message from mac OS 7 or so.

---

