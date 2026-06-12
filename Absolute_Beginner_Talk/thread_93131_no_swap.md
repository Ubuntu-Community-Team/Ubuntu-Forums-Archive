---
title: "no swap"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by mc_bizon on 2005-11-21
i installed ubuntu and have been using it for few weeks and now i read that linux uses swap partition to store swap files. i didn't know it at the time i installed ubuntu, so i didn't make swap partition.
what does it mean? i dont have any swap? can i create swap partition now?

---

### Post by earobinson on 2005-11-21
swap is like windows vertual memory, and you should be able to make a swap partition with gparted and then mount it in your /ect/fstab using a line like this /dev/hda4 none swap defaults 0 0 (hda4 will be changed to whatever partition your swap is)

Swap size is up to you, a lot of distros do double your ram (but thats kinda pointless if you have 4 gigs) I have a 2 gig swap and 1 gig of ram, I have never seen more than 50 megs of my swap used (but im sure i missed it when it was geting used)

---

### Post by mc_bizon on 2005-11-21
ok, i will create a swap partition.
now i dont have any swap, or swap is on the same partition where ubuntu?

---

### Post by earobinson on 2005-11-21
Im not sure I understand your Q, you have to make a swap partition, then add it to your /etc/fstab, then a sudo mount -a will make the changes

---

### Post by mc_bizon on 2005-11-21
no, you didnt understand me. i know that i need a swap partition, you wrote it in your previous post.
this question was about my current situation (no swap partition). where is my swap now? is it now like on windows (same partition for system and for swap)?

---

### Post by earobinson on 2005-11-21
As I understand you just dont have a swap, but I could be wrong, I did a google for (linux with no swap) and found this [http://kerneltrap.org/node/3202](http://kerneltrap.org/node/3202). So if you dont need any more memory there is no need for swap. If you are going to be using programs that may need more memory than you have it is best to install a swap or they will not be able to run.

NOTE: I might be wrong about some of this

---

### Post by dubz on 2005-11-21
swap was mainly used (if im not mistaken) back in the hey-days when program sizes were beginning to get to back for physical memory.

you might have some decreased performance without a swap but that might only be if you are running programs that cant fit into your free RAM.

I might be wrong, but thats how i see it.

thanks.

---

### Post by poptones on 2005-11-21
Without swap you are going to have "old" programs accumulate in RAM, which can have the net effect of slowing things down.

You can easily make a swap file... here's how to make one of 255MB in your / partition

sudo dd if=/dev/zero of=/swap.img bs=1024k count=255
sudo echo '/swap.img none swap' >> /etc/fstab

---

### Post by mc_bizon on 2005-11-22
2 poptones
will this swap file work next time i boot ubuntu? if it will i will use it because i will have a new computer soon(few weeks) and i dont want to download livecd which i could make swap partition with.

i will make a swap partition on new computer, i can live few weeks with this simplier version

---

### Post by earobinson on 2005-11-22
Im not sure I understand the Q, you could install gparted with synaptic and make a swap drive no?

---

### Post by poptones on 2005-11-22
*will this swap file work next time i boot ubuntu?*

Yes. Just make the file, do the other things I show and reboot and it should pick it up. No need to repartition, just use a swap file (that's what I do, it works fine).

---

### Post by steve.horsley on 2005-11-22
The Ubuntu installer normally creates a swap partition. So unless you used custom partitioning, it should be there. Try these commands:

[B]free
sudo fdisk -l[/B]

Steve

---

### Post by mc_bizon on 2005-11-22
thank you all, it works fine. i can feel the difference with my 160MB RAM. :D

2earobinson
no, i cant, i need to unmount partition before resizing it and i cant unmount partition that is in use. i could resize windows partition but there is not a lot of free space. i could use livecd, but i would have to download it first and i will have a new computer soon so it isnt so important.

thank you

---

### Post by poptones on 2005-11-22
I have 512MB of RAM and have never seen my swap usage go above 200MB, but there is a VERY noticeable difference in desktop responsivess even when the swap usage is only a few MB. 

There is one problem with this method you may run into: when synaptic tries to update the kernel image the installer may not like that you have specified a file instead of a block device. If this happens it will appear as if something is broken because it will say "error code 2" and "there was an error trying to upgrade {some kernel image}" 

If this happens, just go to /etc/fstab and put a # before the line about swap, then run synaptic and do a smart upgrade. After the upgrade you can edit the file again and remove the #. 

There's a bug (which I am about to report) when using a loop device for swap. This doesn't mean you can't or shouldn't, it just means we need to fix ubuntu ;)

---

### Post by mc_bizon on 2005-11-23
ok, thank you

---

