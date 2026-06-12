---
title: "Starting hotplug subsystem"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by Uncle Spellbinder on 2006-01-13
:???: 

I've been trying to complete the install for what seems like forever. Each time I reboot to finish the install, everything stops at *Starting hotplug subsystem*.
My external hard drive is unplugged. I tried *ctrl - c*. No go. Any ideas??? :confused:

---

### Post by benplaut on 2006-01-13
boot into recovery mode (in your GRUB boot menu), and see what happens...

did it stop working, or has it never worked?

---

### Post by Uncle Spellbinder on 2006-01-13
I'll try recovery mode in a minute and post back here. And no, it has not worked at all. Used ship-it cd.

---

### Post by Uncle Spellbinder on 2006-01-13
Tried in recovery mode. It started loading and stopped at:

[i][4294689.30100] hw_random: RNG not detected.
     hw_random: can't be loaded.
missing kernel or user mode driver hw_random[/i]

---

### Post by Uncle Spellbinder on 2006-01-13
So, anyone know if this Is this "fixable", or might I need to start over again?

---

### Post by Uncle Spellbinder on 2006-01-13
Anyone??

---

### Post by Uncle Spellbinder on 2006-01-13
Using Partition Magic: I don't know if this is any help, but....

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/LinuxPartitions.jpg[/IMG]

Right clicked Linux ext3 and clicked *check for errors*:

[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/LinuxPartitionWarning.jpg[/IMG]

---

### Post by kagoole on 2006-01-13
I had a similar problem and it took me ages to find out that it would not load as I had an analog/digital monitor, it was only after I run the monitor in analog mode that the system would boot up.
Hope this helps.

kagoole

---

### Post by Uncle Spellbinder on 2006-01-13
[QUOTE=kagoole]I had a similar problem and it took me ages to find out that it would not load as I had an analog/digital monitor, it was only after I run the monitor in analog mode that the system would boot up.
Hope this helps.

kagoole[/QUOTE]

Appreciate the response. But my monitor is in analog mode. After checking, it is an analog monitor.

---

### Post by Uncle Spellbinder on 2006-01-13
15 hours, 80 thread views and 2 responses. I *really* want this to work. But before giving up completely (it's been nearly three days I've not been able to boot Ubuntu), I thought I'd try you all once more.

I just tried booting the Live CD. Same exact proplem.:???: :confused:

---

### Post by Uncle Spellbinder on 2006-01-13
If it helps, my cpu specs:

* Gateway DX200 S, Pentium 4, 1.93GHz, 160 Gig HD 
* Windows XP Home, SP2
* Comcast High Speed Internet (Peachtree City, GA) 
* NetGear CG814WG v2 modem/router 
* Linksys Wireless  G, 2.4 GHz 802.11g usb network adapter (On second computer)

---

### Post by Uncle Spellbinder on 2006-01-13
Thanks anyway, all. Bye.........


:( Sad "almost-ubuntu-user"

---

### Post by tim15856 on 2006-01-13
Couldn't find too much from Google. I did find someone who had it happen with Ubuntu who said he got that error when he left a blank CD in the CD drive. Otherwise, I suggest unplugging all USB devices and see if that works. If not, remove all but the most essential hardware and try it again.

---

### Post by sanjuro on 2006-01-14
[QUOTE=Uncle Spellbinder]If it helps, my cpu specs:

* Gateway DX200 S, Pentium 4, 1.93GHz, 160 Gig HD 
* Windows XP Home, SP2
* Comcast High Speed Internet (Peachtree City, GA) 
* NetGear CG814WG v2 modem/router 
* Linksys Wireless  G, 2.4 GHz 802.11g usb network adapter (On second computer)[/QUOTE]

I have the exact same problem in my 2nd PC. The specs are:

P4 LGA775 2.8 GHz
Intel D915GLVG
2 x 512 MB DDR400

Funny thing is there are no USB devices attached and I have even disabled the USB controller from BIOS. And Breezy runs just fine on my other PC (A64 3200 + MSI RS480M2-IL).

---

### Post by xerophyte on 2006-01-28
On my case it was the on board Sound card, I went and disable the Onboard audio card in the bios. It worked fine. 

When i have enabled the onboard audio card for my Sony VGC RB30, and reboot with Recovery mode. I got the error saying 

snd-hda-intel: Can't be loaded 

Missing kernel or user mode derver snd-dha-intel 

Sound like the installer missing the driver for the sounds card.

I am going to disable the card and get it working and compile the kernel with support for snd-hda-intel. That might fix it

---

### Post by mgmiller on 2006-01-29
One other thing to try is looking for an entry in BIOS regarding "legacy USB support" or similar and disabling it.  Even if you have the USB ports themselves disabled in BIOS, this setting can still create problems, because it will affect pci cards that have USB ports on them.  I have it turned off on all my windows and linux machines.

---

### Post by phen on 2006-01-29
[http://www.ubuntuforums.org/showthread.php?t=122925](http://www.ubuntuforums.org/showthread.php?t=122925)

he's the same problem. someone mentioned a possible fix: edit grub and add "irqpoll" to the parameters. see the post!

good luck...

---

