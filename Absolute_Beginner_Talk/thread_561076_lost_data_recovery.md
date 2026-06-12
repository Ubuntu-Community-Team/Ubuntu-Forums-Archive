---
title: "lost data recovery"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-09-27
Hy guys!
I completely freaked out. I'm working from home right now and i lost completely one of my folders where I used to keep some important stuff. It is not big, only about 10-20 MBs. Yesterday it was there, today, nothing. I have to recover it quick.

I searched a little, but didn't find posts like this. If there are, please, post a link!

Any help will be greatly appreciated!

thanx

---

### Post by hyper_ch on 2007-09-27
Data doesn't just vanish, what did you do?

Furthermore do you have backups?

---

### Post by justleen on 2007-09-27
did you search for the files? might accidently moved them, perhaps?
otherwise you might try [test disk]("http://www.cgsecurity.org/wiki/TestDisk"),  [drtools]("http://dr-tools.sourceforge.net/") or [spinrite]("http://www.grc.com/spinrite.htm")

---

### Post by duruttye on 2007-09-27
Unfortunately I don't have any backups. I am the only one who uses this pc, yesterday I worked in this folder, today, when I started it, I had an error message, it said, the the gnome didn't start, and som themes and sound don't work, when I will restart is, itwill work. So I restarted it, and the folder wanished.

Right now I'm trying the photrec tool, but it will take more than 2 hours to complete, after that, idonnow, i'll try thos other tools yoy said.
thanx

---

### Post by justleen on 2007-09-27
folders dont just disapear, in general...

Did you check the lost+found folders? trash?
or a system wide search?
```
sudo find / -name <filename>

```

---

### Post by ayenack on 2007-09-27
Another thing to try is a Live CD and examine the drive to see what's on it. Check this out [e-fense]("http://www.e-fense.com/helix/contents.php"). I doubt the data has been deleted so should still be on the HD. If it has been deleted and you've got ext3 then you don't stand much of a chance of getting it back unless you're willing to spend some money on data recovery.

---

### Post by duruttye on 2007-09-27
Where can I find the lost+found folder?

this photorec tool found more than 100.000 files, about 15 GB, mostly in .txt format. any ideas how can I find in there folders, and photos?

Another thing. I tried slocate, this is the mesage:

slocate szenas
slocate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old

---

### Post by justleen on 2007-09-27
lost and foud is in your root dir  (/)

There is a lost and found on every partition / disk!  (so /media/disk1 has a lost and found in its oot"as well!)

most of the tools mentioned will find loads and loads of files..

---

### Post by duruttye on 2007-09-27
There is nothing in the lost +found folder...
right now i'm deleting movies and music, just to make room for the 20 GB of data and still groving...

And yes, I do have ext3, and no way it was deleted, still, I have no clue whatsoever, what happened to this folder. And why this folder, why not the movies folder, or music, or whatever else.
Anyway I'm pretty pissed off.
Even if this photoreg tool recover it... there is no way to find it, because it gives files names ike f9856423 and something... in 20 GB...

In the system log or somewhere like this, can I find something about deleted files history???

---

### Post by duruttye on 2007-09-27
Hey guys! 
I found some stuff in the .nautilus/metadata folder. There are some .xml files, and hey look like the folders I lost, at least their names do. What does that mean. The other files look like some paths to old deleted folders, or something like that.

Does this mean, that the folder was deleted???

---

### Post by justleen on 2007-09-27
thats just some metadata nautlius keeps about foldes/files you've visisted...

---

### Post by ayenack on 2007-09-27
Have you tried looking at the HD with a Live CD this will often show up files that can't be seen on the original system. [Knoppix]("http://www.knoppix.org/") if you've got a pretty powerful system with a GIG of ram or more can loaded into ram at boot prompt type toram and then have the CD/DVD drive free. There's also [e-fense]("http://www.e-fense.com/helix/contents.php") which I listed earlier more specific tools but can be pretty involved to use.

---

### Post by duruttye on 2007-09-27
yessss, I was close:))

the photoreg tool still orking, the time to complete is growing, so is the data recovered.
any idea how to find something in this recovered stuff? now it's over 200.000 files found...

---

### Post by duruttye on 2007-09-27
> **ayenack said:**
> Have you tried looking at the HD with a Live CD this will often show up files that can't be seen on the original system. [Knoppix]("http://www.knoppix.org/") if you've got a pretty powerful system with a GIG of ram or more can loaded into ram at boot prompt type toram and then have the CD/DVD drive free. There's also [e-fense]("http://www.e-fense.com/helix/contents.php") which I listed earlier more specific tools but can be pretty involved to use.

I'm downloading the knoppix already, but it will take a while... until then I'm trying to fix my problem, I have only about 600 mega ram, but I will try it still.
I misplaced the ubuntu cd, so I have to wait until the  photoreg tool and the knoppix download finishes, 

Thanx

---

### Post by duruttye on 2007-09-27
Sorry, my mistake, I'm downloadng the Helix:)

---

### Post by duruttye on 2007-09-27
So, here is what I did:
downloaded helix, burned it, botted it.  didn't mount any filesystems, so I couldn't look fo the lost folders...
rebooted, the grub was broken
fixed the grub
rebooted, gdm was broke, fixed that too
rebooted again, now I lost some themes, had some unnalocated inodes and god knows what else.

I think I might hve a hard drive with errors.
any ideas how to check that out???

---

### Post by ayenack on 2007-09-27
Re-boot your comp and select recovery mode at boot and when at the command line type.

**fsck**

This will check the drive for errors you will have to answer yes a lot during the file system check bare with it until it finishes. You may have a HD that's on it's way out. Seems strange that you keep getting errors. After it finishes boot into Ubuntu and check lost and found folder to see if anything is there.

---

### Post by ayenack on 2007-09-28
Have just re-read your post it was late last night when I read it and didn't take it all in. In Helix if I remember correctly you'll have to mount the drives manually. Take a look at this for info on the mount command.

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

To list partitions do this in terminal.

**sudo fdisk -l** (Will list partitions with basic info).

For more info do this in terminal.

**df -Th** (Gives more in depth info with path to file. For more info on the commands that can be used with this type **df --help**. So for instance **df -Th -a** will list all partitions).

To list what's already mounted do this in terminal.

**mount** (Info on mounted devices with path to folders, permissions etc. Agian with **--help** for options as with all commands).

Hope this of some help. ayenack.

There's also the Helix help forums for a guide on how to use Helix [here]("http://www.e-fense.com/helix/forum/index.php").
If your drive is on the way out check out [CloneZilla]("http://clonezilla.sourceforge.net/").

---

### Post by duruttye on 2007-09-28
Hey!
I'm sorry to dissapoit you, but I don't think I will try the helix again... no hard feelings:)

I already started to recover my data, from email inboxes etc, but I don't have nearly as much as I would like.

I changed the processor today, and after boot, it checked the drives, probably because the clock was not set, or something, I don't know exactly why, but it didn't find errors. If I'm not mistaken, that was done by fsck.

Just to be sure, I rebooted in recovery mode, tried to run fsck, but t said, that if tha drice is mounted, sevre damage can be made. So I tried to umount, with no luck.
The command sudo umount -f  /dev/sdb1 returned with error something like unable to umount, drive or resource busy... or something similar.

I really need to check the errors on this drive, because today some other folders dissapeared, but they are not that important.
The other trouble is, when I try to save some pictures with gimp on this drive, exprot in jpg format, it makes a staight blue line instead the picture... a file with 300-400 Bytes...

well
thats it for now...
let''s see who has some ideas :D

---

### Post by duruttye on 2007-09-28
The fdisk /dev/sdb1 command gives me this:


Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.


The number of cylinders for this disk is set to 4786.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)


What the heck is that??
Should I open a new thread?
Some wild sh*t going on on this drive :)) ....at least for me

---

### Post by duruttye on 2007-09-28
And yessss, bingo
it says exactly the same thing for my other " healthy" drive...
funny

---

### Post by ayenack on 2007-09-29
Yes when you changed the CPU the drive would have been checked by fsck (**F**ile **S**ystem **C**hec**k**).
Is this an external drive or an SATA drive? You should be able to run fsck from recovery mode, why you can't I do not know.

You can force the system to run fsck on the next boot by doing this. Close any open apps music players and what not.

Open a terminal and type.

**sudo -i**

Then.

**cd /**

Then.

**touch /forcefsck**

Then Re-boot system.

**reboot**

But if you ask me you have hardware problems of some kind. Let me know what happens.

Also do this in terminal.

[B]sudo apt-get install rkhunter
sudo rkhunter --update
sudo rkhunter -c[/B]

Thsi will check for any root kits on your system.

Good luck. ayenack.

---

