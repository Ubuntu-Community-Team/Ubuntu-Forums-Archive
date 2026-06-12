---
title: "mounted drives, how to have icon on desktop?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by sabredog on 2005-12-28
I followed all the guides and have automounted my NTFS XP drive and the FAT32 share drive, how do I create an icon on the deskop like XP?

cheers and thanks

---

### Post by Imexius on 2005-12-28
if you mounted your windows partition to the media directory ie /media/windows for example then it should automatically come up.

Try this:

sudo mkdir /media/windows
then go: sudo mount /dev/hda1 /media/windows -o umask=000

---

### Post by sabredog on 2005-12-28
[QUOTE=Imexius]if you mounted your windows partition to the media directory ie /media/windows for example then it should automatically come up.

Try this:

sudo mkdir /media/windows
then go: sudo mount /dev/hda1 /media/windows -o umask=000[/QUOTE]

Ok that would be the reason why then, as both drives are not in the media folder.

---

### Post by audax321 on 2005-12-28
If it is in fact mounted to the media directory and is not showing up on the desktop, check the following:

1. Applications > System Tools > Configuration Editor

2. In the Editor, go to Apps > Nautilus > Preferences and make sure that "show_desktop" is checked.

3. Then go to Apps > Nautilus > Desktop and make sure that "volumes_visible" is checked.

With those options mounted volumes should be appearing on your desktop.

---

### Post by sabredog on 2005-12-28
I followed A.Y Siu's excellent guide and used his syntax, which did not create mount points within the media folder.

Can I redo this to the media folder to get the icons thus appearing?

---

### Post by audax321 on 2005-12-28
I don't know about A.Y. Siu's guide, but here is how to mount it in media. Just make sure to undo the lines you put in /etc/fstab following the guide so the drive doesn't end up mounting twice. I'm assuming you know the /dev/hd** paths to the drives...

FOR THE NTFS DRIVE (IN A TERMINAL - Applications > Accessories > Terminal)

1. sudo mkdir /media/Windows

2. sudo gedit /etc/fstab

3. add the following line in gedit (remove the line you added using the guide):

```

/dev/hd**       /media/Windows  ntfs    nls=utf8,umask=0222        0       0

```

4. save and close gedit


FOR THE FAT32 DRIVE (IN A TERMINAL - Applications > Accessories > Terminal)

1. sudo mkdir /media/Storage

2. sudo gedit /etc/fstab

3. add the following line in gedit (remove the line you added using the guide):

```

/dev/hd**       /media/Storage  vfat    umask=000        0       0

```

4. save and close gedit


All step 1 is doing is creating the folder the drive will be mounted to. Step 2-4 is opening the fstab file in gedit so you can add the lines that will mount the drive when the operating system boots. Replace /dev/hd** with whatever it is for your system (e.g. /dev/hda1 or /dev/hdb2, etc...)

After you are done, in the terminal type this to mount the drives (but if the drives are still mounted from the guide you used, I recommend a reboot): sudo mount -a

This command will mount all the drives and they should show up on the desktop.

:)

---

### Post by sabredog on 2005-12-28
That solved the problem!

Many thanks

---

### Post by oxboy on 2005-12-29
audax321 (or anyone actually...), I was just wondering if you could explain what some of the options mean (I'm just curious, since I'm still learning a lot)  

More specifically, was does umask do ? and what were those numbers after it? nls?  and the two digits at the end?

Thanks so much for everyone's help.

---

### Post by audax321 on 2005-12-29
Here's some information about fstab: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

It explains what those numbers at the end mean as well as other options.

umask has something to do with file permissions and applies to newly created files and directories. It basically makes the filesystem read/writeable. That part about utf8 has to do with a character set to use for the filesystem.

---

### Post by oxboy on 2005-12-29
Thanks a lot!

---

