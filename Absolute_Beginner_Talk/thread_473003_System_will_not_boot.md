---
title: "System will not boot"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by J0ris on 2007-06-13
My system is refusing to boot because the partition it is supposed to boot from is full. It had something to do with the default tmp folder of a bittorrent client and I didn't think to check that and put it on another partition. In any case, I did clue in on that after the torrent file froze and emptied the content of the /tmp folder. However, after reboot the system refused to start up, presumably because of a full partition. So I figured it must have written everything to the trash bin, iow, just shifted the data instead of deleting it. 
I booted from the Ubuntu cd to remedy that, but there is no trash bin in sight and the /tmp is indeed empty. Can anybody give me a hand with this?

p.s.: I emptied the /tmp with the rm -R command

Thanks.

---

### Post by logos34 on 2007-06-13
look in your home directory
(View>show hidden files)

/home/user/.Trash

---

### Post by MenZa on 2007-06-13
Umm, perhaps you want to run fsck on that from a LiveCD? Open the Ubuntu LiveCD (or granted, any LiveCD) and open a terminal. Then run:

```
sudo fsck */dev/drivename*
```.

---

### Post by J0ris on 2007-06-13
> **logos34 said:**
> look in your home directory
(View>show hidden files)

/home/user/.Trash

/home folder is on another partition so that shouldn't pose a problem.

---

### Post by jcronkhite on 2007-06-13
When you boot from Ubuntu Live CD, you can do this from the GNOME as well (no command line needed).  Just browse to your local drive and then on to your home directory.  Select the VIEW menu, then SHOW ALL HIDDEN FILES (or just CTRL + H) to expose your hidden directories.  Delete all temporary files as needed.

Thought this might help for the command-line challenged (or for those who were just curious).

---

### Post by dstew on 2007-06-13
Boot the Live CD. Mount your Linux hard disk file system onto the Live CD file system```
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 /media/ubuntu
```
The mount command is assuming your root partition is /dev/hda1. You will need to use whatever it really is, of course. Then, navigate to your home directory and delete the files in your .Trash directory```
cd /media/ubuntu/home/user/.Trash
rm -R *
```Now you should be good to go.

---

### Post by J0ris on 2007-06-13
> **MenZa said:**
> Umm, perhaps you want to run fsck on that from a LiveCD? Open the Ubuntu LiveCD (or granted, any LiveCD) and open a terminal. Then run:

```
sudo fsck */dev/drivename*
```.

partition is clean so no apparent problem there

---

### Post by J0ris on 2007-06-13
Just checked the partition properties. From that it seems that there is about 1Gb of free space but it also adds that "some contents is unreadable". Fsck, however, does not see anything wrong with the partition (fsck /dev/sda1).

Any suggestions?

p.s.: trash folder shows empty

---

