---
title: "Can't mount Windows dev/sda2"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by spiddock on 2008-03-10
hi, i'm only running ubuntu off a disk my friend gave me, i use it to rescue my files onto USB when windows XP crashes. This has worked the last two times but this time I can't access the files. I'm using the commands below (typed because i don't know how to copy text across..):

sudo mkdir /media/windows
sudo mount -t auto -o rw,uid=ubuntu,umask=077 /dev/sda2 /media/windows

but then it comes up with:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
missing codepage or other error

if it helps the problem with windows XP is after the main Dell boot screen it comes up with Loading PBR2...done and then stops. Does this mean I've totally screwed windows once and for all?

any help at all would be really appreciated, i need to rescue the first part of a novel i started writing before i restore to factory settings (otherwise i would just let it be wiped...)!

Thanks

---

### Post by Duck2006 on 2008-03-10
From the live cd in the terminal run

sudo fdisk -l

and post the output

---

### Post by dgray_from_dc on 2008-03-10
> **spiddock said:**
> sudo mkdir /media/windows
sudo mount -t auto -o rw,uid=ubuntu,umask=077 /dev/sda2 /media/windows


Perhaps it's the auto or permission settings.  

You can try changing it to the following:
```
sudo mount -t **[COLOR="Blue"]_vfat_[/COLOR]** -o rw,uid=ubuntu,umask=077**[COLOR="Blue"]_7_[/COLOR]** /dev/sda2 /media/windows
```

for FAT32 or

```
sudo mount -t **[COLOR="blue"]_ntfs_[/COLOR]** -o rw,uid=ubuntu,umask=077**[COLOR="Blue"]_7_[/COLOR]** /dev/sda2 /media/windows
```

for NTFS.

---

### Post by spiddock on 2008-03-10
Duck2006 - is there some way to copy the text from the xterm screen, i can type it out but it'll take a while..

dgray_from_dc - i tried the two options and they came up with the same error

thanks for the help, sorry i have no clue what i'm doing!

---

### Post by taurus on 2008-03-10
Highlight what you want to copy with the left button of your mouse and paste it with the middle scrolling button.

Otherwise, just take a screen shot of the window and post it, System -> Accessories -> Screenshot.

---

### Post by spiddock on 2008-03-10
sort of typed out the sudo fdisk -l

disk /dev/sda; 80.0GB
255 heads
units = 

Device           Boot     Start        End          Blocks                Id           System  
/dev/sda1                        1           12         96358+             de          Dell Utllity
/dev/sda2    (asterix)       13        9331         74854867+       7           HPFS/NTFS
/dev/sda3                    9332        9729        3196935            db        CP/M / CTOS / ...

---

### Post by forrestcupp on 2008-03-10
Also, you can't mount an NTFS drive that wasn't shut down properly.  So if you can't boot Windows and shut it down properly, then you may have to look into other options.

---

### Post by Duck2006 on 2008-03-10
taurus is giving you the good oil on how to do that.

---

### Post by gecko113 on 2008-03-10
If you want to still keep windows Xp on ur system.... Wipe the hard drive clean and do a full install of linux :) thats all u need rite there and then use a virtual machine to run windows Xp. [http://www.techthrob.com/tech/linux_virtualization.php](http://www.techthrob.com/tech/linux_virtualization.php) thats the link to do this. also it shows u step by step on how to install it on linux.

---

### Post by spiddock on 2008-03-10
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        9331    74854867+   7  HPFS/NTFS
/dev/sda3            9332        9729     3196935   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ 


thanks taurus - didn't know that!

---

### Post by ByteJuggler on 2008-03-10
> **spiddock said:**
> Duck2006 - is there some way to copy the text from the xterm screen...

Make sure you're using Gnome Terminal (as opposed to the actual original xterm), e.g. Click Applications->Accessories->Terminal.

Then, to copy something into the term, on the terminal menu bar, click, "Edit"->"Paste".

To copy something out of the terminal, mark it with your mouse by left clicking and dragging (the text highlights), then click "Edit"->"Copy" and paste it into the new window you want.

:guitar:

---

### Post by spiddock on 2008-03-10
thanks ByteJulggler - i now have menu bars...

---

### Post by ByteJuggler on 2008-03-10
> **spiddock said:**
> thanks ByteJulggler - i now have menu bars...

No problem.  As an aside, note you can also use Shift-ctrl-c and shift-ctrl-v, which does what you'd expect.

---

### Post by alphaniner on 2008-03-10
Have you tried the gui method of mounting a partition?  With the Live CD if you go to Places -> Computer it will show all of the partitions available for mounting in the left frame.  Double click or right-click->mount to mount it.  It gets mounted as read only, but you can then use the terminal or gksudo nautilus to do whatever you want with it.

---

### Post by spiddock on 2008-03-10
alphanier - thanks for the try but it says it cannot mount. i think it may be what forrestcupp said earlier about windows not shutting down properly. I had to kill my laptop when it didn't reboot after going into standby (it does that every other time though...) but maybe this time it got upset.

i'm becoming resigned to losing my files (for the 3rd time..) at least i had my music and videos backed up this time. Guess i'll just start storing everything on my external HD and not use the laptop at all. It's not worth the risk :-(

---

### Post by alphaniner on 2008-03-10
I figured that'd be the case.  So your Windows install is completely toasted?  Because if not all you need to do is let Windows load up and shutdown properly, then ubuntu should be able to mount it.  Just in case this wasn't clear.

Barring that, have you gone to any windows oriented forums and tried to ask for help?  There has got to be some kind of bootdisk capable of running scandisk or something to 'clean up' the drive.  I don't know where you could start looking, but I'd bet my left n... arm such a thing exists.

edit: try

[http://www.cse.unr.edu/~kvero/BootDisks.htm](http://www.cse.unr.edu/~kvero/BootDisks.htm)

[http://www.bootdisk.com/ntfs.htm](http://www.bootdisk.com/ntfs.htm)
"**All downloads include a special version of chkdsk that runs in DOS and fixes NTFS drives**."

---

