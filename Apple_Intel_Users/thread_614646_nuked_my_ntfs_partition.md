---
title: "nuked my ntfs partition"
date: 2007-11-16
forum: Apple Intel Users
---

### Post by Jonne on 2007-11-16
I installed ubuntu on an imac using this guide: [http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/](http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/)

In the last box it wasn't exactly clear to me what i should've added in the boot loader box, so after searching google i decided to enter /dev/sda4 (which is the partition where / is mounted).

Unfortunately it looks like my NTFS partition got corrupted (it still exists, but it can't be mounted from ubuntu, and when i try to start windows it complains about a missing hal.dll file).

Is there a way to fix this?

Also, the usb keyboard won't work in grub (windows is listed in grub too, but i can't see if it works using that route because i can't select it).

edit: will running fixmbr fix it?

---

### Post by Jonne on 2007-11-16
my /etc/fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=a250ae46-0b8b-4122-bc4b-29017bf8b94f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=04F9-1905  /media/EFI      System  Partition       vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/sda3
UUID=F8C4FDB8C4FD78E8 /media/Untitled 2       ntfs            defaults,umask=007,gid=46 0 1
# /dev/sda5
UUID=4ccf5a3d-ea97-4d18-887f-f4084b2f6058 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

the error I get whe I try to open it:
[mntent]: line 8 in /etc/fstab is bad
[mntent]: line 10 in /etc/fstab is bad

---

### Post by Jonne on 2007-11-16
ok, replacing the ntfs line with:
/dev/sda3 /media/Untitled ntfs nls=utf8,umask=0222 0 0
allows me to mount everything, so I've got access to my files. Enabling Windows to boot is less of a priority now, but if you happen to know how to fix it, please reply.

---

### Post by tvrg on 2007-11-16
fixing windows to boot again could be as hard as forming a new government around here :)

You often can fix those missing whatever files through the recovery console of an xp install disk, but my experience is after you replace hal.dll it will start complaining about another file.
Then when you replace all system files those will be the original xp versions, not the updated or modified versions (including registry sometimes) which means windows boots, but half of your programs don't start, or you don't have a password anymore.

I would backup the ntfs disk from linux and reinstall windows.

---

### Post by cyberdork33 on 2007-11-16
the Hal.dll error is a very common one to get after you change something on the disk.
EDIT: Try this:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)

You indeed installed grub correctly.

The keyboard problem is known and really unfixable... the last round of Mac firmware updates fixed the problem for most people, including myself, but since I upgraded to Leopard it has not worked again.

---

### Post by Jonne on 2007-11-16
> **tvrg said:**
> fixing windows to boot again could be as hard as forming a new government around here :).
Hello, fellow countryman ;)

[quote=cyberdork33]the Hal.dll error is a very common one to get after you change something on the disk.
EDIT: Try this:
[http://ubuntuforums.org/showthread.php?t=327386](http://ubuntuforums.org/showthread.php?t=327386)[/quote]
Thanks, I'll try that on monday. Good to see I'm not completely screwed. will editing boot.ini to change the partition number be enough, or is there anything else? Those guides seem to tell you to compile stuff, but that's just for getting ntfs to work on the older ubuntu versions that didn't have native ntfs support, right?

[quote=cyberdork33]The keyboard problem is known and really unfixable... the last round of Mac firmware updates fixed the problem for most people, including myself, but since I upgraded to Leopard it has not worked again.[/quote]
I updated OS X right before I installed Ubuntu, but I'm not sure if the firmware update was included (does it come with OS X' update manager, or is it a separate download?). The OS on the mac is still Tiger (I don't use it, really, I don't like OS X. I just boot it for updates). It's kinda annoying that recovery is pretty much impossible if a kernel update were to screw things up, though.

Ubuntu runs ok on the mac, except for the crappy ATI card, which doesn't seem to support compiz fusion, I even tried installing the latest drivers with Envy, but those drivers seem even worse (in 2D mode, when switching windows, it takes about a second to switch them, and during that second both the old window decorations and the new ones are shown).

Looks like I'll have Windows running again *before* we get a government *crosses fingers* :) (but then again, do we really need either of them?)

---

### Post by cyberdork33 on 2007-11-16
> **Jonne said:**
> Those guides seem to tell you to compile stuff, but that's just for getting ntfs to work on the older ubuntu versions that didn't have native ntfs support, right?yea you shouldn't need to do that. just change the partition number.

> I updated OS X right before I installed Ubuntu, but I'm not sure if the firmware update was included (does it come with OS X' update manager, or is it a separate download?). The OS on the mac is still Tiger (I don't use it, really, I don't like OS X. I just boot it for updates). It's kinda annoying that recovery is pretty much impossible if a kernel update were to screw things up, though.I know it sux. Usually it will work every once in a while, so you are not completely screwed. The firmware update should be in the Apple Software Update on OSX.

> Ubuntu runs ok on the mac, except for the crappy ATI card, which doesn't seem to support compiz fusion, I even tried installing the latest drivers with Envy, but those drivers seem even worse (in 2D mode, when switching windows, it takes about a second to switch them, and during that second both the old window decorations and the new ones are shown). you shouldn't need envy. fglrx in available in the restricted modules in the repository. Compiz-Fusion will not work without installing XGL unless you have the very latest drivers from ATI's website.

---

### Post by ukripper on 2007-11-19
I had this error before, here is my tutorial [http://ubuntuforums.org/showthread.php?t=466234](http://ubuntuforums.org/showthread.php?t=466234)

---

### Post by Jonne on 2007-11-19
I've tried several numbers (4 and 2, it originally was 3), but it didn't work yet. I'll try 0 and 1, but I don't have the time to be rebooting the box constantly (I need to get some work done too ;) ). If editing the file doesn't work, I'll just try the windows cd method (if i can find a windows cd).

Anyway, I've got some vmware images of Windows I can use, and I can read all the files on the ntfs partition, so getting windows to work isn't really a priority for me.

---

### Post by Jonne on 2007-11-21
Well, setting the partition number to 2 worked, (apparently i hadn't tried that one after all). Now I have another issue: XP starts up (i see the splash screen), but somewhere in the boot process I get a BSOD (which disappears immediately, so the only thing i could read was 'contactyour manufacturer' or somesuch).

It's pretty cool now, as XP is set to boot first (rEFIIt doesn't allow you to choose which OS you want to start yet, so XP is set as first). When I turn it on it goes into a perpetual blue screen cycle :), unless I choose Linux or OS X in rEFIt.

I'll try to figure out what the BSOD said and Google the error.

---

### Post by cyberdork33 on 2007-11-21
> **Jonne said:**
> Well, setting the partition number to 2 worked, (apparently i hadn't tried that one after all). Now I have another issue: XP starts up (i see the splash screen), but somewhere in the boot process I get a BSOD (which disappears immediately, so the only thing i could read was 'contactyour manufacturer' or somesuch).

It's pretty cool now, as XP is set to boot first (rEFIIt doesn't allow you to choose which OS you want to start yet, so XP is set as first). When I turn it on it goes into a perpetual blue screen cycle :), unless I choose Linux or OS X in rEFIt.

I'll try to figure out what the BSOD said and Google the error.

You might be to the point of repairing the install with the Install disc...

---

