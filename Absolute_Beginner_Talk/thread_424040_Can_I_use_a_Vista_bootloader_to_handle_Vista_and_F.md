---
title: "Can I use a Vista bootloader to handle Vista and FF?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-26
Here is my situation.

I have a Dell XPS m1210 with Vista on it.  I want to try out Ubuntu Fiesty Fawn.

I like the Vista Bootloader a lot more than Grub, but once I install FF, I can't get any program, such as EasyBDC 1.52, to rewrite the Vista bootloader to the MBR.  Grub is VERY persistant.

Any one know of a way?  Hopefully I'll be able to keep Dell's Mediadirect functionallity too, but we shall see!  

Thanks all!

---

### Post by Zzl1xndd on 2007-04-26
As far as I know the Windows boot loaders will not see any non-windows OS. I havnt played with vista but  I dont think it can be done.

---

### Post by gohanssjn on 2007-04-26
Hmmm...

With EasyBCD I am give the option of adding a Linux command, just could never get it to work.  maybe that's why.

Is there any way to make grub a little prettier/larger?  Really, it's the tiny text it uses that gets me.

---

### Post by lluisanunez on 2007-04-26
To change GRUB menu, do:
```
 gksudo gedit /boot/grub/menu.lst

```
Delete the "#" before the line 
#color cyan/blue white/blue

And see if it gets better looking

---

### Post by Arjunus on 2007-04-26
windows is designed to be a pain in the *** when trying to install open source. i dont have vista, i still run XP. does grub not give you a black start up screen with all the operating systems your computer has? the text is usually quite readable. I would not recommend a windows bootloader because usually its a mission to fiddle with.

I would continue to use grub. and try to change the command list if you want to boot into vista first or something. i m sure theres also a way to in change the size of the font and screen. good luck mate.

---

### Post by rsambuca on 2007-04-26
> **tweakedenigma said:**
> As far as I know the Windows boot loaders will not see any non-windows OS. I havnt played with vista but  I dont think it can be done.

Actually it can be done, but you have to make the edits to the Vista boot.ini file or something like that.  It is not as easy as editing grub.  I can't remember off hand, but if you search for it on Google, I am sure you will find it.

EDIT:  [[COLOR="Red"]Try this site[/COLOR]]("http://www.pro-networks.org/forum/viewtopic.php?t=79102")

---

### Post by Cypher on 2007-04-26
The Vista boot-manager can absolutely boot Linux. As stated, it isn't a simple config change to make it happen.

When you install Ubuntu, you'd want to install GRUB to the Linux partition as opposed to the MBR. Then you will have to do run
```

dd if=/dev/XXX of=linux.boot bs=512 count=1

```
XXX = your Linux root partition

Now take the linux.boot file and copy it to your C:\ drive in Windows. Edit the boot.ini file and add
```

C:\LINUX.BOOT="Ubuntu Linux"

```

You should be good to go (TM)..:)

---

### Post by gohanssjn on 2007-04-26
> **rsambuca said:**
> Actually it can be done, but you have to make the edits to the Vista boot.ini file.  It is not as easy as editing grub.  I can't remember off hand, but if you search for it on Google, I am sure you will find it.

[[COLOR="Red"]Try this site[/COLOR]]("http://www.pro-networks.org/forum/viewtopic.php?t=79102")

Awesome, I'll look at all the options listed.  Thanks guys!

Now, another question.  Right now I have:

C:\Vista (Primary)
E:\Programs (Primary)
 :\MediaDirect (Logical, and un-editable; i.e., fixed size)

I usually like a seperate partition for my music.  If I do that, and then have 4 partitions, can FF still install to a fifth between Music and Mediadirect?  I thought I read somewhere that a disk was limited to 4 partitions.

---

### Post by Zzl1xndd on 2007-04-26
Thanks for the Info. good to know

---

### Post by gohanssjn on 2007-04-26
> **Cypher said:**
> The Vista boot-manager can absolutely boot Linux. As stated, it isn't a simple config change to make it happen.

When you install Ubuntu, you'd want to install GRUB to the Linux partition as opposed to the MBR. Then you will have to do run
```

dd if=/dev/XXX of=linux.boot bs=512 count=1

```
XXX = your Linux root partition

Now take the linux.boot file and copy it to your C:\ drive in Windows. Edit the boot.ini file and add
```

C:\LINUX.BOOT="Ubuntu Linux"

```

You should be good to go (TM)..:)

Can you tell me how install Grub to the Linux partition and not the MBR?  When I tried last time, it kind of automated the whole thing.

---

### Post by Cypher on 2007-04-26
That's a good question..back in the Linux days using the text-based installer you had a lot more choices on how/where GRUB/LILO was installed. I know the LiveCD version hides a lot of those details, I wonder if the "Alternative" vesrion of Ubuntu 7.04 which uses the text-based installer will provide those details..

Having not done this I can't be entirely certain..hopefully someone who's played with the Alternative CD will chime in here..

---

### Post by rsambuca on 2007-04-26
> **gohanssjn said:**
> Can you tell me how install Grub to the Linux partition and not the MBR?  When I tried last time, it kind of automated the whole thing.

There is an option of where to install grub with both the liveCD and the Alternate CD.  The last question on the live cd installation is something like grub will be installed to hd0, do you wish to proceed?  If you want to change it you press the hd0 button.

On the alternate CD you can specify where you want grub to go as well.

---

### Post by gohanssjn on 2007-04-26
> **rsambuca said:**
> There is an option of where to install grub with both the liveCD and the Alternate CD.  The last question on the live cd installation is something like grub will be installed to hd0, do you wish to proceed?  If you want to change it you press the hd0 button.

On the alternate CD you can specify where you want grub to go as well.

Awesome, I will try that tonight.  Install to the root drive, not the ext swap.  Hope this all works!  I'm excited to learn a new OS, it looks like it's pretty friendly.

And thanks all, great community it seems here :)

---

### Post by gohanssjn on 2007-04-26
When I go to Advanced at the end of the setup, it says GRUB will be installed to (hd0), but I believe that's the MBR, right?

It's installing Ubuntu to Partition #4 of SCSI1 (0,0,0) (sda) as ext3
and the swap to Partition #6 of SCSI1 (0,0,0) (sda) as swap

Any ideas?

---

### Post by rsambuca on 2007-04-26
> **gohanssjn said:**
> When I go to Advanced at the end of the setup, it says GRUB will be installed to (hd0), but I believe that's the MBR, right?

It's installing Ubuntu to Partition #4 of SCSI1 (0,0,0) (sda) as ext3
and the swap to Partition #6 of SCSI1 (0,0,0) (sda) as swap

Any ideas?

I am not sure of your hard drive structure as you haven't given complete details, but if you have just one hard drive, you will want to tell it to install grub to (hd0,3), which is the fourth partition of drive 1 since it starts counting at zero.

---

### Post by gohanssjn on 2007-04-29
> **Cypher said:**
> The Vista boot-manager can absolutely boot Linux. As stated, it isn't a simple config change to make it happen.

When you install Ubuntu, you'd want to install GRUB to the Linux partition as opposed to the MBR. Then you will have to do run
```

dd if=/dev/XXX of=linux.boot bs=512 count=1

```
XXX = your Linux root partition

Now take the linux.boot file and copy it to your C:\ drive in Windows. Edit the boot.ini file and add
```

C:\LINUX.BOOT="Ubuntu Linux"

```

You should be good to go (TM)..:)

Ok, once I run the first commant, I can't find anything named linux.boot.  Help?

---

### Post by rsambuca on 2007-04-29
> **gohanssjn said:**
> Ok, once I run the first commant, I can't find anything named linux.boot.  Help?

Those instructions are quite obviously wrong.  There is no boot.ini file in Vista.  I have no idea where Cypher pulled those instructions from.

---

### Post by gohanssjn on 2007-04-29
> **rsambuca said:**
> Those instructions are quite obviously wrong.  There is no boot.ini file in Vista.  I have no idea where Cypher pulled those instructions from.

Ok, well, when I boot the Vista bootloader and have Ubuntu listed, I get an error.  I'll post it here in just a second.

OK, here we go.  When it tries to load Ubuntu, I get

Failed to start:  

File: \NST\nst_grub.mbr

Status: 0xc0000225

Info:  The selected entry could not be loaded because the application is missing or curropt.

---

### Post by confused57 on 2007-04-29
I haven't used these instructions myself, but saw the link in another thread:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by gohanssjn on 2007-04-29
Unfortunately, that's exactly what I did, and keep getting the above error.

---

### Post by gohanssjn on 2007-04-29
Well, everything I am reading says I need "nst_grub.mbr" but the link of it is dead.  Sadness, I can't get into Ubuntu right now unless I change it to the boot partition, then I lose Hibernation in Vista.  UGH.  So fustrated right now >.<

---

### Post by gohanssjn on 2007-04-29
Just a quick bump.  Going to bed sad in about an hour >.>

If no-one has any ideas, I'll try agian tomorrow.

---

### Post by gohanssjn on 2007-04-30
Ok, wits end.

Anyone know even what nst_grub.mbr is?

---

### Post by Computer Guru on 2007-05-09
[EasyBCD 1.6](http://neosmart.net/dl.php?id=1) addresses the issues outlined above.

Cheers! :)

---

### Post by drowner on 2007-05-09
gohanssjn : I too tried, when setting up a dual-boot to use windows' boot-loader.

Quickly, i went back to grub.

Why? It detects all the installations, it is entirely configurable, and easily configurable and it does EXACTLY what you need it to do: boot various operating systems.

I know thats not what you want, but trust me, for a dualboot setup GRUB is an excellent thing.

---

### Post by leetcharmer on 2007-11-18
I installed Ubuntu Studio 7.04 via Wubi under a machine with Windows Vista.  When I rebooted, Ubuntu showed up just fine -- and when I choose it from the Vista bootloader, everything works like a charm.

The problem is, when I click on Vista -- grub pops up with the first option as ubuntu, and vista under that.  I see grub as an unnecessary step here -- anyone know how to remove grub completely?   or at least make grub only appear when clicking on Ubuntu from the Vista Bootloader instead?

---

