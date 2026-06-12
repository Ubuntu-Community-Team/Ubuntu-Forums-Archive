---
title: "Help please, Windows XP won't boot!!"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Woody56292 on 2006-09-12
ok so I did something very stupid. I was using ubuntu with the cd and I was reading about how to do a full install. I read the instructions and messed with the partitions, and thought everything looked ok. ( realized after I forgot to install ubuntu to harddrive before rebooting ). So I rebooted without the CD, and it wouldn't let me in XP. Now I got linux set up, but it still won't let me into XP. please help. I just wanted to be able to dual boot XP and ubuntu, Now I fear I may have lost all my xp info.](*,) 

someone please help!

---

### Post by jordanmthomas on 2006-09-12
First, let's see if you did in fact destroy windows.
Go to Applications --> Accessories --> Terminal
type this
```
sudo fdisk -l
```
post what is returned and we'll see what can be done from there.

---

### Post by Christopher Cook on 2006-09-13
I have a feeling you lost xp. Hope you have a restore CD, because your restore D: is also gone.

---

### Post by Woody56292 on 2006-09-13
> **jordanmthomas said:**
> First, let's see if you did in fact destroy windows.
Go to Applications --> Accessories --> Terminal
type this
```
sudo fdisk -l
```
post what is returned and we'll see what can be done from there.

well I typed in sudo fdisk -| when it first popped up and nothing happened, just a new line. 
typed sudo fdisk and it popped up with... "Password:" but won't let me type anything.

---

### Post by meborc on 2006-09-13
when you are typing the password, no letters will be shown on the screen (security reasons)... you just need to insert it and hit enter...

---

### Post by anaconda on 2006-09-13
> "Password:" but won't let me type anything.


just type the password and "enter", you won't see anything happening in the display, but it will accept your password.

it is normal..

---

### Post by Woody56292 on 2006-09-13
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

so.... what's the verdict?

---

### Post by 3rr0r on 2006-09-13
> **Woody56292 said:**
> Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

so.... what's the verdict?

Can you just post the display of just ```
sudo fdisk -l
```

---

### Post by carontis on 2006-09-13
I come from windows so I can tell you: if you can start a terminal session in winXP it's ok. In that way you will have to choose the "start with prompt..." ang go to Administrator login (usually no password is there); go to prompt and after inserted a winXP cd type at console " winnt32 /unattend" if you haven't done a big damage it will re-install all system files needed and also something you lost; but in case you broke the partition... try to use fixmbr (just launch it as written) that should be the only way to help you to correct your XP partition. Let us know.

---

### Post by Woody56292 on 2006-09-13
edit: nevermind, just look at my next post.

---

### Post by Woody56292 on 2006-09-13
> **3rr0r said:**
> Can you just post the display of just ```
sudo fdisk -l
```
oops sorry, didn't realize the difference. This looks much more like what it should.

woody@woody-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7266    58364113+   7  HPFS/NTFS
/dev/hda2            7267        9622    18924570   83  Linux
/dev/hda3            9623        9726      835380    5  Extended
/dev/hda5            9623        9726      835348+  82  Linux swap / Solaris
woody@woody-desktop:~$

---

### Post by Woody56292 on 2006-09-13
> **carontis said:**
> I come from windows so I can tell you: if you can start a terminal session in winXP it's ok. In that way you will have to choose the "start with prompt..." ang go to Administrator login (usually no password is there); go to prompt and after inserted a winXP cd type at console " winnt32 /unattend" if you haven't done a big damage it will re-install all system files needed and also something you lost; but in case you broke the partition... try to use fixmbr (just launch it as written) that should be the only way to help you to correct your XP partition. Let us know.

can you put that in step by step format and with less syllables?:mrgreen:

---

### Post by 3rr0r on 2006-09-13
Just to be clear, let me reiterate what I have gathered.

-You had winxp and wanted to configure a dual boot setup.
-You made some partitions using the tools from the live cd
-you installed ubuntu on /dev/hda2
-you have xp on /dev/hda1

Now, when you boot up, it doesn't prompt you for which OS you want to choose, it just goes straight to ubuntu.  If this sounds right, please post the display of the following:

```
sudo gedit /boot/grub/menu.lst
``` 
For this one, just copy+paste everything after all the comments (post everything after this line) "## ## End Default Options ##
"

---

### Post by Woody56292 on 2006-09-13
well no, that isn't exactly how it happened. I was using the cd, and wanted to install full ubuntu, so I read and followed [These]("http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#installonoldhdd")
directions. I think originally I gave my dev/hda1 40gb ( it was using 36 ) and I created a 1gb linux swap and gave the rest to the other partition.
     I restarted my computer ( didn't have the cd in there ) and popped up with a blue screen telling me windows wouldn't start because of some security reason. it recommended I uninstall any recently installed software or hardware.
    I then used the linux cd ( sicne that was now the only os I could get into ) and realized I forgot to install linux on the other partition. So I went in, and realized the partitions were gone and it looked like it was right back where it started. ( default was 50gb for partition one, the rest was unallocated ).
   So I installed ubuntu and used the installer to automatically partition and reallocate any unused space ( because obviously I was a moron and should let the computer handle it ).
   Now I have the option at start to bootup ubuntu or xp, but it still comes up with the bluescreen if I try xp, but works fine if I try ubuntu.
the partitions look like they are still there for windows, so I cannot understand why it won't operate.

---

### Post by Woody56292 on 2006-09-13
> **3rr0r said:**
> Just to be clear, let me reiterate what I have gathered.

-You had winxp and wanted to configure a dual boot setup.
-You made some partitions using the tools from the live cd
-you installed ubuntu on /dev/hda2
-you have xp on /dev/hda1

Now, when you boot up, it doesn't prompt you for which OS you want to choose, it just goes straight to ubuntu.  If this sounds right, please post the display of the following:

```
sudo gedit /boot/grub/menu.lst
``` 
For this one, just copy+paste everything after all the comments (post everything after this line) "## ## End Default Options ##
"
even though it was slightly different from that ( see previous post ) I decided it wouldn't hurt to post this anyways.

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by bodhi.zazen on 2006-09-13
LOL :lol:

In you terminal type```
gksudo gedit /boot/grub/menu.lst
```This will bring up a graphical editor.

You need a section like this:```
Title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```

Re-boot and yo should be fine. :)

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> LOL :lol:

In you terminal type```
gksudo gedit /boot/grub/menu.lst
```This will bring up a graphical editor.

You need a section like this:```
Title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```

Re-boot and yo should be fine. :)
wait mine looks like this
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



so I need to add boot to the end? what about the savedefault part? do I leave that in there or take it out? just wanna make sure before I mess something up again.;)

---

### Post by Woody56292 on 2006-09-13
ok I tried that and it still pops up with the blue screen when I select xp and try to run it. it says unmountable boot volume error...

edit: Tjust for reference, this is what it looked like when I just tried, I added the boot part but pops up with the error still.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
boot

---

### Post by 3rr0r on 2006-09-13
**BEFORE**:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```

**AFTER**
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
Title Windows XP
[COLOR="Blue"]rootnoverify [/COLOR](hd0,0)
makeactive
chainloader +1
boot

```

What about [COLOR="Red"]savedefualt[/COLOR] in the **BEFORE** section? Please confirm/deny bodhi.zazen

---

### Post by Woody56292 on 2006-09-13
> **3rr0r said:**
> **BEFORE**:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```

**AFTER**
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
Title Windows XP
[COLOR="Blue"]rootnoverify [/COLOR](hd0,0)
makeactive
chainloader +1
boot

```

What about [COLOR="Red"]savedefualt[/COLOR] in the **BEFORE** section? Please confirm/deny bodhi.zazen
yeah realized I forgot that part and tried it again. still no luck. I am now going to restart without the start default part.

---

### Post by Woody56292 on 2006-09-13
still no luck.:-k

---

### Post by 3rr0r on 2006-09-13
Have you considered a complete format/install?  I would think this wouldn't be so bad if you have recently backed up your data.

---

### Post by Woody56292 on 2006-09-13
> **3rr0r said:**
> Have you considered a complete format/install?  I would think this wouldn't be so bad if you have recently backed up your data.
...:)  well you see, the thing is... ( i haven't _ever[U]_[/U] backed up my harddrive )

---

### Post by bodhi.zazen on 2006-09-13
savedefalut is optional. It "saves" the last OS you booted and sets it as the "default" the next time you boot. ie. if you boot windows XP, and then reboot windows XP will be the default OS. If you then  boot Ubuntu when you re-boot Ubuntu will be default. You can still select which OS to boot. I do not use this option, sorry for the confusion.

You do not need two section in menu.lst for windows XP.

This is no longer a Linux or GRUB issue, you have a problem with Windows. :sad:

No time like the present to convert to Linux.... :mrgreen: 

I suggest you try your windows rescue CD if you have one. This will likely re-write you MBR so you will need to restore it. If you can not restore windows you will need to re-install.

Obviously you will lose most of your data in the windows partition if you do this.

You may be able to mount the windows partition and copy/back up your data. If you do not know how to do this, re-post.

[Restore GRUB](http://ubuntuforums.org/showthread.php?t=24113)

I prefer the second method posted by remmelt. :twisted:

---

### Post by ske1fr on 2006-09-13
> **Woody56292 said:**
> Tjust for reference, this is what it looked like when I just tried, I added the boot part but pops up with the error still.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
boot

I'm sure you did this so just humour me.  When you typed in the "boot" instruction into the file, did you hit the Return key at the end of the line?  If not, that line just won't be executed.  I used to do this in another operating system all the time, until I learned to check it!

---

### Post by Woody56292 on 2006-09-13
> **ske1fr said:**
> I'm sure you did this so just humour me.  When you typed in the "boot" instruction into the file, did you hit the Return key at the end of the line?  If not, that line just won't be executed.  I used to do this in another operating system all the time, until I learned to check it!

wow and to think I want to major in programming. ( I am such a newb )
unfortunately that didn't help either. how do I go into the parition on ubuntu ( option isn't there anymore like on cd ). Maybe I can just give all the space back to xp and it will work? ( i know that is like giving a fire a fire extinguisher, but maybe it will work itself out? )

---

### Post by bodhi.zazen on 2006-09-13
If you have a new computer and it did not come with a Windows CD, you may have had a restore partition. If this is the case you may be SOL as I think you toased XP partition and (hd0,0) may be your restore partition (your windows partition os only 3 Gb, awfully small for windows XP.....)

Lets look at what you have:

in a terminal:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows
```

You should now be able to see your ntfs partition, read only with nautilus. Go to /media/windows.

Or, in a terminal:```
ls /media/windows
```

---

### Post by Woody56292 on 2006-09-13
where do you see size? I checked disk manager and this is what I see.
partition 1, device hda1, windows ntfs, 55.6 gb
partition 2, device hda2, extended 3, 18.05 gb
swap partition, dev hda5, memory swap, 815 mb


maybe my swap partition isn't allowing xp to use memory?
Or maybe I have no clue what I am talking about?:mrgreen: 
if at all possible, I would like to keep my information from xp, cause I know it all must be there. ( hoping anyways )
anyone else have any recommendations? ( thanks for everyone's help thus far )

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> If you have a new computer and it did not come with a Windows CD, you may have had a restore partition. If this is the case you may be SOL as I think you toased XP partition and (hd0,0) may be your restore partition (your windows partition os only 3 Gb, awfully small for windows XP.....)

Lets look at what you have:

in a terminal:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows
```

You should now be able to see your ntfs partition, read only with nautilus. Go to /media/windows.

Or, in a terminal:```
ls /media/windows
```
alright I am confused again. ( sorry I super newb at file/memory stuff, I just like programming animations and interfaces:( )
so I am supposed to to type in : sudo mkdir /media/windows
then sudo mount -t ntfs etc. ?
think I need step by step instructions again.:rolleyes:

---

### Post by 3rr0r on 2006-09-13
Follow the "code" in post 27.  Each of those commands is  a seperate one... ie:
```
sudo mkdir /media/windows
```

then

```
sudo mount -t ntfs /dev/hda1 /media/windows
```

lastly

```
ls /media/windows
```

These are commands that need to be typed in a terminal.

---

### Post by Woody56292 on 2006-09-13
> **3rr0r said:**
> Follow the "code" in post 27.  Each of those commands is  a seperate one... ie:
```
sudo mkdir /media/windows
```

then

```
sudo mount -t ntfs /dev/hda1 /media/windows
```

lastly

```
ls /media/windows
```

These are commands that need to be typed in a terminal.
ok I think I need to restart before trying again. first time I typed in the first thing, it asked for password and all that jazz. now it just does this.

woody@woody-desktop:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
woody@woody-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/windows
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /[COLOR="Cyan"]tmp/disks-conf-hda1[/COLOR]
woody@woody-desktop:~$ ls /media/windows
woody@woody-desktop:~$

ok I may be stupid, but I know that is not good. why is it on a temporary disc?


oh and can someone tell me how to pause on the snakes game? I tried p but that didn't work. ( i don't want to go into menu and pause everytime .

---

### Post by jordanmthomas on 2006-09-13
```

sudo umount /dev/hda1
sudo mount -t ntfs /dev/hda1 /media/windows

```

I'm not sure why it mounted it to a temp area, but it's normal for it to do that (at least on the LiveCD)

This will unmount it and then mount it where you want.

---

### Post by 3rr0r on 2006-09-13
That is odd.  You may need to unmount it and remount it.  I'm not too strong in that area, but I do know the command.

```
sudo umount /dev/hda1
```

But, as I said I don't think it should be mounted to a temp folder, but I could be wrong.  Wait for more people to post.

---

### Post by sgtBiafra on 2006-09-13
OK, I realize this is an Ubuntu forum, but perhaps I can help Woody with some Windows information.

It seems that you installed attempting to resize the Windows partition and what has resulted is a volume that cannot be mounted correctly by Windows itself. In the Windows recovery console (accessible from the Windows installation cd), you have a series of console commands available to you to fix boot problems. I believe if you select your Windows install partition, enter the console and use the FIXBOOT command you may be on your way back into Windows. FIXBOOT installs a clean partition boot sector in a system partition (as opposed to FIXMBR that fixes the disk boot sector, restoring Microsoft's boot loader instead of GRUB).

If that does work out, definitely backup your key data and then give Ubuntu another try :)

---

### Post by Woody56292 on 2006-09-13
> **jordanmthomas said:**
> ```

sudo umount /dev/hda1
sudo mount -t ntfs /dev/hda1 /media/windows

```

I'm not sure why it mounted it to a temp area, but it's normal for it to do that (at least on the LiveCD)

This will unmount it and then mount it where you want.

yeah but I am not on the live cd. I installed the full version of Ubu.
The cd is not in the drive either.
so why would it be in a temp area. would that explain why ( in Ubu ) I cannot install or download anything. ( didn't want to mention that problem because I thought it was just unreleated or related to my lack of knowledge of linux interface )

---

### Post by sgtBiafra on 2006-09-13
If the partition was corrupted during the installation process and even Windows cannot access it, it's possible that the Linux mount command would not recognize the partition as NTFS.

Just a thought.

---

### Post by jordanmthomas on 2006-09-13
That wouldn't explain your issues with installing (you were right, it is more likely than not unrelated)

I don't think it's a problem that it was mounted to /tmp ....  I am not sure why it does that though.
Have you got the drive mounted yet?

**edit**
> woody@woody-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 7266 58364113+ 7 HPFS/NTFS
/dev/hda2 7267 9622 18924570 83 Linux
/dev/hda3 9623 9726 835380 5 Extended
/dev/hda5 9623 9726 835348+ 82 Linux swap / Solaris
woody@woody-desktop:~$

It recognizes it

---

### Post by Woody56292 on 2006-09-13
> **jordanmthomas said:**
> That wouldn't explain your issues with installing (you were right, it is more likely than not unrelated)

I don't think it's a problem that it was mounted to /tmp ....  I am not sure why it does that though.
Have you got the drive mounted yet?

**edit**


It recognizes it

isn't the first one xp? so if it recognizes it.... why does windows say unmountable boot... ( when I try and start xp )

---

### Post by jordanmthomas on 2006-09-13
The drive could be damaged.  My friend's Windows was doing that exact thing last weekend all of a sudden for no apparent reason.  Then, yesterday, it just worked again.

If you manage to get it mounted in Ubuntu there shouldn't be any reason Windows can't

---

### Post by bodhi.zazen on 2006-09-13
Wow, this thread is growing fast.

the error messages> 
woody@woody-desktop:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
woody@woody-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/windows
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is mounted on /tmp/disks-conf-hda1
woody@woody-desktop:~$ ls /media/windows
woody@woody-desktop:~$are telling us the drive is already mounted.

so we are good to go...

What is in /dev/hda1 ?

In a termninal, what do you get if you type:```
ls -la /tmp/disks-conf-hda1
```

If you unmounted the partition you will have to re-mount (see above).

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Wow, this thread is growing fast.

the error messagesare telling us the drive is already mounted.

so we are good to go...

What is in /dev/hda1 ?

In a termninal, what do you get if you type:```
ls -la /tmp/disks-conf-hda1
```

If you unmounted the partition you will have to re-mount (see above).
odd...
woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
ls: /tmp/disks-conf-hda1: Permission denied
woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
ls: /tmp/disks-conf-hda1: Permission denied
woody@woody-desktop:~$


it can't be viewed by Ubu?

---

### Post by bodhi.zazen on 2006-09-13
FYI: if you want to re-mount the partition on /media/windows:```
sudo umount /tmp/disks-conf-hda1
sudo mount -t ntfs /dev/hda1 /media/windows
```
Totally optional at this point.

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> FYI: if you want to re-mount the partition on /media/windows:```
sudo umount /tmp/disks-conf-hda1
sudo mount -t ntfs /dev/hda1 /media/windows
```
Totally optional at this point.
ok unmounted then remounted. then tried this again. here it is.

woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
total 8
drwxr-xr-x  2 root root 4096 2006-09-13 10:06 .
drwxrwxrwt 17 root root 4096 2006-09-13 10:49 ..
woody@woody-desktop:~$


( I am not going to lie, that looks like gibberish to me... )

edit: oh wait nm ,that is the date and time.

---

### Post by bodhi.zazen on 2006-09-13
What is the output of:
```
df -h
```

and```
ls -la /media/windows
```

> woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
total 8
drwxr-xr-x 2 root root 4096 2006-09-13 10:06 .
drwxrwxrwt 17 root root 4096 2006-09-13 10:49 ..
woody@woody-desktop:~$
ls = "list" same as dir in windows.
-la = long format and "all files" options.
drwxr-xr-x = permissions
root toor = owner + group (both root)
. = current directory
.. = move up one level.

If you enter pwd you will see /home/woody no?
if you enter cd .. you will move up one level. pwd now returns /home.

To return to you home directory use cd (with nothing else).

~ = /home/woody (shorthand).

---

### Post by Woody56292 on 2006-09-13
ok hadn't tried a restart in a while. Still no luck. Windows says "unmountable boot" whenever I try and start windows normally ( from ubuntu dual boot menu thingy )

it recommends I disable or delete new software or hardware and/or change bios settings for caching and shadowing.

same screen I have been getting.

still, it feels like we are making progress.:) 
What are the odds that my files are still there? It would really suck if I lose all my pictures, naruto videos, and itunes music.;) 
in all seriousness, I guess as long as most of the stuff can be replaced ( except for pictures ) at this point I might be leaning towards full reinstall of xp and Ubu. ( unless ofcourse there is a way to keep my files and current xp setup, cause I don't think I have the restore disc. )

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> What is the output of:
```
df -h
```

and```
ls -la /media/windows
```
woody@woody-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  1.9G   16G  12% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  233M   8% /lib/modules/2.6.15-26-386/volatile
woody@woody-desktop:~$ ls -la /media/windows
total 8
drwxr-xr-x 2 root root 4096 2006-09-13 10:17 .
drwxr-xr-x 4 root root 4096 2006-09-13 10:17 ..
woody@woody-desktop:~$

---

### Post by 3rr0r on 2006-09-13
```

woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
total 8
d[COLOR="Red"]rwx[/COLOR] [COLOR="Blue"]r-x[/COLOR] [COLOR="SeaGreen"]r-x[/COLOR]2 root root 4096 2006-09-13 10:06 .
drwxrwxrwt 17 root root 4096 2006-09-13 10:49 ..

```



These are the permissions.  The permissions are listed in order of you - people in your group - others not in the group.  There are 3 options to have, rwx (read, write, execute).  If that permission is enabled, you will see a letter, if it is not allowed, there is a "-" (dash)

Red is you.  You can read, write, execute.  Other users in your gorup can read and execute.  Lastly, others outside that workgroup can also read and execute.

---

### Post by Woody56292 on 2006-09-13
> **3rr0r said:**
> ```

woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
total 8
d[COLOR="Red"]rwx[/COLOR] [COLOR="Blue"]r-x[/COLOR] [COLOR="SeaGreen"]r-x[/COLOR]2 root root 4096 2006-09-13 10:06 .
drwxrwxrwt 17 root root 4096 2006-09-13 10:49 ..

```



These are the permissions.  The permissions are listed in order of you - people in your group - others not in the group.  There are 3 options to have, rwx (read, write, execute).  If that permission is enabled, you will see a letter, if it is not allowed, there is a "-" (dash)

Red is you.  You can read, write, execute.  Other users in your gorup can read and execute.  Lastly, others outside that workgroup can also read and execute.
wow that actually made sense.:p  thanks.

---

### Post by bodhi.zazen on 2006-09-13
> **Woody56292 said:**
> woody@woody-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  1.9G   16G  12% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  233M   8% /lib/modules/2.6.15-26-386/volatile
woody@woody-desktop:~$ ls -la /media/windows
total 8
drwxr-xr-x 2 root root 4096 2006-09-13 10:17 .
drwxr-xr-x 4 root root 4096 2006-09-13 10:17 ..
woody@woody-desktop:~$


Your partition is not mounted.

```
sudo mount -t ntfs /dev/hda1 /media/windows
```
and re-run "df -h"
You should see something like
/dev/hda1              4G  ?G   ?G  ?% /media/windows
as output.

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Your partition is not mounted.

```
sudo mount -t ntfs /dev/hda1 /media/windows
```
and re-run "df -h"
You should see something like
/dev/hda1              4G  ?G   ?G  ?% /media/windows
as output.

woody@woody-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  1.9G   16G  12% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  233M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              75G   56G   20G  75% /media/windows
woody@woody-desktop:~$


that looks good right? I mean it is showing hda1 which is where my xp os is right?

---

### Post by davec64 on 2006-09-13
HI,

Had a similar problem with XP on a dual boot system.

I tried Fixmbr & Fixboot from within DOS, but it didn't work.

Try downloading and creating the boot disk from this site:

[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

This doesn't actually change anything but hopefully will get you into XP!



You might want to use FDISK to check to see which partition is active. I found that my Linux partition was active as opposed to XP C:\ partition.

Hope this helps!

---

### Post by bodhi.zazen on 2006-09-13
> **3rr0r said:**
> ```

woody@woody-desktop:~$ ls -la /tmp/disks-conf-hda1
total 8
d[COLOR="Red"]rwx[/COLOR] [COLOR="Blue"]r-x[/COLOR] [COLOR="SeaGreen"]r-x[/COLOR]2 root root 4096 2006-09-13 10:06 .
drwxrwxrwt 17 root root 4096 2006-09-13 10:49 ..

```



These are the permissions.  The permissions are listed in order of you - people in your group - others not in the group.  There are 3 options to have, rwx (read, write, execute).  If that permission is enabled, you will see a letter, if it is not allowed, there is a "-" (dash)

Red is you.  You can read, write, execute.  Other users in your gorup can read and execute.  Lastly, others outside that workgroup can also read and execute.

Very nice post.

However, the file is owned by root.

Thus what you said (colors) is true of root. As a user you have permissions of "other".

---

### Post by Woody56292 on 2006-09-13
> **davec64 said:**
> HI,

Had a similar problem with XP on a dual boot system.

I tried Fixmbr & Fixboot from within DOS, but it didn't work.

Try downloading and creating the boot disk from this site:

[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

This doesn't actually change anything but hopefully will get you into XP!



You might want to use FDISK to check to see which partition is active. I found that my Linux partition was active as opposed to XP C:\ partition.

Hope this helps!

would that explain the unmountable boot error I keep getting? also wouldn't that cause my os to restart, like a brand new computer? or would the floppy just be used to reinstate it, then I could get rid of the floppy and go back to switching from xp to ubu?

edit: going to try and restart my comp first. Want to see if that mounting thing I did, does anything.

---

### Post by 3rr0r on 2006-09-13
> **bodhi.zazen said:**
> Very nice post.

However, the file is owned by root.

Thus what you said (colors) is true of root. As a user you have permissions of "other".

Right!  I interchange "you" and "root" because I always presume the main user can enable root priveledges.

---

### Post by Woody56292 on 2006-09-13
ok still no luck. I thought that we mounted the xp?( 1 )
still says unmountable boot.

---

### Post by Woody56292 on 2006-09-13
> **davec64 said:**
> HI,

Had a similar problem with XP on a dual boot system.

I tried Fixmbr & Fixboot from within DOS, but it didn't work.

Try downloading and creating the boot disk from this site:

[http://www.tinyempire.com/notes/ntldrismissing.htm](http://www.tinyempire.com/notes/ntldrismissing.htm)

This doesn't actually change anything but hopefully will get you into XP!



You might want to use FDISK to check to see which partition is active. I found that my Linux partition was active as opposed to XP C:\ partition.

Hope this helps!

so should I just do this? if so can you put it in step by step order  so I know I do it right.

---

### Post by Woody56292 on 2006-09-13
not to be impatient or ungrateful, but can someone give me directions on how to do what he said about burning an iso for xp, I don't have a floppy drive so I assume I will have to burn an iso and do some stuff?. ( that won't delete my files will it )

edit: or should I try something else?

---

### Post by bodhi.zazen on 2006-09-13
> **Woody56292 said:**
> ok still no luck. I thought that we mounted the xp?( 1 )
still says unmountable boot.

Be patient. I'm at work....

Did you try to mount /dev/hda1 and get an error message? If so, post error message please.

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Be patient. I'm at work....

Did you try to mount /dev/hda1 and get an error message? If so, post error message please.
:p  sorry but I am kind of bored, normally I would be listening to podcasts or checking cnet while I wait, but can't install flash. ( totally unrelated flash problem, not with ubuntu )

anyways.... how do I do that again? ( mount /dev/hda1 ):mrgreen: 

( yes I really am that slow... )

---

### Post by 3rr0r on 2006-09-13
dont forget sudo

---

### Post by Woody56292 on 2006-09-13
[This is the error I get when I try and start xp.]("http://support.microsoft.com/?kbid=297185")

If I find the disc, I may try this solution. But I trust you guys much more than I trust a microsoft support page.:rolleyes:

---

### Post by bodhi.zazen on 2006-09-13
sudo mount -t ntfs /dev/hda1 /media/windows

also:

df -h

and 

ls -la /media/windows.

also read some of my previous posts (I edited some and posts were happening rapidly there for a while).

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> sudo mount -t ntfs /dev/hda1 /media/windows

also:

df -h

and 

ls -la /media/windows.

also read some of my previous posts (I edited some and posts were happening rapidly there for a while).

woody@woody-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/windows
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is already mounted on /media/windows
woody@woody-desktop:~$

so now I should try and reboot and see what happens?

---

### Post by 3rr0r on 2006-09-13
he wants you to do all those commands and show us the output

---

### Post by Woody56292 on 2006-09-13
same as before. ( last time I did it on page 5. )
woody@woody-desktop:~$ sudo mount -t ntfs /dev/hda1 /media/windows
mount: /dev/hda1 already mounted or /media/windows busy
mount: according to mtab, /dev/hda1 is already mounted on /media/windows
woody@woody-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  1.9G   16G  11% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  233M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              75G   56G   20G  75% /media/windows
woody@woody-desktop:~$ ls -la /media/windows
ls: /media/windows: Permission denied
woody@woody-desktop:~$

---

### Post by 3rr0r on 2006-09-13
I have my preferences set to show 100 posts per page, so its all 1 page to me  :mrgreen:

---

### Post by davec64 on 2006-09-13
> **Woody56292 said:**
> would that explain the unmountable boot error I keep getting? also wouldn't that cause my os to restart, like a brand new computer? or would the floppy just be used to reinstate it, then I could get rid of the floppy and go back to switching from xp to ubu?

edit: going to try and restart my comp first. Want to see if that mounting thing I did, does anything.

The floppyy uses it's own NTLDR.ini and NTDETECT.ini rather than those located in the root folder on your c:\ drive.
This enables you to boot directly into windows.
It doesn't change any of your files.
I used this method to get into XP, then using Partition Magic reset the active partition.
My problem appears to have been a partial install of Dapper which left the wrong partition active.

All the best!

---

### Post by Woody56292 on 2006-09-13
> **davec64 said:**
> The floppyy uses it's own NTLDR.ini and NTDETECT.ini rather than those located in the root folder on your c:\ drive.
This enables you to boot directly into windows.
It doesn't change any of your files.
I used this method to get into XP, then using Partition Magic reset the active partition.
My problem appears to have been a partial install of Dapper which left the wrong partition active.

All the best!

so all I would have to do is use my 2gb usb drive ( says both usb and floppy are supported ) and copy those files to it from another windows pc, then it will bootup those files at start and hopefully allow me into xp?
are there any steps I am missing.

---

### Post by Woody56292 on 2006-09-13
what would happen ( if it is possible ) if I....
unmounted hda2 ( or whatever linux is using )
and mounted hda 1....
would that give me xp back as primary?

---

### Post by davec64 on 2006-09-13
> **Woody56292 said:**
> not to be impatient or ungrateful, but can someone give me directions on how to do what he said about burning an iso for xp, I don't have a floppy drive so I assume I will have to burn an iso and do some stuff?. ( that won't delete my files will it )

edit: or should I try something else?

Sorry I'm in and out!

The web site has a link and instructions on creating a bootable CD.

Looking at the BSOD I would run chkdsk from the recovery console on your XP CD. The XP CD does have an automated revoery but I don't trust it and the last thing you want is to stuff Ububtu!

As you can guess I come from Windows and am new to Ubuntu!

---

### Post by Woody56292 on 2006-09-13
well if the windows cd will get me xp back without eliminating my files, I am all for that approach. ofcourse I will then have to be very careful next time I install ubu. ( cause I definately want to install it again, but if it is the thing giving me trouble now, shouldn't I trash it and hope xp still works? )

---

### Post by xpod on 2006-09-13
> all the space back to xp and it will work? ( i know that is like giving a fire a fire extinguisher, but maybe it will work itself out? )
Reply With Quote


Not sure where your at right now but just to give you another option....

My xp was recently on it`s own HD with a little bit of unallocated space on the end of it.Every time i tried to format that sapce to something Ubu could use i would get the BSOD when trying to boot to xp.But as soon as i undone what i had done XP would come back after hitting "last good config".

When i eventually messed about with things too much i realised that like you`ve been advised all i needed to do was reset the "active partition" with the use of "Fdisk" on a 98 bootdisk.

Unfortunately i missed that fix and carried on messing things up untill i was so fed up i hit "format c:" and gave ubunto the whole bloody disk and left XP off:twisted: .........UNTIL the wife started getting on my case and now it`s back again.........being it`s usual pain in the backside.

Hope you get sorted....but IF all else fails try just giving the space back and of course making sure the partition is active......just be careful if you do use fdisk

EDIT:...Just using the "upgrade" option on the cd leaves all your stuff in tact does it not???

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> Not sure where your at right now but just to give you another option....

My xp was recently on it`s own HD with a little bit of unallocated space on the end of it.Every time i tried to format that sapce to something Ubu could use i would get the BSOD when trying to boot to xp.But as soon as i undone what i had done XP would come back after hitting "last good config".

When i eventually messed about with things too much i realised that like you`ve been advised all i needed to do was reset the "active partition" with the use of "Fdisk" on a 98 bootdisk.

Unfortunately i missed that fix and carried on messing things up untill i was so fed up i hit "format c:" and gave ubunto the whole bloody disk and left XP off:twisted: .........UNTIL the wife started getting on my case and now it`s back again.........being it`s usual pain in the backside.

Hope you get sorted....but IF all else fails try just giving the space back and of course making sure the partition is active......just be careful if you do use fdisk
how do I do that? cause at this point, I would be happy to just uninstall Ubu and start over, if it means having all my files back.

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> Not sure where your at right now but just to give you another option....

My xp was recently on it`s own HD with a little bit of unallocated space on the end of it.Every time i tried to format that sapce to something Ubu could use i would get the BSOD when trying to boot to xp.But as soon as i undone what i had done XP would come back after hitting "last good config".

When i eventually messed about with things too much i realised that like you`ve been advised all i needed to do was reset the "active partition" with the use of "Fdisk" on a 98 bootdisk.

Unfortunately i missed that fix and carried on messing things up untill i was so fed up i hit "format c:" and gave ubunto the whole bloody disk and left XP off:twisted: .........UNTIL the wife started getting on my case and now it`s back again.........being it`s usual pain in the backside.

Hope you get sorted....but IF all else fails try just giving the space back and of course making sure the partition is active......just be careful if you do use fdisk

EDIT:...Just using the "upgrade" option on the cd leaves all your stuff in tact does it not???


I can't find my xp recovery cd. so I have to use the other iso cd option. haven't tried it yet, still trying to figure out how to remove my ubuntu partition/swap partition and seeing if that will work. any clue how to do that? ( in the cd there was a partition editor option, can't find it on ubu menu now )

---

### Post by Woody56292 on 2006-09-13
alright I am going to try uninstalling ubu and using the ubu iso cd to redo the partitions. might be offline for 10/20 minutes.

---

### Post by xpod on 2006-09-13
Im not entirely sure what you used in the first place but i imagine it was gparted that was used.
Just put the Ubu live cd back in,once it`s up & running go to gparted in the "system-administration" tab and once thats up and running you should see both your XP and UBU partitions.....Delete all the Ubu partitions.Now thats ALL i had to do to get XP back.....But if you resized the XP partition to begin with you could resize back again  to include all the now free unallocated space.

I would just delete the UBu partitions to start....while your in gparted look at the XP partiton and make sure it has the "boot lba" flag is in the end column.And does XP`s data show up at all as the "yellow band" within the white one?

Im new to all this so im only telling you what i did in a similar situation..
This is by no means expert advice that you must listen to.

If you have an XP cd though i dont know what the worry is......all you need to do is throw it back in........Unfortunately i was`nt so lucky but thats another story

---

### Post by Woody56292 on 2006-09-13
ok so I haven't done anything yet. ( I am running through cd )
so I just need to delete ubu paritions...
windows partition is yellow ( with some white ) and a green border...
flags says boot ( not boot lba )
so doing this wont cause more trouble right? Cause I am doing it..... now.

edit: ok what!!! 20gb was being used by linux ( hda2 ) so I deleted that. but the swap and extended are locked. I cannot delete them... why?
should I still restart and try to load xp?

edit again: ok nm it was mounted. I disabled it, now I just mount partition 1 and be done with it?

---

### Post by bodhi.zazen on 2006-09-13
LOL :lol:

Ok, we are now mounted. We have a permissions problem. Can fix later.

In a terminal, what is now the output of:```
sudo ls -la /media/windows
```.

I am just trying to see what you have in your windows partition to determine if we can rescue or if we need to re-install.

Even better```
gksudo nautilus /media/windows
```This should open a nautilus window to your windows partition. What do you see?

---

### Post by Woody56292 on 2006-09-13
Hey everybody!! it is your favorite xp idiot again. Wanna guess what mistake I made this time? I forgot to click apply to my partitions....](*,) 
lol I guess that is good since bohdi.zazen has me doing something different.
So everything is still the way it was.
ubuntu is active on partition 2, the cd is out, and xp still is on partition 1 and isn't working.

---

### Post by bodhi.zazen on 2006-09-13
> **Woody56292 said:**
> ok so I haven't done anything yet. ( I am running through cd )
so I just need to delete ubu paritions...
windows partition is yellow ( with some white ) and a green border...
flags says boot ( not boot lba )
so doing this wont cause more trouble right? Cause I am doing it..... now.

edit: ok what!!! 20gb was being used by linux ( hda2 ) so I deleted that. but the swap and extended are locked. I cannot delete them... why?
should I still restart and try to load xp?

edit again: ok nm it was mounted. I disabled it, now I just mount partition 1 and be done with it?

Now you are getting drastic. If you deleted the Ubuntu partition we will need to fix your MBR next. If you are not careful in your frustration you may do further damage. I am trying to recover your system or at least your data. Deleting and resizing partitions will not help in the recovery process.

FYI: The boot flag is set (thanks for the suggestion xpod).

Can we try to find out what is on /dev/hda1? (sudo ls -la /media/windows).

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> LOL :lol:

Ok, we are now mounted. We have a permissions problem. Can fix later.

In a terminal, what is now the output of:```
sudo ls -la /media/windows
```.

I am just trying to see what you have in your windows partition to determine if we can rescue or if we need to re-install.

Even better```
gksudo nautilus /media/windows
```This should open a nautilus window to your windows partition. What do you see?

I see absolutely nothing....
that is why...
woody@woody-desktop:~$ gksudo nautilus /media/windows
(nautilus:5078): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
woody@woody-desktop:~$

all the window popped up with is blank white....

---

### Post by xpod on 2006-09-13
Only WE ....can cause ourselves MORE trouble.These things only do what we tell them and unfortunately sometimes we tell them to do things that aint 
such a good idea.......OR "was`nt"...as is the case here;) 

Mind you ...i "take back" that bit about them doing what WE tel them all the time....:-k :mrgreen: 

Your xp data is THERE.....thats the main thing.KNOWING that is half the battle.

If it still dont "boot" to xp without probs then all you should need to do then is use a "bootdisk with fixmbr.........ive even used "fdisk/mbr" and that has worked before when my mbr has been messed but i`ll probably have all sorts of people shouting about how dodgy that can be blah blah blah.

It`s WORKED for me....evrytime

---

### Post by Woody56292 on 2006-09-13
woody@woody-desktop:~$ sudo ls -la /media/windows
total 8
drwxr-xr-x 2 root root 4096 2006-09-13 10:17 .
drwxr-xr-x 4 root root 4096 2006-09-13 12:42 ..
woody@woody-desktop:~$



yeah I guess it is a good thing I forgot to click apply partitions.

my hda1 still shows up 30gb full, so I must have the files still right?

---

### Post by bodhi.zazen on 2006-09-13
sudo ls -la /media/windows then please.

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> sudo ls -la /media/windows then please.

I posted them right above your post.

also why does partition 1 show up in temporary file and partition 2 has no access path???

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> Only WE ....can cause ourselves MORE trouble.**These things** only do what we tell them and unfortunately sometimes we tell them to do things that aint 
such a good idea.......OR "was`nt"...as is the case here;) 

Mind you ...i "take back" that bit about them doing what WE tel them all the time....:-k :mrgreen: 

Your xp data is THERE.....thats the main thing.KNOWING that is half the battle.

If it still dont "boot" to xp without probs then all you should need to do then is use a "bootdisk with fixmbr.........ive even used "fdisk/mbr" and that has worked before when my mbr has been messed but i`ll probably have all sorts of people shouting about how dodgy that can be blah blah blah.

It`s WORKED for me....evrytime
rofl I thought you were talking about me for a second. ( not computers )
ok so if I need to use fdisk.... how? I need step by step, because clearly leaving anthing to chance or common sense is going to cause problems for my computer.:mrgreen:


edit : I saw my files! that is a step. I clicked on the file path for hda1 ( don't worry I didn't change it ) and I saw all my xp files!!! my beautiful files are still there. :p  now I just need to find out how to get them back.

---

### Post by bodhi.zazen on 2006-09-13
Thank you. If this is the ouptput> woody@woody-desktop:~$ sudo ls -la /media/windows
total 8
drwxr-xr-x 2 root root 4096 2006-09-13 10:17 .
drwxr-xr-x 4 root root 4096 2006-09-13 12:42 ..
woody@woody-desktop:~$you have lost your windows XP partition. I am sorry.:( :(

Recovery of data may be possible, but this would be very specialized. If you want to do this, disconnect the HD now so as to do no further damage and choose a recovery method.

What to do: If you want to run windows XP you will need to re-install. To keep Ubuntu do not touch the current partitions or you would need to re-install Ubuntu as well.

After you re-install you will need to restore your MBR.

[How to re-install GRUB from the Ubuntu Live CD](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

---

### Post by bodhi.zazen on 2006-09-13
> **Woody56292 said:**
> rofl I thought you were talking about me for a second. ( not computers )
ok so if I need to use fdisk.... how? I need step by step, because clearly leaving anthing to chance or common sense is going to cause problems for my computer.:mrgreen:


edit : I saw my files! that is a step. I clicked on the file path for hda1 ( don't worry I didn't change it ) and I saw all my xp files!!! my beautiful files are still there. :p  now I just need to find out how to get them back.

Yes... Where are they? (path). (output of df -h again please).

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Thank you. If this is the ouptputyou have lost your windows XP partition. I am sorry.:( :(

Recovery of data may be possible, but this would be very specialized. If you want to do this, disconnect the HD now so as to do no further damage and choose a recovery method.

What to do: If you want to run windows XP you will need to re-install. To keep Ubuntu do not touch the current partitions or you would need to re-install Ubuntu as well.

After you re-install you will need to restore your MBR.

[How to re-install GRUB from the Ubuntu Live CD](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29)

how is that possible, I can see my xp files in the file path. they are just greyed out. and a few of them ( folders, are accessible. )

---

### Post by Woody56292 on 2006-09-13
well I clicked on disc manager ( the closest thing I could find to look at partition space... )
and when I look under partition 1 it tells me the access path is /tmp/disks-conf-hda1.
When i click "change" I can see xp files. example... dell, myxbox icon, documents and settings, sexyback.mp3 etc. ( don't hate that is a good song )

edit: but when I click browse partition 1, it says I don't have permission.

edit : p.s. you scared the crap out of me!:(

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Yes... Where are they? (path). (output of df -h again please).
woody@woody-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  1.9G   16G  11% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  233M   8% /lib/modules/2.6.15-26-386/volatile
/dev/hda1              75G   56G   20G  75% /tmp/disks-conf-hda1
woody@woody-desktop:~$



so now that we know all my files still exist, how do I get xp back? I think all I need to do is mount it and make it primary. so how do I do that and/or if necessary uninstall ubuntu?

---

### Post by bodhi.zazen on 2006-09-13
> **Woody56292 said:**
> well I clicked on disc manager ( the closest thing I could find to look at partition space... )
and when I look under partition 1 it tells me the access path is /tmp/disks-conf-hda1.
When i click "change" I can see xp files. example... dell, myxbox icon, documents and settings, sexyback.mp3 etc. ( don't hate that is a good song )

edit: but when I click browse partition 1, it says I don't have permission.

edit : p.s. you scared the crap out of me!:(

Are you running on the live CD? The mount point of your windows partition is unusual and it should be mounted on /media/windows.

At any rate, if you can see your data BACK UP. I think the answer to your question is because the partition is mounted read only to root. It is possible the windows partition is damaged.

Then you can try to restore the windows partition via either the windows CD or the microsoft site. I do not know how to do this as I do not have the expertise with microsoft.

---

### Post by xpod on 2006-09-13
If these other guy`s are helping you try recover the lot then wait see what happens.....I dont want to be giving you conflicting methods.

If that data is showing up as the yellow band then it`s definetely still there ......unless somebody knows something i dont.

All i know is i`ve experienced the same nonsense on more than one occasion due to my messing about but everytime XP gave me a BSOD all i had to do was delete the offending linux partitions

I now have XP and Ubu on the SAME hd but it only works when i leave a lttle unallocated space after the XP partition.I tried every way imaginable to stop the BSOD`s with linux on the same partition.

I used gparted on ubu live cd and gparted on it`s own live cd,and i used fdisk from a floppy to wipe and re-make and re-format that partiton but no matter how i did it i got a BSOD.......Until i left that little unallocated space after it.

Now i know yours is a slightly different situation but the UBU partition after the XP one resulting in a BSOD is`nt too much different......hence IF all else fails THEN it is something to consider.

Dont know what your presently trying but....well,see what happens eh.

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Are you running on the live CD? The mount point of your windows partition is unusual and it should be mounted on /media/windows.

At any rate, if you can see your data BACK UP. I think the answer to your question is because the partition is mounted read only to root. It is possible the windows partition is damaged.

Then you can try to restore the windows partition via either the windows CD or the microsoft site. I do not know how to do this as I do not have the expertise with microsoft.
no I am not running on the live cd. So I shouldn't take the other's advice and just uninstall/clear partition of ubu? 
or should I do the iso cd thing and run fdisk and try and repair?

( repartitioning sounds so much easier )

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> If these other guy`s are helping you try recover the lot then wait see what happens.....I dont want to be giving you conflicting methods.

If that data is showing up as the yellow band then it`s definetely still there ......unless somebody knows something i dont.

All i know is i`ve experienced the same nonsense on more than one occasion due to my messing about but everytime XP gave me a BSOD all i had to do was delete the offending linux partitions

I now have XP and Ubu on the SAME hd but it only works when i leave a lttle unallocated space after the XP partition.I tried every way imaginable to stop the BSOD`s with linux on the same partition.

I used gparted on ubu live cd and gparted on it`s own live cd,and i used fdisk from a floppy to wipe and re-make and re-format that partiton but no matter how i did it i got a BSOD.......Until i left that little unallocated space after it.

Now i know yours is a slightly different situation but the UBU partition after the XP one resulting in a BSOD is`nt too much different......hence IF all else fails THEN it is something to consider.

Dont know what your presently trying but....well,see what happens eh.

 I barely understand what you guys are saying, but I do think uninstalling and reinstalling ( repartitioning ) ubuntu would solve the xp problem.
My view is that if it didn't start having  the problems until after ubuntu, surely ubuntu must be the problem? ( not saying that it caused this, I know it was my own stupidity and lack of attention to detail... )

---

### Post by bulldog on 2006-09-13
Just take a windows install cd-rom and go into revcovery console.

One off the options you will have there is fixboot and another one is fixmbr.
Try them and if you didn't damage your XP-installation it should repare and install all the files needed for XP to start.

Your GRUB will be gone but your Ubuntu still is there.
By reinstalling GRUB you will be able to choose to boot in XP or Ubuntu.

But you need a Windows XP cd-rom.

[As I look at your postings I would advise you to search for a more experienced person to do this for you.]

Reacting on your post above.
You messed with gparted and uninstalling Ubuntu won't get you anywhere.
Your XP partiton is damaged and should be repared!!
Has nothing to do with your Ubuntu just with your messing around with gparted not knowing what you where doing.

---

### Post by Woody56292 on 2006-09-13
> **bulldog said:**
> Just take a windows install cd-rom and go into revcovery console.

One off the options you will have there is fixboot and another one is fixmbr.
Try them and if you didn't damage your XP-installation it should repare and install all the files needed for XP to start.

Your GRUB will be gone but your Ubuntu still is there.
By reinstalling GRUB you will be able to choose to boot in XP or Ubuntu.

But you need a Windows XP cd-rom.

[As I look at your postings I would advise you to search for a more experienced person to do this for you.]

yeah only I don't have a windows xp cd-rom. hence the problem...

---

### Post by xpod on 2006-09-13
> So I shouldn't take the other's advice

Just to clarify....i aint giving you advice but am merely explaining what i did in a similar situation.

i come HERE to get the advice too mate.....i Just noticed you having similar headaches to what i had recently.

Ive just spent the last couple of days re-installing my mother in laws XP with a bootdisk and a dusty old i386 directory on cd and if i never see another xp i386 file i`ll be a happy man..

I KNOW what advice i would give you but i`d probably be barred from the forum
:mrgreen: ........killbill

EDIT:....OH NO....Not you as well....haha...well at least now i know im not the only unlucky git who has to learn how to re-install with no XP CD`s.
THATS great fun.....](*,)

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> Just to clarify....i aint giving you advice but am merely explaining what i did in a similar situation.

i come HERE to get the advice too mate.....i Just noticed you having similar headaches to what i had recently.

Ive just spent the last couple of days re-installing my mother in laws XP with a bootdisk and a dusty old i386 directory on cd and if i never see another xp i386 file i`ll be a happy man..

I KNOW what advice i would give you but i`d probably be barred from the forum
:mrgreen: ........killbill

well your problem you had sounds similiar to my problem, and if your solution is a proven one.... why not just try it?
I can just put ubuntu on our second/guest computer.

---

### Post by Woody56292 on 2006-09-13
> **bodhi.zazen said:**
> Are you running on the live CD? The mount point of your windows partition is unusual and it should be mounted on /media/windows.

At any rate, if you can see your data BACK UP. I think the answer to your question is because the partition is mounted read only to root. It is possible the windows partition is damaged.

Then you can try to restore the windows partition via either the windows CD or the microsoft site. I do not know how to do this as I do not have the expertise with microsoft.

ok so would the world blow up if I just typed the access path as /media/windows instead of /tmp etc??
or would that not be a real location and just dump all my files.

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> If these other guy`s are helping you try recover the lot then wait see what happens.....I dont want to be giving you conflicting methods.

If that data is showing up as the yellow band then it`s definetely still there ......unless somebody knows something i dont.

All i know is i`ve experienced the same nonsense on more than one occasion due to my messing about but everytime XP gave me a BSOD all i had to do was delete the offending linux partitions
[COLOR="DarkOrange"]
I now have XP and Ubu on the SAME hd but it only works when i leave a lttle unallocated space after the XP partition[/COLOR].I tried every way imaginable to stop the BSOD`s with linux on the same partition.

I used gparted on ubu live cd and gparted on it`s own live cd,and i used fdisk from a floppy to wipe and re-make and re-format that partiton but no matter how i did it i got a BSOD.......Until i left that little unallocated space after it.

Now i know yours is a slightly different situation but the UBU partition after the XP one resulting in a BSOD is`nt too much different......hence IF all else fails THEN it is something to consider.

Dont know what your presently trying but....well,see what happens eh.


omg I just remember that when it was trying to auto set up last night it left a small ( half a gb or less ) portion in between xp and ubuntu and swap.
crap I knew I shouldn't of deleted it ,but it was unallocated so I thought I just messed up. So I deleted the linux and reinstalled it so there was no extra allocation inbetween them. ( cause I had already given my xp an extra 10gb attached to it...:(

---

### Post by Woody56292 on 2006-09-13
ok so my 3 options are....
1) burn an iso cd and attempt to repair windows through start up.
2) find a xp cd and repair.
3) delete and remove partitions for Ubu, then reinstall. ( kind of scared to reinstall now )

so... which one should I do?

---

### Post by Najand on 2006-09-13
Well, it sounds option 3 is useless as far as your windows booting command has been broken... To me number 2 is ideal...

---

### Post by Woody56292 on 2006-09-13
> **Najand said:**
> Well, it sounds option 3 is useless as far as your windows booting command has been broken... To me number 2 is ideal...

What do you mean my booting command is broken? I thought the problem was I just had to mount the windows partition instead of the ubu one. wouldn't it automatically make my windows partition active if I deleted the ubu one?
Around 4 pm I have to go, so if all else fails I will do option 3. Everything is there so there is no reason it shouldn't work.

---

### Post by Timothy Butwinick on 2006-09-13
Wait!
I just read through this thread, and I do not think you updated GRUB after editing its /boot/grub/menu.lst file! 

Write this:
sudo grub-install --root-directory=/dev/your_ubuntu_partition

---

### Post by Timothy Butwinick on 2006-09-13
Sorry about tthe double post.

Furthermore, a possible explanation for your problem is the following:
When you resized the NTFS partition, how much free space did you leave? Windows XP does not use a swap partition, but a part of the system drive. Maybe there is no place left for memory?

---

### Post by davec64 on 2006-09-13
> **Woody56292 said:**
> ok so my 3 options are....
1) burn an iso cd and attempt to repair windows through start up.
2) find a xp cd and repair.
3) delete and remove partitions for Ubu, then reinstall. ( kind of scared to reinstall now )

so... which one should I do?

I agree option 3 'aint a starter as the XP installation is stuffed!

As you've got Ubuntu up and running do a web search for EBCD.
This is a bootable CD image with a host of tools for repairing Windows, and believe it or not it Linux based!
It has a DOS prompt and you can run CHKDSK and/or SCANDISK which should repair the Disk file structure.

Reading your responses I don't think the NTLDR boot disk will have any affect, but might be worth just trying to confirm if you can boot into XP (if you can then my prrevious advice stands regarding the active partition).
The BSOD appears to confirm the need to run CHKDSK.

Hope this helps!

---

### Post by Woody56292 on 2006-09-13
> **Timothy Butwinick said:**
> Wait!
I just read through this thread, and I do not think you updated GRUB after editing its /boot/grub/menu.lst file! 

Write this:
sudo grub-install --root-directory=/dev/your_ubuntu_partition 
all I got is this....

woody@woody-desktop:~$ sudo grub-install --root-directory=/dev/your_ubuntu_partition
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
woody@woody-desktop:~$

---

### Post by xpod on 2006-09-13
Well.....there you go then......More similar than we thought eh

---

### Post by Timothy Butwinick on 2006-09-13
Sorry! It's my computer that's a bit slow today. I must have clicked too many times. :)

---

### Post by Woody56292 on 2006-09-13
ok I am out of ideas.:confused: 
I haven't tried the windows startup disc. ( cause I don't have one and don't know where to download one )

the repair thing seems like it would work but haven't done it yet.

I still think all I have to do is mount it... and make it primary.


anyone have any ideas, it is almost time for me to go.

edit: xpod can you explain to me step by step how you removed ubuntu and go xp to work again?

---

### Post by Timothy Butwinick on 2006-09-13
> **Woody56292 said:**
> all I got is this....

woody@woody-desktop:~$ sudo grub-install --root-directory=/dev/your_ubuntu_partition
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
woody@woody-desktop:~$

Exchange the your_Ubuntu_partition part for the name of your drive. I don't remember what fdisk -l 
said, but it should be listed there.

---

### Post by Woody56292 on 2006-09-13
Ok, I was lost without you guys.... I deleted the partitions for linux, but when I tried to restart, it popped up with a gnome! what on earth? then it gave me error code 22.

how is gnome still popping up when I deleted the partition that it was on?

I am lost... help.:(

---

### Post by Woody56292 on 2006-09-13
omg I am redoing the installation and now my hda 1 is going to be media/hda1. That is good right?:)

---

### Post by xpod on 2006-09-13
You mean "grub" surely?????
Well now you need to use fixmbr and you`ll need to get it onto a floppy disk

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

Or of course theres "fdisk/mbr" but again you`ll need a 98 startup disk at least...i have xp bootdisk`s(single and 6 pack) but find that a plain old 98/m.e bootdisk is fine for "fdisk/mbr"

"fdisk/mbr" only rewrites the first part of the boot record or something like that........As i said ....i aint no expert.

I have the fixmbr utility but the fdisk/mbr worked fine for me.

I really hope you get your xp back and i still firmly believe that if you can see that band of yellow data within gparted then your xp is still there.
Others seem to be telling you different and they probably do know better than moi...BUT...What harm can you do reverting it all back to how it was?

You aint got many other options it seems.......OR possibly you might just have TOOOOOO  many options from what im reading:confused: :-k :-#

EDIT: of course if your trying to reinstall Ubu again PROPERLY then that might work too:D

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> You mean "grub" surely?????
Well now you need to use fixmbr and you`ll need to get it onto a floppy disk

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

Or of course theres "fdisk/mbr" but again you`ll need a 98 startup disk at least...i have xp bootdisk`s(single and 6 pack) but find that a plain old 98/m.e bootdisk is fine for "fdisk/mbr"

"fdisk/mbr" only rewrites the first part of the boot record or something like that........As i said ....i aint no expert.

I have the fixmbr utility but the fdisk/mbr worked fine for me.

I really hope you get your xp back and i still firmly believe that if you can see that band of yellow data within gparted then your xp is still there.
Others seem to be telling you different and they probably do know better than moi...BUT...What harm can you do reverting it all back to how it was?

You aint got many other options it seems.......OR possibly you might just have TOOOOOO  many options from what im reading:confused: :-k :-#

EDIT: of course if your trying to reinstall Ubu again PROPERLY then that might work too:D

I figured reinstalling it was my only option. I highly doubt this is going to work though. I must need a cd or else use use fixmbr...

---

### Post by bulldog on 2006-09-13
The problem is not GRUB nor Ubuntu.

You get a BSOD,XP will boot but it fails!!

This is not going to be repaired by GRUB neither by uninstalling Ubuntu.

Your only option is by getting a Windows cd and try to fix it.

The second option is worth a try by mounting your existing XP one way or another and try to copy as much of your data as posible to your /home on Ubuntu.

But please,find someone who knows what he is doing!!
Is just an advice though,it's your data.

---

### Post by Timothy Butwinick on 2006-09-13
Grub should still be there (it is installed on the very first 255 bytes or so on your hard disk). Error code 22 means something like (I think): "When reading the /boot/grub/menu.lst file, it cannot find the partitions listed" (Note, however that it does not read the actual file that you have now removed, but the copy it makes during its installation).

1. Boot up with the Ubuntu live CD.

2. ```
sudo update-grub -y
``` This generates a new /boot/grub/menu.lst file (the old one refers to your formatted Linux partition, giving you an error, since it can't be found).

3. ```
sudo grub-install
``` This replaces the old gub installation, with your mew partitions.

4. Reboot the computer to see if it works.

It is not recommended to remove grub altogether, since you won't be able to boot at all (without a boot CD or floppy, that is).
If this works, you can either try to install Ubuntu again, or use Windows' boot program. I think the command is "fdisk /mbr", but I am not sure at all.

Edit: Bulldog: Replacing GRUB *does* work! I had the same error code, and this fixed it.

---

### Post by Woody56292 on 2006-09-13
ok now something is wrong. It is letting me access all my files from ubuntu. ( xp still won't work )
all the files are on hda 1, but they are accessible from ubuntu. does that mean that if I delete ubuntu this time, all my files will go with it?

---

### Post by Woody56292 on 2006-09-13
> **Timothy Butwinick said:**
> Do you mean "gnome" or "grub"?
Grub should still be there (it is installed on the very first 255 bytes or so on your hard disk). Error code 22 means something like (I think): "When reading the /boot/grub/menu.lst file, it cannot find the partitions listed" (Note, however that it does not read the actual file that you have now removed, but the copy it makes during its installation).

1. Boot up with the Ubuntu live CD.

2. ```
sudo update-grub -y
``` This generates a new /boot/grub/menu.lst file (the old one refers to your formatted Linux partition, giving you an error, since it can't be found).

3. ```
sudo grub-install
``` This replaces the old gub installation, with your mew partitions.

4. Reboot the computer to see if it works.

It is not recommended to remove grub altogether, since you won't be able to boot at all (without a boot CD or floppy, that is).
If this works, you can either try to install Ubuntu again, or use Windows' boot program. I think the command is "fdisk /mbr", but I am not sure at all.

 I don't think I need to anymore. I uninstalled it and reinstalled it.

---

### Post by bodhi.zazen on 2006-09-13
I agree with Bulldog. He has given the solution in his previous posts (thank' s bulldog, I was going to book mark this, but 12 pages !!!!). I posted twice how to restore you MBR.

FOLLOW BULLDOG'S ADVICE. PAGE BACK IF YOU MUST.

I also advised you back up your data. It is possible the windows partiton is in some way unstable and you could lose more data, [color=red]especially the way you are going about it[/color].

If you do not have a windows CD beg, borrow, or steal one!!. Get advice from someone who knows windows XP.

THIS IS NOT AN ISSUE WITH UBUNTU OR GRUB.

---

### Post by xpod on 2006-09-13
Whatever you need or dont need and whatever works or dont work......
...DONT get all worked up about it......It`s ONLY a stupid pc after all and if you have really important stuff on that xp of your`s then "there endeth the lesson"

People with important pc`s should`nt be playing with them in this manner(NO matter HOW experienced they think they are)

If you`ve got someone who can lend you an xp cd then your ok and if not then dont worry about it.......If xp dont show up,turn up or work without being f*$*$ed up then you`ve still got Ubu there until you can get a lend of one.

I only put XP back on this pc as "she who MUST be obeyed" demanded it of me..
NOT cause she use`s it as she dont BUT just to watch me squirm in her belief that i could`nt possibly re-install XP without a proper bootable cd....watch me dear

I did manage to borrow one but only at the exact same time as i finally sussed out how to re-install with a floppy and a dusty old i386 directory i had copied to cd.....

Ive had to do it twice now for the mother in law in the last few days and i`ll be glad if i never have to click in an xp ever again....

The more i kill it the more i learn from it..........JUST try look at it THAT way.................killbill:twisted:

---

### Post by bodhi.zazen on 2006-09-13
Timothy Butwinick: Your advice is good for fixing the grub error.

However the problem is with his windows install. Fixing GRUB will not fix windows and he will have to fix it again once he fixes windows as his MBR will be overwritten.

Woody56292: If you keep going, trying to fix without the windows CD, you will eventually lose your windows partition, one way or another.

---

### Post by Timothy Butwinick on 2006-09-13
Yes, I type to slowly.

The files won't be removed unless you format hda1. What you see is only a mounted drive: The files are still at their own disk. Mounting can be seen as linking the device (hda1) to a folder on your Ubuntu disk. This is done automatically when it is booted.

---

### Post by bulldog on 2006-09-13
> **Timothy Butwinick said:**
> Grub should still be there (it is installed on the very first 255 bytes or so on your hard disk). Error code 22 means something like (I think): "When reading the /boot/grub/menu.lst file, it cannot find the partitions listed" (Note, however that it does not read the actual file that you have now removed, but the copy it makes during its installation).

1. Boot up with the Ubuntu live CD.

2. ```
sudo update-grub -y
``` This generates a new /boot/grub/menu.lst file (the old one refers to your formatted Linux partition, giving you an error, since it can't be found).

3. ```
sudo grub-install
``` This replaces the old gub installation, with your mew partitions.

4. Reboot the computer to see if it works.

It is not recommended to remove grub altogether, since you won't be able to boot at all (without a boot CD or floppy, that is).
If this works, you can either try to install Ubuntu again, or use Windows' boot program. I think the command is "fdisk /mbr", but I am not sure at all.

Edit: Bulldog: Replacing GRUB *does* work! I had the same error code, and this fixed it.

Nope can't believe that.
You are right if XP never boot and you're get an error by GRUB.

In this case XP does boot but fails,implying GRUB is working correctly.
The messing up is done by XP not GRUB or Ubuntu.

---

### Post by Timothy Butwinick on 2006-09-13
Oh, sorry: I didn't realize that it was Windows that gave the error message.

---

### Post by bodhi.zazen on 2006-09-13
Bulldog, you the man.

---

### Post by Woody56292 on 2006-09-13
ok thanks for the advice and help. ( wow 13 hours of free tech support.:cool: )

I guess as long as I still have firefox and if I can get my email working, I will survive until I find a disc.

---

### Post by bodhi.zazen on 2006-09-13
No offense everyone, but:

[color=red][size=3]Bulldog knows the problem and the solution. Could we cut the chatter and allow bulldog to guide Woody56292 to the solution?

Woody: back up you data and follow bulldog's advice[/color][/size]

---

### Post by bulldog on 2006-09-13
Topic Starter does a good try to destroy his data.

By installing and uninstalling he WILL make an error and his XP will be gone to the XP-Heaven.

@TS
You can try what you want OR you can read and try the only thing that is going to help.

But I'm afraid that you manage to loose all your data by trying to get it back.

I advised you twice to get somebody overthere who has a little computer experience.

Last time then.

FIND SOMEBODY WITH AN XP CD AND IT SHOULD BE VERY VERY NICE TOO, IF YOU COULD FIND SOMEBODY WHO IS A LITTLE EXPERIENCED WITH COMPUTERS.

---

### Post by Timothy Butwinick on 2006-09-13
I have an XP CD, and would gladly share it if it were not illegal.

Can't you copy hda1 using:

1. mkdir temporarymnt

2. sudo mount /dev/hda1 ntfs temporarymnt (is this command right for NTFS disks?)

3. mkdir copied

4. sudo cp -R temporarymnt/* copied

---

### Post by xpod on 2006-09-13
AGAIN.....i was`nt giving you advice to DO......i was merely telling you what i did with my BSOD on my pc when i touched xp`s partition....

...and what ive done when ive merely messed up my mbr when trying to get round my unallocated xp space problem....

I could go now into gparted and format that 2g to the exact same fat32 as ive kept xp and my xp will give me a bsod.....DONT ask me why and dont tell me i need to do xy or z,,,,cause ive done them ALL....and ive used every piece of partitioning software out there.........SOME pc`s just seem to have some strange quirks ...and of course some users have even stranger ones but thats another thread;) 

Remember....dont fret..learn from it all....you`ll laugh about it once you suss and sort it all(im just one of the strange ones that laughs AS mines dies as apose to after)........(mind take a copy of that xp cd`s i386 if you borrow one....it does in emergancys)

EDIT:> I have an XP CD, and would gladly share it if it were not illegal.

IF he`s using his own product key then whats the problem....illeagal..HUH

---

### Post by bulldog on 2006-09-13
> **Timothy Butwinick said:**
> I have an XP CD, and would gladly share it if it were not illegal.

Can't you copy hda1 using:

1. mkdir temporarymnt

2. sudo mount /dev/hda1 ntfs temporarymnt (is this command right for NTFS disks?)

3. mkdir copied

4. sudo cp -R temporarymnt/* copied

It's not illegal if he borrows your cd.
He may not install it without a proper licence but that is not the case.
He need the cd to fix his MBR and nothing more.

It's 2 minutes of work IF he didn't borked his XP already.

By messing around installing and uninstalling an resizing partitions, the chance to get his data back gets smaller and smaller.

I get the feeling TS has no idea what he's doing and the risk of loosing his data gets bigger.

But as I said before,it's his data and is not important to me if he succeed.

The only thing I can do is give him a helping hand,but if he decide otherwise.it's oke to me.

---

### Post by Woody56292 on 2006-09-13
ok still searching for xp disc. hope I find it soon, having no email, wmp/itunes is really sucking.

edit: so the fixer isn't something I could download off the net and install on a cd?

---

### Post by bodhi.zazen on 2006-09-13
> **Woody56292 said:**
> ok still searching for xp disc. hope I find it soon, having no email, wmp/itunes is really sucking.

edit: so the fixer isn't something I could download off the net and install on a cd?

Learn to email, wmp/itunes with ubuntu:

```
sudo apt-get install aptitude
sudo aptitude install xmms streamtuner thunderbird
```

bulldog you the man. See my last 4 or so posts.

#-o can't keep my big mouth shut.

---

### Post by Timothy Butwinick on 2006-09-13
Maybe this will help: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
I do not know if it has got something for this issue, but it's worth a try.

---

### Post by davec64 on 2006-09-13
> **Woody56292 said:**
> ok still searching for xp disc. hope I find it soon, having no email, wmp/itunes is really sucking.


Bulldog is right, XP CD & Recovery Console to run CHKDSK is your first step, alternatively a boot cd with it on.

EBCD will let you copy files and folders to CD/DVD, this will preserve any data you want to keep.

Honest, EBCD is really good, we use it regularly when somebody stuffs Windows!

---

### Post by xpod on 2006-09-13
> FYI: The boot flag is set (thanks for the suggestion xpod).

Listen bulldog..as i emphasised to woody ,my tale of my calamity was in no way to be taken as advice...i was merely giving him a final thought if all else failed..
There is a comment from someone telling him his XP IS dead and even i in my limited experience can gather that this is not the case....His xp IS still(was still?)there as far as i can tell.

woody..i think you "jumped" at my sorry tale because your just so confused with all the other conflicting advive you were mabey GIVEN.
Thats the trouble with this forums.....toooo many psuedo pc experts.

And not enough sudo pc experts...;) 

Still.....IF it still dont work there`s always fdisk and format c:...THEN the xp problem will definetly be solved.....JOKE JOKE HAHA LOL(DONT DO)

---

### Post by bulldog on 2006-09-13
How did you install XP the first time?

If you bought your computer with it pre-installed you should have a disc.

When you only had a recovery partition and NO disc, contact the shop where you bought it.

Maybe they will help you out,but then again,maybe not.

There should be somebody in your neighberhood with an XP-CD.

Try to borrow it for 10 minutes,you only need it for a few minutes,you even do not have to enter a code.

Only the administrator password if installed you must know,because that is necessary to do the repair.

---

### Post by bulldog on 2006-09-13
> **bodhi.zazen said:**
> Learn to email, wmp/itunes with ubuntu:

```
sudo apt-get install aptitude
sudo aptitude install xmms streamtuner thunderbird
```

bulldog you the man. See my last 4 or so posts.

#-o can't keep my big mouth shut.

Thank you,to much honor though.

I did this several times when I borked up my machine and I know it's a little trouble to get things right.

---

### Post by Woody56292 on 2006-09-13
oh well live and learn, next time I should just stick to the demo.:p 
so what are the odds that it will work whenever I get the cd, cause I would hate to have to go through all this to find out even a cd wouldn't work.


edit: what would happed if I used a system recovery cd ( that doesn't match my computer? )

lol I know it probably won't do anything, but I figured I would ask.

---

### Post by bulldog on 2006-09-13
> **xpod said:**
> Listen bulldog..as i emphasised to woody ,my tale of my calamity was in no way to be taken as advice...i was merely giving him a final thought if all else failed..
There is a comment from someone telling him his XP IS dead and even i in my limited experience can gather that this is not the case....His xp IS still(was still?)there as far as i can tell.

woody..i think you "jumped" at my sorry tale because your just so confused with all the other conflicting advive you were mabey GIVEN.
Thats the trouble with this forums.....toooo many psuedo pc experts.

And not enough sudo pc experts...;) 

Still.....IF it still dont work there`s always fdisk and format c:...THEN the xp problem will definetly be solved.....JOKE JOKE HAHA LOL(DONT DO)

I know everybody wants to help TS and we all have different points of view.
That's allright and it make the forums so interesting to read.

But I have a little experience with computers,XP and Ubuntu and I know that my solution should have worked in the beginning before TS started to mess everything up.

Still I think that recovery is possible but not by Ubuntu or GRUB.

---

### Post by xpod on 2006-09-13
> If you bought your computer with it pre-installed you should have a disc.

Too many people buying pc`s and NOT getting any cd`s of any sort and not knowing any better.....It`s ON the pc and their happy.

But round about the same time their guarantee runs out SO does their XP run out and guess what...:twisted: 

This was my mum in laws old box bought new with no cd`s and dead 2 years later....Ive just re-installed XP(without xp cd)for her on the pc she has now that she was in the exact same situation with 19 months after buying it(18 month warrenty:eek: )

DEMAND THOSE XP CD`S PEOPLE

EDIT:> But I have a little experience with computers,XP and Ubuntu

I have a "little" too.......from march till now....hows that for a "little" experience....lol

---

### Post by Woody56292 on 2006-09-13
> **xpod said:**
> Too many people buying pc`s and NOT getting any cd`s of any sort and not knowing any better.....It`s ON the pc and their happy.

But round about the same time their guarantee runs out SO does their XP run out and guess what...:twisted: 

This was my mum in laws old box bought new with no cd`s and dead 2 years later....Ive just re-installed XP(without xp cd)for her on the pc she has now that she was in the exact same situation with 19 months after buying it(18 month warrenty:eek: )

DEMAND THOSE XP CD`S PEOPLE

EDIT:

I have a "little" too.......from march till now....hows that for a "little" experience....lol

I know for sure I had one. I remember looking at it wondering, [COLOR="Red"]why on earth am I still keeping this thin[/COLOR]g. It might be in the back with all the other piles of cds ( haven't found it yet ) or it might be in the trash.

the irony kills me.

---

### Post by bulldog on 2006-09-13
> **Woody56292 said:**
> oh well live and learn, next time I should just stick to the demo.:p 
so what are the odds that it will work whenever I get the cd, cause I would hate to have to go through all this to find out even a cd wouldn't work.

I should think about 100% :D 
Even if we can't fix the existing XP do a new install beside it and your data won't be lost.

But don't mess around anymore.

Try to copy as much data as possible when you mount your XP-partition to be sure.

And do no more resizing your parttions,cause that's the most dangerous thing to do!!!!

Get an XP-cd and be sure to kow the administrator password.
[Mostly on pre-installed it's just ADMINISTRATOR]

---

### Post by Woody56292 on 2006-09-13
OMG he does love me.
I just found my dell cds, magically right on the desk. ( no lie I have no clue how they got there )

so now I just put it in and restart my computer?

---

### Post by xpod on 2006-09-13
OMG....and i thought i was slower than a week in the jail...

ALL TOGETHER NOW....."DUH"!!!!!.......LOL

Oh it`s good knowing theres more dosy git`s like me out there.

\\:D/

---

### Post by bulldog on 2006-09-13
Yes boot from the cd.

Windows will come with some screens and look at "repair an existing XP" or something like that.
NOT THE AUTOMATIC REPAIR it will bring you nowhere.

You get three options,install windows,repair an existingt XP or quit.

Yust choose repair you get a black screen where the existing install [a number] is displayed.

Choose that number and then it asks for your administrator password.

Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.

Then you get a prompt.
Type   fixboot   and see what it tells you.
If this doesn't work type    fixmbr   and you get a warning about messing up things,but ignore,and proceed.

This should make your windows bootable again.

[print this out]

Your GRUB is lost but that 's a minor thing.
We get in that later it's really simple to restore.

---

### Post by bulldog on 2006-09-13
Lol, XPOD :D

I'm off for now.
Have to be up at six and it's almost midnight.
I come back tomorrow to see how it went.

Goodnight every one.

---

### Post by bodhi.zazen on 2006-09-13
Book mark that. Thanks Bulldog. Never know when I might have to repair a windows box.

---

### Post by xpod on 2006-09-13
I usually go round in circles SOOOOO much that im sure im about to vanish up my own backside....

I love it when i spend a week on google and forums and knowlage bases just to find out it was only 2 or 3 clicks away.....

Im a pc noob though not just ubunto...THATS my excuse!!!...I still get my DLL`s and my LOL`s mixed up for god`s sake.I know what all the bits are inside now though along with the extra bit`s i managed to squeeze in

Still.......i got that ISO burned which is more than some of the pro`s seem to manage:cool: ...IN FACT..i got a whole bloody distro deli here:D 

This poor guys been to dell and back:D ...all in the space of an evening which is pretty damm fast by MY reckoning

---

### Post by Woody56292 on 2006-09-13
man just when I needed him. it didn't work. I didn't try fixmbr.

it said ntdr was missing.
said filesysytem type was unknown. and now it looks like my files are all gone.:(  I suddenly think cd wasn't a good idea.


ok this sounds like a good idea, just tell me how to uninstall everything and I will create a new xp. I give up just give me xp back so I can start reinstalling my vast amount of stuff.:confused:

---

### Post by xpod on 2006-09-13
[http://www.bestpricecomputers.ltd.uk/freehelp/ntldr_missing.htm](http://www.bestpricecomputers.ltd.uk/freehelp/ntldr_missing.htm)

Still seems like your mbr is messed up OR of course worse.
I still say the xp is THERE if it still appears as yellow band in gparted

---

### Post by xpod on 2006-09-13
I only know how to use a bootdisk with fdisk to wipe,create and format the partitions from scratch.
You could of course wipe it with gparted but i had boot issues using other software to create my xp partition.

This was probably only my ignorance but i used fdisk to do all the wiping and formatting of half my hd for xp then i used gparted to do the other half for ubunto(of course on MINE leaving a tiny unallocated bit in between)

If it`s a proper XP cd you have you should just be able to go to setup and choose "upgrade" option and it will re-install your xp while keeping all your files.....Im looking at the copy i have ON my pc that i took from an xp cd and thats the option you want to chose if you just want to install with your old files staying in-tact

EDIT:Not sure if that way requests the product key but have it handy

---

### Post by Woody56292 on 2006-09-13
nope I put in the ubuntu cd just to be sure. ( checked partition manager )

it was all there, but no yellow inside of it. somehow between the cd and testing it again, it all disappeared. I am now using our old computer till I can take it to Doug, our computer guy. ( I guess in hindsight, I should of just gave it to him when I reazlied I couldn't get into xp in the first place. he probably could of gotten my information out.
oh well, it was a great learning experience and I am through being upset about it.

so thanks for the help everyone. let's all do the happy dance.\\:D/ 

problem solved.

---

### Post by blx_286 on 2006-09-13
> **Timothy Butwinick said:**
> Maybe this will help: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
I do not know if it has got something for this issue, but it's worth a try.

You might also find this link of use ... [http://ubcd4win.com/](http://ubcd4win.com/)

You can do some serious damage with it.

---

### Post by Mimsy on 2006-09-14
Might I suggest to just step back and do NOTHING until you've heard back from Bulldog, or someone else who gave usefuladvice earlier in the thread?


Just a thought...

Mimsy,
who now goes to bed, while muttering about "silly Americans, so desperate for instant solutions they'd rather mess things up even more than wait another few hours for osmething that might work"...

PS:
Seriously, just WAIT. From what I have seen of this thread so far, all your attempts to try out new things all the time is what turned your original situation from a large inconvenience into a much larger problem. Let the guy sleep, and check the forum again tomorrow.

---

### Post by xpod on 2006-09-14
Nothing wrong with messing up ones pc......This is how you learn what to do when future calamitys arise...
Mind you...IF you are being GIVEN advice in the first place that is the advice you need..THEN one should take the time to read that advice properly.

Again...if pc`s have important material on them THEN stick to messing around with those old spare pc`s.....NOT your main ones.

least you`ve got an xp cd it seems which is more than some have

---

### Post by davec64 on 2006-09-14
> **Woody56292 said:**
> nope I put in the ubuntu cd just to be sure. ( checked partition manager )

it was all there, but no yellow inside of it. somehow between the cd and testing it again, it all disappeared. I am now using our old computer till I can take it to Doug, our computer guy. ( I guess in hindsight, I should of just gave it to him when I reazlied I couldn't get into xp in the first place. he probably could of gotten my information out.
oh well, it was a great learning experience and I am through being upset about it.

so thanks for the help everyone. let's all do the happy dance.\\:D/ 

problem solved.

DOn't panic!!!!!

All is not lost!!

Use the NTLDR boot disk I mentioned earlier in thread to get into XP now. Whilst FIXMBR repairs the master boot record and prevents you from booting into Ubuntu, the indication you're getting possibly indicates the partition isn't active. Basically it's looking for NTLDR in the wrong partition.
The NTLDR boot disk bypasses the NTLDR.ini and NTDETECT.ini files held in the root of your XP installation (doesn't change anything) just to get into the XP Installation.

I'm sure this will work, as I've had to do it myself!

If at this point you get the BSOD, you need to go back to the XP boot cd and run CHKDSK.

Then run the NLDR boot disk again, an hopefully your in to XP.

Now you need to:
1) Back Up Yer Data!
2) Check your partitions to see which is active and make your XP C:\ partition active.

Then it's time to reinstall GRUB!

If your c:\ partiton is FAT32 you can run FDISK without having to use the NTLDR boot disk, and set the C:\ partion as active.
If you still get the BSOD, you still need to run CHKDSK.

All the best

---

### Post by bulldog on 2006-09-14
When you put in the windows cd how far did it go?

It first checks your partitions and see if there is a windows install somewhere.
Did you get any errors at this time?

Then if there where no errors it starts to copy some basic programs to your hdd.
Did it do that?

Then you get [just out of my memory,could be some way around] the option to automaticly repair,which you should skip.

Then you get 3 options install windows,repair an existing windows and quit.
Did you get there with no errors?

This is the moment to choose R for repare,and you get a black screen.
Here you see if it has found your windows install on your hdd and here you should login in the existing window with your password.
Then you can give the fixboot command and the fixmbr command.

If you got this far without errors,your windows must be accessible.

But on the other hand,when it checked your partitions and you got an error about your parttions,or it gave you no existing windows on your c:\drive then I'm afraid that your system is realy messed up.

But I can't believe that your NTFS partition is seen in Ubuntu and by restarting with the cd your partition has gone bad.

The cd does nothing more than check if everything is okay to install XP and that's it.

When the file system is not recognized, and be sure that we are talking about your windows install, and not Ubuntu which can't be read by XP.

When you boot with the windows cd go to the three options mentioned before and choose install instead of repair.
The next page should clarify if you windows still exist.
There you see all your partitions [Ubuntu as unknown] and if there is a C:\ drive you see what format it is [NTFS or FAT32]
What ever you do, do not format at this time cause that terminate any chance of repair.

If there is no c:\ but unallocated space instead there is to much damage done to your windows and repair is out of the question by normal programs.
You need a specialist to repair and they are not cheap.

But let me know first how far you came and what you did,before we decide your windows is dead.
And give me the errors if there where any.

[Reinstalling windows is about 30 minutes on a reasonable computer]

---

### Post by xpod on 2006-09-14
> Reinstalling windows is about 30 minutes on a reasonable computer]

LOL...it is with a nice proper bootable xp cd....AND 3-4 poxy hours plus the way i have to do it without a bootable one.
OH just to "have one lying on my desk" like that.....:rolleyes: LOL

Good luck mate

---

### Post by Mimsy on 2006-09-14
Oh, there is NOTHING wrong with mesing with, and up, a computer. It's one of the more entertaining things in life, as a matter of fact.

But when the mess has turned into a serious problem, that I have no idea how to solve on my own, common sense dictates that I stop trying, until I can get help. If I do keep trying anyway, I need to be aware that I'm probably going to mess things up even worse. The famous "monkey with soldering iron" analogy comes to mind.

But that's what forums like these are for. To keep the monkeys out of my cmputer! :) 

/Mimsy

---

### Post by Tobster on 2006-09-14
I had the same problem but it is easy fix so relax.  The bad news is that I lost the peace of paper that I wrote down on how to fix it.  But all I done was phone 0906 752 5600 it cost 75p (UK) per min.

If I find that sheet I let you know, but it is easy to fix

---

### Post by xpod on 2006-09-14
Whats THAT....the samaratins number just in case???????

---

### Post by Najand on 2006-09-14
Hmm, i think what  you really need to do is 
1. "back up" your valuable data.
2. Reinstall Windows
3. Restore Grub to your MBR.

---

### Post by bulldog on 2006-09-14
> **xpod said:**
> LOL...it is with a nice proper bootable xp cd....AND 3-4 poxy hours plus the way i have to do it without a bootable one.
OH just to "have one lying on my desk" like that.....:rolleyes: LOL
 
Good luck mate
 
You could try to burn an ISO from your windows,there are some apps who can do this for you.
So you can reinstall a little more comfortable the next time.
Symantec sells such a program and if you use Google there maybe even be a free program you can use.
 
I think TS is not responding anymore.
Too bad we can't take it to an end so we all could learn from it.
 
Some advice for people who have a problem with XP.
Do not ever resize your partitions when you can't boot in XP,it will damage your install beyond repair if your unlucky.
 
The best thing you can do is find another computer and search for a solution and let the broken one powerless.

---

### Post by xpod on 2006-09-14
> You could try to burn an ISO from your windows,there are some apps who can do this for you.
So you can reinstall a little more comfortable the next time.
Symantec sells such a program and if you use Google there maybe even be a free program you can use.


LOL....oh if only you knew...From the day i first used the xp a few months ago and discovered what an "i386" was directory i have been trying to make that bootable cd with a slipstreamed sp2...mmmmmmm..lol...over and over and over

I even managed to just re-direct the SFC  /SCANNOW utility to look in my "i386" rather than request an XP cd-rom so that was enough...for a while.

Of course "sod`s law" being what it is i soon NEEDED to learn one way or another...I did have the luxuary recently of a forum member going "above & beyond" the call of duty by sending me his XP & SP2....RIGHT at the same time i finally sussed out how to copy that i386 from pc to cd then back over with the bootdisk and chase down the "winnt.exe"(after wiping with fdisk of course:biggrin: )......Of course my i386 burn was corrupt also so i had to salvage a "amsm" from another dusty old copy hence the installs i do now are a jigsaw of "i386`s".........£80 for new XP....erm...NAAAAAA

I`ve not given up "making" that bootable disc but frankly i dont give a s**t about XP now....It`s just to shut the wife up

EDIT: how XP boot`s and how i`d LIKE to boot it are two different things

---

### Post by bulldog on 2006-09-14
> **xpod said:**
> LOL....oh if only you knew...From the day i first used the xp a few months ago and discovered what an "i386" was directory i have been trying to make that bootable cd with a slipstreamed sp2...mmmmmmm..lol...over and over and over

I even managed to just re-direct the SFC  /SCANNOW utility to look in my "i386" rather than request an XP cd-rom so that was enough...for a while.

Of course "sod`s law" being what it is i soon NEEDED to learn one way or another...I did have the luxuary recently of a forum member going "above & beyond" the call of duty by sending me his XP & SP2....RIGHT at the same time i finally sussed out how to copy that i386 from pc to cd then back over with the bootdisk and chase down the "winnt.exe"(after wiping with fdisk of course:biggrin: )......Of course my i386 burn was corrupt also so i had to salvage a "amsm" from another dusty old copy hence the installs i do now are a jigsaw of "i386`s".........£80 for new XP....erm...NAAAAAA

I`ve not given up "making" that bootable disc but frankly i dont give a s**t about XP now....It`s just to shut the wife up

EDIT: how XP boot`s and how i`d LIKE to boot it are two different things

You will get there,if you're determined enough.
You have the right attitude to solve any problem and you can face them all if neccessary.
Wish you all the best and see you around on the forums,hopefully with no problems to our self,but trying to solve the problems of another.

Cheers.

---

