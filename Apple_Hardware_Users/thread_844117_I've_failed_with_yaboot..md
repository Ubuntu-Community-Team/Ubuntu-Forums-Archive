---
title: "I've failed with yaboot."
date: 2008-06-29
forum: Apple Hardware Users
---

### Post by kronat on 2008-06-29
Hello to all,

I tried to install linux under my powerbook g4.
I make two linux partition, and started installation: when I have installed yaboot, it prompt me to select a bootable partition, where install the bootloader. Talking as a normal PC user, I've thought that I need to insert the partition that is bootable normally, not one partion to erase for installing yaboot.. at the end, I've choice /dev/hda3, where was my os x installation. 

Now, I can't enter in os x partition. 

If I use mac-fdisk, I see all its dimension ( 65 Gb ) without a problem, but if I mount it I can only see 3 files of yaboot, and nothing else, and with df I see that it mount only 2 Gb. 

Is there any option to recover my os x partition, with all data and os ?

Thank you.

---

### Post by mfox on 2008-06-29
I have a somewhat similar problem at the moment on my PowerBook G4 that I haven't solved yet, but I can at least tell you how to access the MacOS.   Start up with your finger on the option key.  This will show all bootable volumes, and you will be the MacOS volume.  Select and boot. You should also see your Linux volume that way, but you don't need that at the moment. 

To fix the problem, I know also that all you need to do is add some lines to your /etc/yaboot.conf file that recognizes the MacOS, and then save them and have them written to your bootloader.  But I don't know exactly what the text is that you must add.  I'll leave that to someone more knowledgeable on this forum, but at least my suggestion will allow you to access the Mac side of your PowerBook.

---

### Post by stream303 on 2008-06-29
At this stage I think it would be best to try and recover your osx partition.  Can you boot from your OSX install disk, and go to the top panel and start up disk-utility?  From there I think you should be able to define your OSX startup disk.  This will wipe out your yaboot settings in nvram so you can start over once OSx is back up and running.

When installing Ubuntu (or any linux on ppc for that matter), the easiest thing to do is let guided partitioning handle the whole thing for you by telling it to either install to "free space", or if going totally dedicated to use the "entire disk".

In your case, it sounds like you made room for Ubuntu, but tried to partition it yourself the pc-way, with just a main system partition and a swap partition.  Thing is, apple needs special partitioning, and unless you are skilled at it, it is just a whole lot easier to let guided partitioning handle the job for you.

So, once OSX is back and running, use disk-utility to delete those non-functional Ubuntu partitions you made, and just leave it as free-space.  Now let Ubuntu do the heavy-lifting by installing to free-space, and it should save you a lot of trouble.

---

### Post by kronat on 2008-06-29
Thanks for the suggestion.
Partitioning was easy ( after that, I could boot Os X ). Not installing the bootloader.. After that I can't boot Os X. And the fact that, if I try to mount hda3 I will receive only 3 files and 2 Gb of space ( when with fdisk I see 65 Gb ) give me some happiness. I hope in the apple DVD method.

Unfortunately, I don't have it at the moment, I will try Monday.

For yaboot, I've tried to boot os x partition, adding this line to yaboot.conf:

macosx=/dev/hda3

But it doesn't boot: A fast black screen and go back to first stage boot.

Start with option key pressed doesn't help :(

---

