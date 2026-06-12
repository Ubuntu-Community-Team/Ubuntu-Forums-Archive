---
title: "[SOLVED] Setting Up Partitions"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by GZBurtchell on 2007-10-22
Ok, I messed up my Ubuntu drive big time to the point where it would just be easier to wipe the partitions and start over. All my important files are safe so wiping the drive is no big deal. I have my Gparted live cd, the program looks easy enough to use but I’ve never used it before.

I have an 80GB drive, I want to create one partition to install Ubuntu 7.10 on, and create another partition to install Ubuntu Studio on. Then there’s also the extended partition for swap. I’m just not sure how, or the best way, to do this.

---

### Post by forestpixie on 2007-10-22
If you just want a partition for each it's quite simple

Boot with gparted - delete the partitions you have and then make new ones, 1 for each os and 1 swap (I'm sure that you could use the swap for either OS)

IF you want a separate /home it'd be a bit more complicated

---

### Post by GZBurtchell on 2007-10-22
> Boot with gparted - delete the partitions you have and then make new ones, 1 for each os and 1 swap (I'm sure that you could use the swap for either OS)


I'm sure that I should format the OS partitions to ext3, but what about the swap partition?

Oh, I think I'll keep my /home with everything else. That's just a bit too much to get into for now. :-)

---

### Post by mramsey on 2007-10-22
I went through the same thing...see [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=578729"). really not too bad to set up :)

---

### Post by forestpixie on 2007-10-22
just tell it swap and you don't get a choice as to file type if I remember correctly.

If you did want /home - you'd have to do an extended partition to allow enough partitions on the drive - so it's only a bit worse :)

---

### Post by bliffle on 2007-10-22
Gparted doesn't do anything until you've specified everything you want done. This can lead to errors of logic on your part that don't become evident until you try to apply what you've specified.

Gparted is basically a GUI to a CLI process that builds a script. I've made mistakes that didn't become apparent until an hour or two or three had gone by.

I advise you to divide up your requiremets with a view to importance and time requirements. For me this means that I spec a couple of simple things like delete partitions and then I apply that. If the result looks good then I go ahead with allocating new partitions and apply it. If that looks good I go ahead with formatting.

At each step I can go back and mend mistakes.

YMMV.

---

### Post by forestpixie on 2007-10-22
> **bliffle said:**
> Gparted doesn't do ... If that looks good I go ahead with formatting.

At each step I can go back and mend mistakes.

YMMV.

+1

---

### Post by GZBurtchell on 2007-10-22
Just out of curiousity, I already have an extended partition for the swap on there, and as far as I can tell it's fine. It's the ext3 partition that I messed up. Can I leave the swap partition as is and just create the two ext3 partitions?

---

### Post by forestpixie on 2007-10-22
As far as I know yes you can

---

### Post by GZBurtchell on 2007-10-22
> **forestpixie said:**
> As far as I know yes you can


I'll be finding out shortly. :-) Hmmm, what about Grub? I think I'll play it safe and restore the MBR to Windows while I do this. If I'm right, when I install Gutsy it'll install Grub and control the MBR.

---

### Post by GZBurtchell on 2007-10-23
I really need some help here. I can't seem to get things set up and working the way I want/need to. I used my Gparted live cd and setup the partitions without any problem and went to install Gutsy and it wouldn't recognize them, or rather it insisted I needed to select a mount point. I tried selecting a mount point from the dropdown menu but no go. So I let it do a Guided/Use the entire disk thing. After Gutsy was all done installing and whatnot. I ran Gparted again, resized the partiton, created a new one, formatted to ext3. I can't seem to do anything with it, I can access it but that's it, no read/write access and I can't change it. I have the feeling I missed something but I don't know what. I'm not having an easy time trying to find simple, easy to understand instructions.

---

