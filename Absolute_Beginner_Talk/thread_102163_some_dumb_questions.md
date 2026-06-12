---
title: "some dumb questions"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by jimrz on 2005-12-11
1 - I know I've seen this before, but not sure where. I have a FAT32 partition (hda5) (:G in winxp) and an icon for it shows up on my ubunru desktop but any file I open from it comes up "read only". How do I get write permission for files on this partition?

2 - Have a MS 5-button optical mouse and the 2 side buttons (back / forward) are not working in ubuntu. So far, this is the ONLY thing that I miss from windows. How can I get this functionality working?

3 - How do I get NumLock to be on at startup? I know, lazy, but Guess I am.

---

### Post by shof2k on 2005-12-11
The answer to number one is to click Applications-Accessories-Terminal, and type the following:

sudo gedit /etc/fstab

In the editor that appears find the line mentioning hda5 and append
"iocharset=utf8,umask=000" to the end of that line.  Save and exit the editor.

Then type 

sudo mount -a to remount your drives

Hope that helps

---

### Post by doitashimashite on 2005-12-11
> 3 - How do I get NumLock to be on at startup? I know, lazy, but Guess I am.

You can install the package "numlockx" in Synaptic. That will do the trick.

---

### Post by aysiu on 2005-12-11
[QUOTE=jimrz]1 - I know I've seen this before, but not sure where. I have a FAT32 partition (hda5) (:G in winxp) and an icon for it shows up on my ubunru desktop but any file I open from it comes up "read only". How do I get write permission for files on this partition?[/quote] [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Make sure to substitute */dev/hda5* for */dev/hda1*, though.

> 
3 - How do I get NumLock to be on at startup? I know, lazy, but Guess I am. Follow the instructions in the first link of my sig. Then, ```
sudo apt-get update
sudo apt-get install numlockx
```

---

### Post by jimrz on 2005-12-11
[QUOTE=aysiu][http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Make sure to substitute */dev/hda5* for */dev/hda1*, though.

 Follow the instructions in the first link of my sig. Then, ```
sudo apt-get update
sudo apt-get install numlockx
```[/QUOTE]

Thanks you all the NumLock fixed worked, but the files on hda5 still come up read ony, guess will have to chang permissions from terminal.

---

### Post by aysiu on 2005-12-11
[QUOTE=jimrz]the files on hda5 still come up read ony[/QUOTE] Did you try this? ```
sudo umount /dev/hda5
sudo mount -a
``` You could also try rebooting. If that still doesn't work, post the contents of your /etc/fstab here.

As far as I know, you can't chown a FAT partition. It has to be mounted properly.

---

### Post by Mustard on 2005-12-11
There is a script that you can run to mount windows drives and make permanent entries in your fstab file.

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

Its a bit fussy about what is mounted and what entries are already in the fstab file, so to get it to work correctly you would need to meet these two conditions first;

1. You have no entries for window drives in your fstab file already (so backup your original fstab and then remove all the entries that relate to windows drives ie those entries that show the file format of vfat or ntfs)

2. All the windows drives are unmounted when the script is run (use the umount command on each windows drive to ensure they are unmounted)

Personally, I find it much easier to run the script than to edit my fstab by hand, as I don't have a clue what some of the fstab options mean. :)

---

### Post by jimrz on 2005-12-11
Thank you guys...saw that while searching after posting this...will do and, hopefully will resolve issue.

Yep, that did it ... you guys rock!

---

