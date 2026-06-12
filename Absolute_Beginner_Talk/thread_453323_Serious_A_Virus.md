---
title: "Serious?: A Virus?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-24
I dont' know whats going on

I have an external USB drive, right. It has music on it.

So, there is a folder in there, which has some files. No biggie.

i was looking for a file just now, so I did a find / ...... command.... and i noticed that it froze, and kept searching over and over again in the same directory on this drive, I had NO knowledge this directory (bizarre characters) existed.

I didn't need this directory, so I went to delete it. The drive had become read-only, and i can't change the permissions!

I managed to delete the folder, and it went into the ./trash on the external to permanently delete it.... no dice!

So i gksudo nautlilused the directory, and there a BIZARRE bumber of randomly named files in there... and i can't delete it. The drive is read only, even though I am set as read and write file properties. 

I know this is confusing, but I am lost. Help me, please.

---

### Post by Hobo Joe on 2007-05-24
Try and do a quick virus scan on the drive. It would probably be better to do that with a Windows anti-virius though, becuase if it is a virus, it is almost surely a Windows one.

---

### Post by taurus on 2007-05-24
What format is that USB drive?  You cannot remove files from it even if you are root if it's ntfs filesystem.  You need to install ntfs-3g before you can modify stuff on that harddrive.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by drowner on 2007-05-24
> **Hobo Joe said:**
> Try and do a quick virus scan on the drive. It would probably be better to do that with a Windows anti-virius though, becuase if it is a virus, it is almost surely a Windows one.

Yeah, but its not affecting me throuigh windows.

I found one of the bizarre files... the date modfifed is the year 2030

they have names like ee.ee.... its entirely strange.

---

### Post by drowner on 2007-05-24
> **taurus said:**
> What format is that USB drive?  You cannot remove files from it even if you are root if it's ntfs filesystem.  You need to install ntfs-3g before you can modify stuff on that harddrive.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Nah, mate, its fat32.

I knew that

thing is, i write to it everyday! its only when i tried to delete this stuff that it becomes read only..... its weird!

---

### Post by taurus on 2007-05-24
Does it automount when you plug it in or do you mount it by hand, from a terminal?

```
ls -la /media
```

---

### Post by drowner on 2007-05-24
it automounts.
the ls -la /media:

```

total 52
drwxr-xr-x  5 root   root  4096 2007-05-24 23:18 .
drwxr-xr-x 24 root   root  4096 2007-05-08 07:18 ..
lrwxrwxrwx  1 root   root     6 2006-01-15 08:29 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2006-01-15 08:29 cdrom0
drwxr-xr-x  2 root   root  4096 2007-05-11 23:28 dan
drwx------ 15 daniel root 32768 1970-01-01 09:30 EXTERNAL200
-rw-r--r--  1 root   root   212 2007-05-24 23:18 .hal-mtab
---xr-s--T  1 root   root     0 2007-05-08 07:25 .hal-mtab-lock
```

the drive in question is the EXTERNAL200 one.

---

### Post by Hobo Joe on 2007-05-24
> **drowner said:**
> Yeah, but its not affecting me throuigh windows.

Scan it anyway, just to be safe.

---

### Post by drowner on 2007-05-24
Ok, so i unmounted it.

Then remounted it (it appears to be read and writeable again!)

then i found the folder in question, in the .trash.... etc folder

pressed delete

and nautilus hangs, on 'preparing to delete files.

Bizarre.

---

### Post by glenndavy on 2007-05-24
hey there drowner

so ATM the files are in .trash on the usb stick?
what happens if you simply empty the trash?

alternatively what happens when you sudo rm -fr /path_to_usb_mountpoint/.trash  from with in a shell?

---

### Post by drowner on 2007-05-24
Firstly, now that i remounted, and apparently i can read and write again, i tried to delete the folder.

And it tells me there are 383 files in there (there aren't, well there shouldn't be) and then it hangs on 'preparing to delete files'

I may have to unmount violently (unplug it) and try from a shell, cause its currently hung.

---

### Post by drowner on 2007-05-24
THIS IS GETTING WEIRD

I had to xkill the deleting files window, and then i tried to rm -rf etc, but the device unmounted itself (probably cause i xkilled the window where it was trying to delete files on there)

OK.

So, it remounted. I can create a file on the disk, so its not stupidly read-only. Good.

I deleted that file. Double good.

Here goes, with the sudo rm -rf.

I'll do a 'sudo rm -rf /media/EXTERNAL200/.trash-daniel/*'

that should work, right?

---

### Post by drowner on 2007-05-24
OMG WHAT IS GOING ON

```
~$ sudo rm -rf /media/EXTERNAL200/.Trash-daniel/
Password:
Sorry, try again.
Password:
rm: cannot lstat `/media/EXTERNAL200/.Trash-daniel//The Best Of//lc_mess.AGE': No such file or directory

```

---

### Post by drowner on 2007-05-24
AND NOW, THE DISK IS READ-ONLY AGAIN!!!!!!!!

(ssss was a test file I created)

 sudo rm /media/EXTERNAL200/.Trash-daniel/ssss
rm: cannot remove `/media/EXTERNAL200/.Trash-daniel/ssss': Read-only file system

---

### Post by drowner on 2007-05-24
This Is Freaking Weird

---

### Post by drowner on 2007-05-24
Sorry to keep bumping.

It seems that its creating a random number of files, deleting them, and creating more, and making the drive read-only.

Bizarre. Absolutely bizarre.

---

### Post by 3rdalbum on 2007-05-24
It just sounds to me like directory corruption - not an uncommon thing on Fat 32 partitions.

Try running fsck on it.

---

### Post by Soybean on 2007-05-24
Sometimes when there's a disk access error, linux will remount the drive read-only. It's standard procedure with ext2/3, at least... I don't know about fat32.

I'm guessing something got corrupted on your drive (hardware error, power spike, walked by a magnet, solar flare, voodoo... something), and the corruption coincidentally occurred in such a way that it looked like a directory to linux. When you tried to delete it, it first tried to back up that directory (which is really just noise) to your trash before deleting, so now there's a mess in there too.

I'd recommend backing up your data and formatting the drive. If it came with a formatting tool, or if there's one on the manufacturer's website, use that. Maybe look for a diagnostic program, too, in case the hardware is actually failing (as opposed to an isolated incident).

---

### Post by headcronie on 2007-05-24
Same thing happens with SD cards.  I 2nd the idea of backing up your data, and reformating your drive.

---

### Post by drowner on 2007-05-24
Well its my entire music collection, so i'm hesitant....

but its all on my ipod, so i suppose i could TRY... but i have it all so neatly organised....!

---

### Post by tgalati4 on 2007-05-24
What is the model of the USB drive?  Sometimes USB controllers are slow and some operations (like deleting large blocks of files) take a while to complete.  Pulling the drive is a sure way to corrupt the filesystem, regardless of the file system type.  If fsck doesn't fix it, then there could be some bad blocks on the drive (from transport--it is portable afterall).  This would require a low-level format using the manufacturer's setup disk (or Ultimate Boot CD) to verify the disk surface.  If you have access to a mac, run disk utility and it can perform a verification and repair if necessary.  

If the drive is routinely used between different machines and operating systems, it's not surprising that the drive got corrupted.  USB drives are convenient, but they subject the physical disk to conditions that are outside of specification.

For instance, if it is a cheap USB drive (or a homebuilt one) then the drive may have low tolerance for shock and temperature.  If it is an expensive USB drive, then perhaps it has been tested and certified for portable use including high temperature use and high shock tolerance.  Anyone take an iPod jogging?

But it's also a good idea to scan if for viruses from Windows.  Just to be sure.

---

### Post by glenndavy on 2007-05-24
as an earlier posted alluded  - on a fat32 system - this is generally symptamtic of a corrupted fat. 
check the out fsck.vfat command. 

If the fats corrupted then doing pretty much anything,including virus scanning, will give bizar results on those files.

---

### Post by drowner on 2007-05-24
> **tgalati4 said:**
> What is the model of the USB drive?  Sometimes USB controllers are slow and some operations (like deleting large blocks of files) take a while to complete.  Pulling the drive is a sure way to corrupt the filesystem, regardless of the file system type.  If fsck doesn't fix it, then there could be some bad blocks on the drive (from transport--it is portable afterall).  This would require a low-level format using the manufacturer's setup disk (or Ultimate Boot CD) to verify the disk surface.  If you have access to a mac, run disk utility and it can perform a verification and repair if necessary.  

If the drive is routinely used between different machines and operating systems, it's not surprising that the drive got corrupted.  USB drives are convenient, but they subject the physical disk to conditions that are outside of specification.

For instance, if it is a cheap USB drive (or a homebuilt one) then the drive may have low tolerance for shock and temperature.  If it is an expensive USB drive, then perhaps it has been tested and certified for portable use including high temperature use and high shock tolerance.  Anyone take an iPod jogging?

But it's also a good idea to scan if for viruses from Windows.  Just to be sure.

its a samsung 200gb hard drive in a $5 case off ebay. ;)

---

### Post by tgalati4 on 2007-05-24
I'm not familiar with Samsung drives.  What is the brand of the USB enclosure?  When your data gets hosed, you start to pay attention to those things.

I prefer LaCie drives, they work well with Macs and PC's and have Firewire and USB in a solid metal enclosure.  They are also pretty fast.

Please share the results of your fsck.

---

### Post by irish_flu on 2007-05-24
I hope that fsck fixes it; I'd bet ten bucks the problem is some kind of filesystem or partition issue (maybe one that Windows tolerates better than Linux, or something?).

Were there any odd characters (originally, not after they got all jumbled heh) in the name of the directory, or files within it?

---

### Post by drowner on 2007-05-25
The names of the files kept changing, it was bizarre... somtimes foreign characters, sometimes parts of decipherable words, really weird

so I had a brainwave... I would partition 40gig of that drive as ext3, back up all data (it was less than that) into there (EXCEPT the troublesome ./Trash!) and then hose the fat32 partition

Didnt work.... couldnt shrink the partition (gParted gave an error)

fsck.vfat couldnt do anything, it also produced an error

all my music is on my IPod anyway, so i hosed it.

Reformatted 2 partitions:  fat32/ext3. I used to unmount it pretty harshly... like when windows crashed, etc, so i suspect its a sort of file corruption.

---

### Post by lilro on 2007-05-25
can you backup your music to your computer? if so, do that then reformat your usb drive.

---

### Post by drowner on 2007-05-25
nah lilro, i can't.... there's no room, which is why i bought the USB drive to begin with ;)

But its all on my ipod, so i guess the plan is:

Import all the ipod files

organise, if need be, using easytag.

Songbird is still a little buggy.

---

### Post by argie on 2007-05-25
Just throwing this in. The last time I had a similar problem my USB drive was beginning to fail. After a while it had complete junk on it (in strange characters, some of which didn't show up completely i.e. I got the boxes). Good luck anyway.

A similar thing also happened to me just today when I accidentally unplugged the USB drive while writing to it. The table got corrupted and the drive became read-only. I had to format it again. Good luck with yours.

---

