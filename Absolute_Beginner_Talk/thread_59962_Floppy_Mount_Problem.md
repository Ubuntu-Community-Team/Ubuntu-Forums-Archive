---
title: "Floppy Mount Problem"
date: 2005-08-25
forum: Absolute Beginner Talk
---

### Post by Rick069 on 2005-08-25
I have an applet on my desktop that will automatically mount any drive I have, but there is a problem. When I slide in my floppy disk in and then click on mount, I get a message that says that:

Unable to mount specified volume, could not determine filesystem type and none was specified.

It was made from windoze xp, if that has anything to do with it. Anyway, is there a way to mount this particular floppy so I can read and write from it? I need to print a couple of files from it. I can't go back into windoze to do it because I only have linux on my system now. Don't wanna go through the trouble of installing windoze just to copy a file from a floppy disc.

---

### Post by jasmuz on 2005-08-25
Open a terminal and type:

sudo mount -t vfat /dev/fd0 /media/floppy0

That should be it, remember to unmount it when done.

---

### Post by firenurse4 on 2005-08-26
[QUOTE=Rick069]
Unable to mount specified volume, could not determine filesystem type and none was specified.[/QUOTE]

I wa having trouble with flopies too, and found afix by editing the fstab file. (sudo gedit /etc/fstab) [COLOR=Red]Make sure you bac up your origional ftab file!!![/COLOR]

Find the following line.

/dev/fd0        /media/floppy0  [COLOR=Blue]auto[/COLOR]    rw,user,noauto  0       0

and change it to read...

/dev/fd0        /media/floppy0 [COLOR=Blue] vfat[/COLOR]     rw,user,noauto  0       0

Save the file and reboot.  It should work then. I don't know why, but none of my storage media would mount as an auto file system type.

---

### Post by Irony on 2005-08-26
I had the same problem so put the floppy in and did;

*sudo mount -t vfat /dev/fd0 /media/floppy0*

which worked.

I then did;

*sudo chmod 777 /media/floppy0*

because I could only read not write to floppy. However this command didn't work. How do I enable full write?

Also why does one need to unmount the volume, does it not unmount on shutdown?

---

### Post by firenurse4 on 2005-08-26
[QUOTE=Irony]I had the same problem so put the floppy in and did;

*sudo mount -t vfat /dev/fd0 /media/floppy0*

which worked.

I then did;

*sudo chmod 777 /media/floppy0*

because I could only read not write to floppy. However this command didn't work. How do I enable full write?

Also why does one need to unmount the volume, does it not unmount on shutdown?[/QUOTE]

I had tried manually mounting the drive like that but I was unable to umount it. By changing the line in fstab, I was able to mount the drives under the GUI Computer Icon. You can get there under Nauilus by typing the url [COLOR=Navy]computer:///[/COLOR]

To answer you last question, the only way I was abl to umount the drive when using the mount command in terminal was to reboot! :shock:

Hope this helps.

---

### Post by Irony on 2005-08-27
My sudo chmod 777 command has worked, also the instruction to change auto to vfat has worked. I didn't notice the chmod command had worked until I booted up today - obviously a reboot was the way to the command to work.

I think the reason the floppy should be unmounted before shutdown is that it is a mechanical device unaffected by ejecting the disc - in other words the computer doesn't detect a floppy like it does a cd. Probably just shutting down unmounts it anyway.

---

