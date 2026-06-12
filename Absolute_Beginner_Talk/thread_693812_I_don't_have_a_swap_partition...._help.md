---
title: "I don't have a swap partition.... help?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Telescope_Nerd on 2008-02-11
Hi there
I recently started dual booting Ubuntu with Windows and have been happy ever since! But when I set up my Ubuntu partition I did not create a swap partition. Truthfully I'm not even sure what a swap partition actally is and I have not noticed any problems when using Ubuntu. But every so often I read something about swap partitions on the forums and think that maybe I should have one.

Can anyone out there explain why I would want a swap partition? And can I create/set one up  in my Ubuntu partition now, or would I have to re-install?

Thanks in advance!

---

### Post by dca on 2008-02-11
So Windows was there and you ran the Ubuntu Live CD and installed via Ubiquity?
 
 When you went through the motions of installation, went it prompted:
 
Resize existing partitions and let Ubuntu blah blah blah...  What did you choose?  By default if you let Ubuntu automatically re-size the partition and kept the settings it should have a swap...

---

### Post by dca on 2008-02-11
...ohh, if you type top at CLI, before it lists running processes, the line before should mention swap and its total size... I don't think the 'df' command lists it as partitions.

---

### Post by jken146 on 2008-02-11
Swap is virtual memory.  It's like using part of your hard drive as extra RAM if you need it, although it is a lot slower than RAM.

If you have enough free RAM (type **free** to find out or use System Monitor) most of thie time, don't bother creating a swap partition.  It could be more trouble for you than it's worth.

---

### Post by garyed on 2008-02-11
In terminal type the command:
sudo fdisk -l

That will list your partitions & tell you about swap / extended etc...

---

### Post by Telescope_Nerd on 2008-02-11
> **dca said:**
> So Windows was there and you ran the Ubuntu Live CD and installed via Ubiquity?
 
 When you went through the motions of installation, went it prompted:
 
Resize existing partitions and let Ubuntu blah blah blah...  What did you choose?  By default if you let Ubuntu automatically re-size the partition and kept the settings it should have a swap...

Not quite.. I created a partition using windows before I ran the live cd. Then during istallation I selected the partition I made designated it ext3 and mount point /

when I type "top" it says :

Swap:  0k total,  0k free, ...

so it looks like I definitely don't have one.

---

### Post by The Cog on 2008-02-11
> I created a partition using windows before I ran the live cd.
What a strange thing to do. <rhetorical>Did you use Linux to create an NTFS partition before instlling Windows?</rhetorical>

Anyway, a swap partition is used as virtual memory for when the OS runs out of physical memory. Windows use a swap file on C: instead (I forget the name of the file). Linux is capable of using a file instead of a separate partition, but its not a normal thing to do. I gather a separate partition gives better performance. Until you run enough apps at once to run out of memory, you won't notice the absence of swap space. Editing lots of large image files might provoke problems.

Probably the easiest thing to do is to use the Ubuntu live CD, and run the gparted partition editor to shrink the Ubuntu partition a bit. Then create a swap partition in the space you have made. 1-2 Gig should be enough. Some people say twice the physical memory but I reckon machines with less memory probably need more swap. Then you need to edit /etc/fstab to tell Linux to use the swap file when it boots. My fstab entry looks like this:
> /dev/sda8       none            swap            sw    0   0
but your device number will be different (use the name gparted uses).

Note that you can only have 4 primary partitions. If you have used up the 4, you will need to delete the Ubuntu partition and create an extended partition in its place, then put the new Ubuntu system and swap partitions inside the extended partition.

---

### Post by Telescope_Nerd on 2008-02-12
> **The Cog said:**
> What a strange thing to do. <rhetorical>Did you use Linux to create an NTFS partition before instlling Windows?</rhetorical>

lol! no I am dualbooting and vista was pre-installed. Vistas bootloader and grub don't seem to play nicely so I used vista to create a partition and put ubuntu+grub in the partition then configured vista's bootloader to chainboot grub.

Anyway thanks for the info, i'll give it a try.

---

### Post by jordanmthomas on 2008-02-12
If you don't want to mess around with repartitioning, you can use a file for swap.
[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)
Obviously, for ubuntu you'll just want to use sudo instead of logging in as root.

One of the great things about *NIX is that everything is a file, so it doesn't matter if you're using a swap partition or a swap file.

---

### Post by Joeb454 on 2008-02-12
How much RAM does your PC have? If it's more than 1GB I doubt you'll ever need a swap partition.

---

### Post by Telescope_Nerd on 2008-02-12
jordanmthomas: Thanks mate! I think a swap file is definately the way to go, seeing as Ubuntu has been up and running on my system for a while and I would prefer not to re-partition and certainly dont want to re-install.

Joeb454: I have 1G and I'm not too worried about running out of memory but my machine is a laptop and I think that when hibernating It wants to write the ram to swap - is this correct?? If so then I see that as a good reason to set up some swap.

---

