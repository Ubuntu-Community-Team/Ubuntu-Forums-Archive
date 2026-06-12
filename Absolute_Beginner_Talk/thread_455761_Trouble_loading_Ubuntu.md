---
title: "Trouble loading Ubuntu"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-05-26
I'm having trouble dual booting ubuntu. I've made a patition for ubuntu to go on xp 30gb. My computer is amd 2.2ghz 3200+ Nvidia Fx5700le graphics card. I load ubuntu 7.04 boot from cd and it goes to install, then it proceeds then it stops and flashes a blue screen and thats it.

                                    Please help as I would relly like to use this OS.

---

### Post by alienexplorers on 2007-05-26
Did you burn the CD yourself.  Did you burn it at the slowest speed possible.  Does the MD5 checksum match.

---

### Post by irish_flu on 2007-05-26
What is the setup program doing when the install fails?

---

### Post by fongs on 2007-05-26
> **alienexplorers said:**
> Did you burn the CD yourself.  Did you burn it at the slowest speed possible.  Does the MD5 checksum match.

How do i check this

---

### Post by fongs on 2007-05-26
> **irish_flu said:**
> What is the setup program doing when the install fails?

Installing i belive Nothing else

---

### Post by 3rdalbum on 2007-05-26
Do you actually get to the desktop?

If not, try starting in safe graphics mode (there's an option for it at the first menu).

---

### Post by rusty4r on 2007-05-27
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

this link should help you with cd burning and checksum questions it sure helped me get started

---

### Post by fongs on 2007-05-27
> **3rdalbum said:**
> Do you actually get to the desktop?

If not, try starting in safe graphics mode (there's an option for it at the first menu).

Right I'm in with safe graphics mode and the disk is already partitioned with xp. When in prepare disk space do I.  1 use guided resize IDE1 master, partition #1 (hda1) and use free space
                                     2 Guided use entire disk space
                                 
                                     3 Guided - use largest continuous free space

                                     4 Manual

---

### Post by fongs on 2007-05-27
plase help I'm in the process right now of installing

---

### Post by ugm6hr on 2007-05-27
if you have already created a partition - use manual.

i think it is easier to delete the partition - and leave it as free space.  then reboot the live cd and use the "largest contiuous free space" option.  this sorts out all directories and swap for you.

---

### Post by fenian on 2007-05-27
Sorry misread your post do what was said above.

---

### Post by fongs on 2007-05-27
Maybe you could be so kind as to guide me though the manual process.

---

### Post by ugm6hr on 2007-05-27
sorry.. going to work now. so this will be last post this morning.

besides, i think i decided that the free space option was so easy that i didn't finish the manual.  so not sure i can remember off the top of my head what the options look like.

but - in broad terms:
you need an ext3 partition with path "/" (home directory)
and also a linux swap partition

---

### Post by mybunche on 2007-05-27
Sorry I can't help you with this, but if you still cannot install it on your hard drive, you can always install it on a USB hard drive. I had a few troubles my self so I went and bought a USB hard drive and put Ubuntu on there. No problems installing and doesn't interfere with your main hard drive. 

Hope that worth something. Don't give up, it's worth it.

---

### Post by fongs on 2007-05-27
thanks for the help maybe there is someone else who can help with manual partitioning.

---

### Post by fongs on 2007-05-27
surely someone knows how to manual partition Ubuntu

---

### Post by ugm6hr on 2007-05-27
Seriously - if you're getting nowhere - just delete the partition you created and install to free space via the guided route.  It will save a lot of stress.  It also does not risk your Windows partition, if that's what you're concerned about.

This doesn't need any settings to be adjusted at all.

Presumably if you've created a partition, you must know how to delete it?

---

### Post by fongs on 2007-05-27
thank for the help everyone concerned Iworked it out thanks to --------------------------------------------------------------------------------

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Cheers all

---

