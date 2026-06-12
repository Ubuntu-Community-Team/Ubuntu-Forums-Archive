---
title: "Question about external hard drive before I make the switch..."
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by emma.meg on 2006-09-06
Hello everyone!

I have been a Windows user all my life but I really want to make the switch to Linux. I currently have a Thinkpad T43 (2686DHU if you want to see the specs). I was planning on just taking the plunge, so I bought an external hard drive to back up all my media (I have quite a few MP3s and large video files).

I just realized that the Maxtor OneTouch III requires Mac or Windows. I have no other place to back up my files, so I need to use this (or exchange it for another external hard drive). If I were to move all my files to this hard drive and then install Ubuntu, would it recognize the hard drive? I plan to access it often so this is something that I hope won't be problematic.

For the record, I have pretty much no experience with Linux other than reading about how awesome it is. 8)

Your thoughts would be much appreciated.

Thank you!

---

### Post by bodhi.zazen on 2006-09-06
Your shiny new drive is very likely to work with no problems.

Experiment: Save a mp3 file from windows to the new USB drive.

Boot Ubuntu -> play the mp3 form the hard drive.

If that works, you are good to go.

If not, or you need help re-post.

---

### Post by reacocard on 2006-09-06
It'll be fine. USB hard drives and other devices use the "USB Mass Storage" standard for interfacing with your operating system. This is supported natively by Linux, Windows and OSX. The warning about PC/Mac is likely only for the included backup software, which won't run on Linux. There are a number of freely available Linux backup programs that work well (sbackup,partimage).

---

### Post by gn2 on 2006-09-06
Another alternative is to replace your internal hard drive with a shiny new one and install on that.

You can either put your old one away for safekeeping, or put it in an external USB hard drive enclosure/caddy (cheap on eBay) for use as additional storage.

---

### Post by aysiu on 2006-09-06
Testing the MP3s won't work until you install the proper codecs, but you should pop in the Ubuntu live CD and test to see if it recognizes the external hard drive as... an external hard drive. It *should*, but it never hurts to double-check.

---

### Post by bodhi.zazen on 2006-09-06
> **aysiu said:**
> Testing the MP3s won't work until you install the proper codecs, but you should pop in the Ubuntu live CD and test to see if it recognizes the external hard drive as... an external hard drive. It *should*, but it never hurts to double-check.

He he he.. I was trying to show him what he was getting into, now you've given it away.

---

### Post by emma.meg on 2006-09-06
*She* has realized what she's getting into. ;)

I'm now writing to you from my fully installed Ubuntu desktop complete with working wireless. You were right -- it recognized the external drive just fine.

Thanks for your help!

...

On second thought, I just tried renaming my external hard drive but it wouldn't let me because it's read-only. Which means I can't transfer any files either. How do I change that?

---

### Post by aysiu on 2006-09-07
What filesystem is the external hard drive?

---

### Post by emma.meg on 2006-09-07
I'm guessing you mean if it is FAT32 or NTFS...I don't actually know how to find that out. I right-clicked and looked in Properties but I didn't find anything there.

---

### Post by aysiu on 2006-09-07
Can you paste back here the output of this terminal command? ```
sudo fdisk -l
``` Make sure the drive is plugged in before you enter the command.

Oh, and this command, too, would be helpful: ```
df -h
```

---

### Post by emma.meg on 2006-09-07
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS


-- and for the other code --

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G  2.0G   49G   4% /
varrun                252M   84K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  164K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/sdb1             280G   19G  262G   7% /media/New Volume

---

### Post by aysiu on 2006-09-07
Yup... looks like it's /dev/sdb1... and that's NTFS, which means read-only.

There's some experimental software out there that will allow you to read/write NTFS, but I don't recommend it. Your best bet is to reformat it as FAT32 or Ext3.

---

### Post by elemental666 on 2006-09-07
I use a Maxtor OneTouch II, yours will work fine as well.  What you have to watch out for is the FS you format that monster with.  There are some free utilities on the intarweb you can dl to give windows ext2/ext3 support.  I suggest installing one of these utilities and formating the drive as ext3.  Then backup what you need and blow windows away.  When you boot to linux you'll have a fully native environment.

I'd stay away from trying any of the NTFS read/write hacks out there... just cause... I lost a metric butt load of movies trying it that way and its just not worth the risk.

So here's what ya do:
1. Boot to the LiveCD (or to Ubuntu if already installed)
2. Format your extrenal as ext3
3. Reboot back into Windows
4. Install this: [http://www.fs-driver.org/](http://www.fs-driver.org/)
5. Copy what you want to save to the external
6. Reboot back into the live CD and install Ubuntu
7. Go by a case of Heini's and throw a NO BILLS PAST THESE GATES party!

NOTES: Do not install that utility and have windows format the  drive as ext3...  that's wrong on so many level your leetness will wither and die before your very eyes.

Do not format that drive as NTFS hoping to figure it all out later (this road could cost you all your data).

---

### Post by emma.meg on 2006-09-07
I looked up ext3 on Wikipedia and it says it's only usable in Windows through an IFS. Formatting it as FAT32 would be more versatile for connecting to other OS then? And what program do you use to format?

One last really silly question -- I have no idea how to actually manage my files. I mean, where do you put them? I have two "places" that show up besides my CD drive and external HD -- the Root Volume and the Filesystem. When I click on them, they appear to the be same thing. And even then, there's a ton of folders that I don't know where to actually put my stuff like media, docs, etc.

And thank you! You've been so helpful. :)

---

### Post by emma.meg on 2006-09-07
> **elemental666 said:**
> I use a Maxtor OneTouch II, yours will work fine as well.  What you have to watch out for is the FS you format that monster with.  There are some free utilities on the intarweb you can dl to give windows ext2/ext3 support.  I suggest installing one of these utilities and formating the drive as ext3.  Then backup what you need and blow windows away.  When you boot to linux you'll have a fully native environment.

I'd stay away from trying any of the NTFS read/write hacks out there... just cause... I lost a metric butt load of movies trying it that way and its just not worth the risk.

So here's what ya do:
1. Boot to the LiveCD (or to Ubuntu if already installed)
2. Format your extrenal as ext3
3. Reboot back into Windows

First off, sorry to hear about losing all those movies. Something like that happened to a friend of mine on her Mac and she freaked. Hopefully you've recuperated some. ;) 

I don't actually have Windows anymore on this laptop. So I'm not sure where that leaves me with your instructions...

---

### Post by JNowka on 2006-09-07
My suggestion to you, if you have already overwritten windows is to copy the files back to the internal HDD and format the sucker to FAT32 if you plan on using it with other OS's, like maybe friends and family members.  Once it is formatted copy the files back to the External and you are done. :)

---

### Post by elemental666 on 2006-09-07
> **emma.meg said:**
> I don't actually have Windows anymore on this laptop. So I'm not sure where that leaves me with your instructions...

Oh, I thought your were trying to back up media off your windows box before turning it into a linux box...

Anyway, I was explaining how to avoid having to deal with the limits of MS filesystems and still be able to read/write to the drive from either windows or linux.

---

### Post by blackened on 2006-09-07
> One last really silly question -- I have no idea how to actually manage my files. I mean, where do you put them? I have two "places" that show up besides my CD drive and external HD -- the Root Volume and the Filesystem. When I click on them, they appear to the be same thing. And even then, there's a ton of folders that I don't know where to actually put my stuff like media, docs, etc.

The only folder that you have unlimited access to by default is your /home/*username* folder. In there you can freely create subfolders for your media, documents, etc. To write anywhere else on the drive you need to have either root or superuser privileges. The root user is not enabled by default in Ubuntu.

There is a pretty good description of the filesystem structure [here]("http://www.ahinc.com/linux101/structure.htm").

---

### Post by reacocard on 2006-09-07
> And what program do you use to format?
gparted. Open synaptic (System->Administration->Synaptic Package Manager) search for it, and install. Then Gparted will be under System->Administration->Gnome Partition Editor.

---

### Post by emma.meg on 2006-09-07
I'm going to do the reformat tonight. Thanks everyone -- you've been super helpful.

---

### Post by emma.meg on 2006-09-07
I'm really stumped at this point. I can't reformat -- I posted the problem in [this thread]("http://ubuntuforums.org/showthread.php?t=253109"). I'm hoping to do this before I finish packing for school tonight. Help please?

---

