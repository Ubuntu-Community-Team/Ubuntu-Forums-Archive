---
title: "Accessing Compact Flash card via CF Adapter/PCMCIA slot - HELP!"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-08
Ive posted this problem in another section of the forums, but really never got the response I was looking for.  I have a lexar 2GB compact flash drive that I would like to access through combination of CF adapter through PCMCIA slot on laptop computer.  By default of the Canon G2 camera, the CF drive is formatted FAT16.

Here's a problem Im having:
1. No automount (not really a big deal)
2. Able to manual mount: I use the following: sudo mount /dev/sda1 /media/cf -t vfat -o iocharset=utf8,umask=000 

I found these instructions from the wiki.  Is this OK???  Should I be concern about the sync or autosync option??

3. Accessing the drive takes forever: Using Konqueror, in order to get a directory listing that shows a thumbnail of the 20 or so jpegs in the folder, takes like 20 minutes.  In WinXP the listing was within 1-2 seconds.  Am I doing something wrong here.  I can access the CF card through the command line, which doesnt take as long, however there is still a significant delay -- around 20 seconds to list about 20 files.

4. If the card happens to be in the slot during boot -- the boot process hangs.  I have to manually remove the adapter/CF card combination, reboot, and then reinsert, manual mount after the boot process is done.

When inserting card, fdisk -l lists device as /dev/sda1.  

dmesg doesnt list any errors.

What else can I do,  Ive written this whole post and only a quarter of the thumbnails have been brought up in Konqueror???

---

### Post by alex1974 on 2007-05-09
I'm also a newbie but had similar problems.
Try this:
When the CF is mounted type in the terminal
mount
and you get a list off all the mounted devices. Look for your CF. Looks like /dev/scd0
Then sudo gedit /etc/fstab/ in the terminal and you get the config for automount.
If there is no line starting /dev/scd... then type something like:
/dev/scd...    /media/usb   auto    rw,users,noauto,sync    0    0
scd... should be the same like in your mount list. rw means read and write permissions and users that eyery user can access them.
Hope that helps,
Alex

---

### Post by kevdog on 2007-05-09
Ok here is te deal since no one else is reporting it:

My PCMCIA slot is made by Texas Instrument (TI).  Its not that the drive wont mount manually or it cant be accessed after mounting, its just that it is terribly slow -- access time takes like 10 minutes to bring up 15 thumbnails.

I have a USB CF reader, it this works normally -- the card is mounted automatically and directory access is just a few seconds.

Dmesg gives no indication why the access time on the PCMCIA card bus is so slow.

I have a feeling its a bug with the PCMCIA utils module but can not prove this.  There are just a small scattered posts in this forum and on the web giving hints of this problem.  

What else can I do at this stage???

---

