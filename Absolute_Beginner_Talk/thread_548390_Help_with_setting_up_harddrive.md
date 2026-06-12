---
title: "Help with setting up harddrive"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Carl_Barks on 2007-09-11
Hello everyone.

I have a 80 Gb Internal Harddisk wich contains 2 basic partitions.
a ntfs windows partition 
and an ubuntu partition.

Now, I 've bought a brand new 320Gb Internal Harddisk and all I want is to :
format the disk so that i can store my files. Not even a touch of any OS. Just files.
Also I want to have full access (read+write) on that disk so that I keep all my files there, and none of them on the other disk which contains the OSs.
BUT I want it to be accessible both from Ubuntu and Windows. 
I have gparted but I am not sure about doing anything so I want to ask first.

Any help is much appreciated. Thnx in advance.

---

### Post by ijason on 2007-09-11
i would think that formatting it NTFS would be a good plan. windows XP and beyond can see NTFS and it compatible with much larger volumes than FAT32. i'm no expert about compatible formats, but i DO know that the external 300gig drive i formated NTFS for use with windows loads right up without a problem when i plug it into my ubuntu laptop :)

---

### Post by chrome saint on 2007-09-11
Both Windows and Ubuntu can read and write to FAT32 formatted partitions so if your external drive is set up as such you will be able to access the files from either system.  Most external drives come formatted that way for just such reasons.  Remember that FAT32 has a file size limit so it is not something you can rip 5gb iso files to.

There are packages you can get for ubuntu that will allow read/read access to ntfs file systems as well.

---

### Post by Carl_Barks on 2007-09-11
But will ubuntu be able to have full access on an NTFS disk? 
And if yes, how do I do the format? (remember i just want to format it, no OS )

EDIT: The drive i want to format will be internal, not external. it's a SATA disk

---

### Post by jw5801 on 2007-09-11
If you do plan on having large files on there (.isos or archives of any description), go with ntfs, it has reasonably stable support in Linux. I have no idea about ext3 support for Windoes although I know it does exist. ntfs has read support by default in Ubuntu and write support by installing the following package:
```
sudo apt-get install ntfs-3g
```

EDIT: and you can just format it using GParted once you hook it up. You can find GParted under "System > Administration > GNOME Partition Editor" or if you don't already have it run "sudo apt-get install gparted."

---

### Post by chrome saint on 2007-09-11
If you look at my signature you'll see the system I use and it sounds similar to what your trying.  When I was dual-booting XP/Ubuntu I had my external Western Digital drive as FAT32 so I could read and write from either.  Now I only use Linux so all three drives are ext3 file systems.

You can I believe read from an NTFS partition inside ubuntu but to write to NTFS from inside ubuntu  will require you to download a package from the repositories that allows it.

---

### Post by Carl_Barks on 2007-09-11
starting the proccess i click the hd check New and then it asks for a disklabel. Should I stick with ms-dos?

---

### Post by hyper_ch on 2007-09-11
I'd rather format it as Ext3 and then use the Ext2/3 drivers in windows to read and write to it.

---

### Post by jw5801 on 2007-09-11
> **Carl_Barks said:**
> starting the proccess i click the hd check New and then it asks for a disklabel. Should I stick with ms-dos?

Starting what process?

EDIT: Woo! My 2^8 th bean! :p

---

### Post by Carl_Barks on 2007-09-11
> **jw5801 said:**
> Starting what process?

Gparted. I click the desired disk. Click New, and says that i have to set a disklabel first. 
Should I go with ms-dos?

---

### Post by kevin11951 on 2007-09-11
that might be a bad idea, because i have heard from other sites that the software for windows, opens ext3 as ext2, and that has corrupted file systems, just format it as ext2, and see how that goes... if someone else could please elaborate...

---

### Post by hyper_ch on 2007-09-11
ext3 is compatible to ext2... the main difference is that you do not have file journaling while ext3 is opened as ext2 --> [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Carl_Barks on 2007-09-11
Ok, i'll propably make it ntfs.
Can you help me with formating it?
What disklabel do I choose? ms-dos?

---

### Post by jw5801 on 2007-09-11
So you selected the device from the dropdown menu in the top right (should be /dev/sda1 or maybe sda2 if it's sata, there should only be 2 options anyway and one of them should obviously be your existing drive)? Then right-clicked on the blank space and selected "New" and it asked you for a disk label? That's strange... but I would assume ms-dos would work.

---

### Post by Carl_Barks on 2007-09-11
i put an ms-dos label and when i try to make a partition and i see the  filesystem choices ...
I CANNOT SELECT NTFS ...

---

### Post by jw5801 on 2007-09-11
Hmm... Well the repository version of GParted is quite old, so it's entirely possible that it doesn't have support for making an ntfs partition. Try their LiveCD (the link in my sig.) it's much more versatile.

---

### Post by johnbull on 2007-09-11
I have a working system similar to what you describe. Vista Ultimate and Feisty dual-booting with a stand-alone 360Gig hard drive as the data bank.
I formatted the big disk with Vista to ntfs and everything works just tickety-boo. I had to install ntfs-3g to enable the likes of open office etc. writing to the data disk.

A prophet of doom told me Microsoft have been tinkering with the spec of ntfs (it is, after all, their property) and I would be banjaxed trying to write to Vista made docs etc. from Ubuntu - but so far, no probs at all.

As for the label - call it what you like, that's all it is, a label.

---

