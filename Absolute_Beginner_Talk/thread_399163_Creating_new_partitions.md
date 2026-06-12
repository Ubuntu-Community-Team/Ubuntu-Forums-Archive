---
title: "Creating new partitions"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by eldar on 2007-04-02
I have a 200G HD. I currently have XP on it with only 1 partition. I want to resize the partition and then install Ubuntu on the second partition.  I looked around but there are so many posts, ity gets hard to sift through things.

So my first question is this. I can boot off the disk and open the partition program(cant think of the name), At this point, what do I need to do? I know I unmount the drive then I can resize. This is where I have questions. how do I do this part? It is a little weird, it lists MB is how large I want the part, I get that, then it lists "after MB" or something like that. Do I put in a number that sets WHEN the new partition starts?

So if I am able to make the partition, do I set it as fat32 or can I do ntfs? Ubuntu is an ext3 file system? Can it install over any system or does it need to be fat32?

And once I do this, I know my MB can do dual-boot but should the option come up right after install?

1 final ?, if I have to format xp for some reason, do I have have to redo Ubuntu as well or will the partitions stay separate, except in the case of a virus attack? I would think I can just reformat the 1 partition.

---

### Post by rubbsdecvik on 2007-04-02
First off... good questions.

Here's what little knowledge I can pass, but hopefully someone with some more knowledge can help.

To your first question.  You can actually go right into the installer and it will ask you if you want to use the free space from your XP partition.  All you have to do is slide the slider to tell it how much the Ubuntu partition should take.  The installer does the rest.

Linux works best for most people in the ext3 file system, however I have heard that it can run on FAT32.  My suggestion would be if you are new to use ext3 because it's better documented.

If you use the installer, and have it automatically repartition your windows drive it will automatically add a GRUB menu that will allow you to switch to XP very easily.  All you will have to do is restart, and when the GRUB menu comes up you will have about 10-30 seconds (The exact number escapes me at the moment) to choose what operating system to use before it will choose the default (Ubuntu).  

As far at the reformating XP, I'm not sure.  My guess is that XP would be nice and only affect its designated partition, but I'm not sure.  I would suggest doing a little more research on that.  But I'm pretty sure that you wouldn't have to reinstall Ubuntu again.

I hope that helps a little.  Others might be able to give you better answers.

---

### Post by antoz on 2007-04-02
Check out this link below
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by eldar on 2007-04-02
OK both of those helped quite a bit! I think I would like to do it manually or at least know how to do it using GParted on the live disk.

Once the drive I want to resize is unmounted, I can set the size I want but the last setting is what gets me. Is that WHERE the new partition will start? So if I put in a number there, it starts at that point then?

Would be nice if it gave the numbers in Gigs as that is pretty much how most everything is being measured now.

---

### Post by dstew on 2007-04-02
My favorite way to create new partitions is to use the GParted live CD. I like to do one step at a time. In your case, assuming you have defragmented your Windows partition and checked it for errors with chkdsk /f, it should be ready to resize.

I like to put a number into the window, rather than using the slider. Put the number of megabytes you want to free up from your Windows partition in the bottom box (make space after the partition). If you want to free up 10 Gb, put 10000 in there. If you leave the 0 in the Before box, it will not move the partition, only shrink it from the right. Then click Resize/Move, and then on the main screen click Apply. It can take a long time to shrink a partition. On one old laptop it took about 1 hour 30 minutes. DO NOT cancel the resizing operation if the program is running (blue bar going back and forth). If it cannot finish the operation, it will quit safely and give you an error message. Just wait.

After the partition has been shrunk, GParted will show you the unallocated space. Create new partitions out of that space. Make an ext3 partition, and a swap partition that is 1.5 times the size of your system memory. Once that is all finished, install Ubuntu.

---

### Post by eldar on 2007-04-02
Gparted live disk huh. Do you have a good source to download that from? That might work better for me.

---

### Post by dstew on 2007-04-02
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by eldar on 2007-04-02
Hey thanks everyone!  With any luck I will only blow up a couple of things!:lolflag:

---

