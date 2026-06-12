---
title: "Installed Ubuntu: XP won't boot anymore"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by peterhuang913 on 2007-12-28
I just installed Ubuntu to my existing XP and my XP isn't booting. When I select it and press enter, it says Starting _. It just stays there. I have 3 partitions: NTFS, ext3, and swap. Any ideas?

---

### Post by nunnst on 2007-12-28
And why is that a problem?  Sorry for the sarcasm...hopefully, when you installed ubuntu you did not reformat your ntfs partition.  Boot to ubuntu, mount the ntfs partition and look at it to see if your files are still there.  If they are not, someone with more experience will have to help you.  If they are there you probably have a grub problem.  There is a lot of info in these forums about grub and searching the forums should give you the info you need.

---

### Post by peterhuang913 on 2007-12-28
Its automatically mounted as hda1 and my files are there.

---

### Post by Peyton on 2007-12-28
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=651379](http://ubuntuforums.org/showthread.php?t=651379)

---

### Post by peterhuang913 on 2007-12-28
I did fixmbr and fixboot and now it says "A disk read error occured". No GRUB, no nothing.

---

### Post by spydon on 2007-12-28
Try to reinstall GRUB then maybe...
I shall look for some usefull links brb.

---

### Post by Zip247 on 2007-12-28
this will help you re-install grub

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by spydon on 2007-12-28
This one is good if you have an ubuntu live cd or any other live cd that comes with gurb.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by peterhuang913 on 2007-12-28
GRUB CD says it cannot be installed :(

---

### Post by ingram on 2007-12-28
when you added the new partitions how did you set them up and with what options.

I am assuming you resized your windows partition. 

Did you try to slim it down before hand ?
Did you run defragment ?

What options and setup did you use. See there are certain rules about where partitions can be that kind of thing and there is a chance you may have overwritten a block you need.

I think I explained that right. :(

---

### Post by spydon on 2007-12-28
Can you run 
```
cat /boot/grub/menu.lst
```
You said your windows partion were mounted as hda1, right?
Then one part in the menu.lst should look something like this:

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

If it doesn't it's probably something wrong in there and if you post that windows part we can figure it out.

Like ingram said something could have gone wrong at the partion part too.

---

### Post by peterhuang913 on 2007-12-28
It shows:

title Microsoft Windows XP Home
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by spydon on 2007-12-28
> **peterhuang913 said:**
> It shows:

title Microsoft Windows XP Home
root (hd0,0)
savedefault
makeactive
chainloader +1

Nothing looks wrong there...
Maybe something went wrong when you did the partion, can you describe how you did it?

---

### Post by meierfra on 2007-12-28
Are you able to boot into Ubuntu again? Or the LiveCD? Post the output of

 ```
sudo fdisk -l
```
(l is a lower case L)

---

### Post by peterhuang913 on 2007-12-28
> **spydon said:**
> Nothing looks wrong there...
Maybe something went wrong when you did the partion, can you describe how you did it?

Down size xp form 10gb to 6gb. Make a swap with size of 250mb with unallocated and use the rest of unallocated as ext3. When through install and manual partition setup. Set ext3 mount to "/", format check, and went to do the install.

---

### Post by spydon on 2007-12-28
> **peterhuang913 said:**
> Down size xp form 10gb to 6gb. Make a swap with size of 250mb with unallocated and use the rest of unallocated as ext3. When through install and manual partition setup. Set ext3 mount to "/", format check, and went to do the install.

Then ingram is probably right... :(
Some windows system files might have been deleted when you formated. Windows tend to spread all over the partion it is dedicated and if you don't defrag before it is not unlikely that files gets deleted.

But you say that you can mount the windows partion, maybe backup the data you have there and reinstall windows and then reinstall GRUB from the live cd. But I'm not 100% sure that windows acctually is missing system files.

Maybe a checkdisk(chkdsk) can tell if there is any corrupted files on your windows partion. If you have a windows cd this shouldn't be too hard doing it might even be a app for doing this in ubuntu.

---

### Post by peterhuang913 on 2007-12-28
> **meierfra said:**
> Are you able to boot into Ubuntu again? Or the LiveCD? Post the output of

 ```
sudo fdisk -l
```
(l is a lower case L)

```
Disk /dev/hda: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x218d218c

   Device Boot      Start         End       Blocks     Id   System
/dev/hda1            1           803       632258   6   NTFS
/dev/hda2   *        804         1621      773193    83  Linux
/dev/hda3            1622        1653      257040    5   Extended
/dev/hda5            1622        1653      257008+  82 Linux swap / Solaris
```

---

### Post by meierfra on 2007-12-28
Assuming you are able to boot into ubuntu:

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```
(l is a lower case L)

Change 

title Microsoft Windows XP Home
root (hd0,0)
savedefault
makeactive
chainloader +1


to 


title Microsoft Windows XP Home
root (hd0,1)
savedefault
makeactive
chainloader +1


save the file and reboot.

---

### Post by peterhuang913 on 2007-12-28
It still won't boot.

---

### Post by spydon on 2007-12-28
> **meierfra said:**
> Assuming you are able to boot into ubuntu:

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```
(l is a lower case L)

Change 

title Microsoft Windows XP Home
root (hd0,0)
savedefault
makeactive
chainloader +1


to 


title Microsoft Windows XP Home
root (hd0,1)
savedefault
makeactive
chainloader +1


save the file and reboot.

Doesn't that change it to hda2 :S his windows is on hda1...

You can try doing this:
```
e2fsck /dev/hda1
```
that is like checkdisk in ubuntu.

---

### Post by meierfra on 2007-12-28
What was on your drive before you installed ubuntu?

Also post the output of


```
mkdir XP
sudo mount -t ntfs /dev/hda1 XP
cat XP/boot.ini
```

---

### Post by meierfra on 2007-12-28
> Doesn't that change it to hda2 :S his windows is on hda1...

Oops.I don't know what I did.  Somehow then I looked at "fdisk" I thought XP was on "hda2". Must have been sitting on the computer for  too long. So menu.lst  needs to be changed back.

Sorry about that.

---

### Post by spydon on 2007-12-28
> **meierfra said:**
> What was on your drive before you installed ubuntu?

Also post the output of


```
mkdir XP
sudo mount -t ntfs /dev/hda1 XP
cat XP/boot.ini
```

I think you have to you umount it first to remount it. It's maybe easier to cd into the directory where you got windows mounted now and do 
```
cat boot.ini
```

Now I'm off for bed I can barely keep my eyes open I hope you can help him meierfra :).

---

### Post by meierfra on 2007-12-28
> e2fsck /dev/hda1

 e2fsck only works on ext2 and ext3 file systems. Not on ntfs.

---

### Post by peterhuang913 on 2007-12-28
> **meierfra said:**
> What was on your drive before you installed ubuntu?

Also post the output of


```
mkdir XP
sudo mount -t ntfs /dev/hda1 XP
cat XP/boot.ini
```

You want to see what is in boot.ini?

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn

```

---

### Post by meierfra on 2007-12-28
Well I wanted to see it when I  thought that windows is on /dev/hda2. Because then there was a chance that boot.ini was pointing to the wrong partition.

Anyway, boot.ini seems to be fine.

---

### Post by Zip247 on 2007-12-28
peterhuang913  

Did you happen to remove a recovery partition at the same time you created your new partitions.  Just asking cause I am having the same problem getting windows to boot.

 [http://ubuntuforums.org/showthread.php?t=651379](http://ubuntuforums.org/showthread.php?t=651379)

---

### Post by meierfra on 2007-12-28
Now I know why I thought Windows  is on hda2.  The boot flag is on hda2. That is very strange. The "makeactive" statement in  menu.lst should have put   the boot flag  on hda1.

---

### Post by peterhuang913 on 2007-12-28
Ubuntu failed me :(

---

### Post by spydon on 2007-12-29
If you are going to reinstall windows you can probably fix it if you use the same partions.
reinstall windows on the partion that it was on and then install GRUB or you can just reinstall Ubuntu too after you reinstalled windows because I think it went wrong when you did the partions so if you reinstall both everything should work fine.

---

