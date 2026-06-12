---
title: "Shared Folder"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Controlpanel on 2007-08-25
I dual boot my computer between Windows XP and Ubuntu. Is there someway I can make a shared folder between the two OS?

---

### Post by schorsch on 2007-08-25
No, a shared folder ist not possible. But a shared partition formatted with "fat32", "ntfs", "ext2" or "ext3" is possible when using some tools on windows or linux either.

---

### Post by jay4e on 2007-08-25
yes there is.  the problem is choosing which partition to use.  your best bet is to make a folder in your ubuntu partition (or just use /home) and set up xp to read ext3 partitions, do a search for EXT2IFS.  another options is to make another partition as fat32 and both should see it and read/write no problem.  you can use ntfs-3g to read ntfs partiton from ubuntu but it is the least desirable as its the least stable method.   really your simplest and best bet is to use a fat32 partition or even usb drive formated in fat32.

---

### Post by diffuze on 2007-08-25
I have a fat32 partition that I share between XP and Linux. I've chosen this method because it's by far the easiest way to do this. There are other alternatives I personally prefer the easy way out if it's practical.
On it I store obvious things such as graphics, music and so on, but also for example my firefox profile folder. That means I'm using the same profile regardless of which OS I've booted up in. Extremely useful!

---

### Post by Controlpanel on 2007-08-25
> **diffuze said:**
> I have a fat32 partition that I share between XP and Linux. I've chosen this method because it's by far the easiest way to do this. There are other alternatives I personally prefer the easy way out if it's practical.
On it I store obvious things such as graphics, music and so on, but also for example my firefox profile folder. That means I'm using the same profile regardless of which OS I've booted up in. Extremely useful!

Ok can you tell me how to do this?

---

### Post by diffuze on 2007-08-25
[http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml](http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml)

There's all the info you need to set up the dual boot sharing if that's what you meant. Regarding the fat32 partition I made it during my Kubuntu install and simply chose to format it in fat32.

---

### Post by Controlpanel on 2007-08-25
> **diffuze said:**
> [http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml](http://www.ces.clemson.edu/linux/firefox-thunderbird.shtml)

There's all the info you need to set up the dual boot sharing if that's what you meant. Regarding the fat32 partition I made it during my Kubuntu install and simply chose to format it in fat32.

Thats helpful but I was hoping to be able to share files between the two.

---

### Post by diffuze on 2007-08-26
But that's what you're doing here. Put files on that partition and use them regardless of how you boot up. Full read + write access.

---

### Post by Toufik on 2007-08-28
Much more easier (**ntfs-3g is stable!!** see [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)) :

$ sudo apt-get install ntfs-config

Then, answer the questions and you'll get a full read and write access to your windows partition(s). You can then use it as a shared partition.

Obviously, this work if your windows partitions are in formated in NTFS, if they are in FAT32, you have nothing to do at all to access them from Ubuntu.

On the contrary, you may access (but read only I think) any EXT2 or EXT3 formated parition from Windows with some small applications like explore2fs [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by hyper_ch on 2007-08-28
well, to access ext2/3 partitions form windows use this:  [http://www.fs-driver.org/](http://www.fs-driver.org/)

to read-only access ntfs partitions from linux you don't need anything special
to write access ntfs partitions from linux you need ntfs-3g

To have a partition where you don't need to install anything else, use Fat32 (however files over 2Gb [or 4gb] are not supported).

---

