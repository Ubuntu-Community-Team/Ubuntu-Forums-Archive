---
title: "installing ubuntu on imac (mac 8.6)"
date: 2009-06-23
forum: Apple Hardware Users
---

### Post by Mitch9654 on 2009-06-23
I put ubuntu 8.04 on an imac that used to hold mac 8.6
I took out hard disk, installed, plugged it back in, but it won't boot

help please

mitch9654

---

### Post by barbaGNU on 2009-06-23
what's the model ?

how did you install your system? do you have another ppc box ?

---

### Post by Mitch9654 on 2009-06-23
Thank you for replying!!!

I removed the hard disk from an **imac G3**
I cracked open my ubuntu computer's tower, connected the mac's hard disk and installed from there

I plugged the disk back into  the imac G3 but it just shows a folder with an mac face that changes into a question  mark and back again forever...


I think that means that it doesn't understand the operating system



please help

mitch9654

---

### Post by urosg3 on 2009-06-23
Your system missing yaboot, Mac have a different firmware. You must boot from  G3 CD to install yaboot first, then system itself.

---

### Post by Mitch9654 on 2009-06-23
what if I dont know what yaboot is and dont have the mac install cd?

**ALSO,** how would I install it if I already have an OS on the imac?

---

### Post by urosg3 on 2009-06-23
> **Mitch9654 said:**
> what if I dont know what yaboot is and dont have a cd?

Look, yaboot is way to boot PPC architecture with Linux, is essential. Like BIOS in PC, to compare. If you don't have CD drive, only alternative is to boot your Mac with external Disk drive via firewire.

---

### Post by Mitch9654 on 2009-06-23
i have the cd drive, but just not the mac install cd.


mitch9654

---

### Post by urosg3 on 2009-06-23
> **Mitch9654 said:**
> i have the cd drive, but just not the mac install cd.


mitch9654

Ok my friend, you don't need Mac installation CD install Ubuntu, you need Ubuntu installation CD. How much RAM you have?

---

### Post by Mitch9654 on 2009-06-23
i have no clue how much RAM I have, and when I tried to boot from the cd when macintosh was still in the hard disk, I held down see and it did the mac smiley-face question mark thingy

how do you install yaboot? (from the cd?)


mitch9654

---

### Post by urosg3 on 2009-06-23
Yes, yaboot is on installation disk. Put installation disk in bay, hold down C button and fire power on. Hold it down C until you see yaboot.Then you will be able to install Ubuntu on Mac. 
Now, some bad news, if you have small Ram, you may have various problems during installation, some maybe to big to handle. My advice is to give a chance to Debian Lenny net install small CD if you have internet connection.
There is a link: [http://www.debian.org/distrib/netinst]("http://www.debian.org/distrib/netinst")
Choose small cd, this with only 40 MB. Burn this ISO put it on CD bay, hold down C and run. 

Good luck, and sorry for bad English

---

### Post by Mitch9654 on 2009-06-23
a

---

### Post by Mitch9654 on 2009-06-23
Are you positive that this will work because last time I tried the boot from cd with 'C' the computer annoyed me with the error.

Also, is this on ubuntu 8.04 cd's?



mitch9654

---

### Post by urosg3 on 2009-06-23
You must to burn this ISO or any other ISO for this vintage MAC on very low speed, x1 the best. And don`t use any fancy burner, like K3B, Brasero, just Nautilus burner. Old Mac`s have problem reading CD. And yes, I`m positive, i type this from old G3 Powerbook with Debian Lenny, installed from this net installer. But this was long fight between me and my Mac. Its not easy, but its possible.
This is my mashine

G3 on 400 Mhz
256 RAM
6 GB HDD
8 MB Video Memory
CD/DVD bay
(no firewire, therefore no alternative if something goes wrong)

Cheers

---

### Post by Mitch9654 on 2009-06-23
thanks, I'll try it

mitch9654

---

### Post by Mitch9654 on 2009-07-15
How do you install yaboot if the mac won't boot from the cd that has yaboot on it? I even tried booting from the cd on my working computer, searched through the cd's menu, but couldn't find it


still need help...

mitch9654

---

### Post by Mitch9654 on 2009-07-16
STILL need help...


mitch9654

---

### Post by WB2Colorado on 2009-07-16
Are you SURE that you are using the Ubuntu PowerPC install CD? A PowerPC Mac will not boot from a regular Ubuntu CD.

EDIT: Also, don't hold down the 'C' key at start up, hold down the 'Option' key (If you have an Apple keyboard.), or the Alt key on a PC keyboard.

---

### Post by Mitch9654 on 2009-08-19
Last question, how do I open the cdrom directory in nautilus? It keeps going to "burn:///"

---

### Post by B_Free on 2009-08-19
> **Mitch9654 said:**
> Last question, how do I open the cdrom directory in nautilus? It keeps going to "burn:///"

Let me jump in here. I understand exactly the feeling, the frustration. Please refer to my post at [http://ubuntuforums.org/showthread.php?t=1242108](http://ubuntuforums.org/showthread.php?t=1242108). The people that are answering the question have never run into the problem. My iMac is 266 w/256 of ram.
I went to YouTube and they had a lot of info about installing Ubuntu. But it was always on an Intel machine. 
It would be helpful if someone that is proficient at installing Ubuntu on PPC Macs would take some screen shots and a description of what is going on. Maybe they could write a book (I've purchased 5). I'd buy it!

---

### Post by B_Free on 2009-08-20
> **Mitch9654 said:**
> I put ubuntu 8.04 on an imac that used to hold mac 8.6
I took out hard disk, installed, plugged it back in, but it won't boot

help please

mitch9654

Me again. I was reading one of my books and it kept talking about the BIOS. Being a Mac person, I had no idea what they were talking about. I kind of figured it out. Start your computer up. Put the CD in the CD drive. Go to the control panels. Go down to start up drive. Click the start up drive. If the CD is dimmed, there is noway you can start up from the CD. I just tried it. It was dim. If it not dim, you should be able to select the CD and restart, using your CD as your hard drive.
Whether it is because the CD is a CD-W or the iso file is wrong, I have no idea. I'm going to try to get a CD from shipit. That is where Ubuntu sends you a pre-made CD or DVD.

---

### Post by Mitch9654 on 2009-08-24
The mac wouldn't start the control panels. 
it said that they didn't exist or something

Now the imac won't even boot to macintosh


mitch9654

---

### Post by Mitch9654 on 2009-08-24
What windows or ubuntu program should I use to burn the ubuntu 6.06 CD?

mitch9654

---

### Post by urosg3 on 2009-08-25
Fire up Ubuntu, insert blank CD. CD/DVD creator will pop up. Use the lowest speed possible.

---

### Post by Mitch9654 on 2009-09-09
Thanks so much!

I am going to use ubuntu 6.06 instead, because it says that it is used for imac G3s. I booted to the cd where it showed some text based interface. I selected to install using the live command, and it gave me some "Kernel Panic" message, also saying "not syncing: VFS: (etc)"


mitch9654

---

### Post by Mitch9654 on 2009-09-10
> **Mitch9654 said:**
> Thanks so much!

I am going to use ubuntu 6.06 instead, because it says that it is used for imac G3s. I booted to the cd where it showed some text based interface. I selected to install using the live command, and it gave me some "Kernel Panic" message, also saying "not syncing: VFS: (etc)"


mitch9654

the full error message is :
```
RAMDISK: Compressed image found at block 0
RAMDISK: incomplete write (-28 != 32768) 8388608
RAMDISK: ran out of compressed data
invalid compressed format (err=1)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
```

---

### Post by Mitch9654 on 2009-09-14
New problem, 
found a newer imac G3 with macintosh 9 installed... won't boot from cds that older mac will boot

blech these macs!

mitch9654

---

### Post by oswaldkelso on 2009-09-17
The first thing you need to do is make sure the firmware is up to date this can only be done in mac OS.

If you want an easy install the debian xfce-lxde CD is the one to go for you'll need to fix the X display see PPC facts or there's a how to on the debian forum or if you want to trawl through my old etch stuff a link in my sig. Be aware of the 8gb limit. 

Check the firmware first!

---

### Post by Mitch9654 on 2009-10-14
YES! I was able to upgrade the RAM, (that was the problem) and installed ubuntu 5.04 on the system. Unfortunately, on the first boot, a message came up saying that something didn't install right and that I would enter synaptic. I had no clue how to use this synaptic (for ubuntu 5.04) so just pressed 'u' or 'g', which ever one installed the missing piece. Unfortunately, I don't think that it was successful because the GUI isn't working. Is that because when I installed ubuntu, I didn't have a mouse plugged in? So it didn't "see" the mouse hardware and install a driver for it, so when GDM (GNOME) came to install it aborted because there was no mouse driver to build on?

I am confuzzled (or confused, but I like confuzzled better :) )

mitch9654

---

### Post by Mitch9654 on 2009-10-18
No thanks for debian... I know ubuntu better

The GDM works now for logging in, but then there is a bonobo-activation-server problem. I looked it up and someone said that you just have to set a date and put it in the hardware and system clock, so I think that it is just the imac's PRAM.c I will test further on Mon.

---

### Post by Mitch9654 on 2009-10-30
> **oswaldkelso said:**
> The first thing you need to do is make sure the firmware is up to date this can only be done in mac OS.

If you want an easy install the debian xfce-lxde CD is the one to go for you'll need to fix the X display see PPC facts or there's a how to on the debian forum or if you want to trawl through my old etch stuff a link in my sig. Be aware of the 8gb limit. 

Check the firmware first!


It won't boot cd!

---

