---
title: "Tried to install Ubuntu, lost my partitions. Need help, seriously."
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by kNick on 2006-10-07
Hello world!

First of all, everyone should know that this is really urgent, and serious. Because the data that SEEMS TO BE lost, or at least inaccessable, is really important. 

So, i tried Ubuntu at school, since we were learning about Linux and stuff. and i thought it was really cool! Now, i told my dad about it, and he, even though he's not much into computers and stuff, wanted to try it. So i burn Ubuntu onto a CD, and i let him try it out a little, running from the CD.

I told him that he'd be able to do a lot more, and that it would run faster if we installed it onto his harddrive, and he told me to do so.

Here the problem starts...

I start installing Ubuntu, and while doing so i see that the computer only got one partition. One big NTFS partition with Windows on. (i choose to manually edit partition table btw..)

So, i resize it, giving me about 10Gb of unallocated space.
Now i create two new partitions, one as root partition and one for swap... (with correct filesystems etc..)

Now at the next screen, i get a little confused. mount points?
I think to myself, nono... so i back up, thinking i'll let the installation do the partitioning all by itself.

What do i see? i see that all the partitions i created are black, "Unknown" filesystem. I think, oh well, maybe i should just quit the install and dig up some info about installing this before i try again. So i quit the installation, hoping everything was going to be alright, and reboot the laptop.

Now, guess what? "Error loading operating system". Period.

I've tried fixing it with a WinXP install CD, using recovery console. i.e., FIXBOOT, FIXMBR... nothing helps. 

Looking at "Gnome Partition editor" this is what i see:

```

Partition     Filesystem     Size

/dev/hda1     FAT32          7.81GB     (Hidden, probably created by the Laptop vendor for some reason...)
/dev/hda2     Unknown        68.71GB    (Flagged as -boot)
unallocated   unallocated    7.84MB

```

I assume something screwed up the filesystem (NTFS) on my drive... So i lost the partition with Windows, and all my dads files on. It havent been formatted, so the data should be there alright.. but how do i restore it so that i can boot back into Windows?

---

### Post by gn2 on 2006-10-07
Looks like you created the new partition at the start of the drive, where Windows needs to be.

This is not irrecoverable.

Before trying anything else I would suggest you get the hard drive in an external USB drive ASAP and copy the required data onto another PC.

Once the data is safe you can use Partition Magic to shift the Windows partition back to the start of the drive, and run "fixmbr" from recovery mode.

Lesson learned: Dual-booting on one hard drive can SERIOUSLY ruin your day.

---

### Post by kNick on 2006-10-07
Yeah, i know Dual boot can be a bitch, but this time i really got it smack in my face. thanks for the reply, i think i'll just somehow back up all the important files and format the drive, then install Windows again. Will report back later.... if not sooner.

---

### Post by gn2 on 2006-10-07
> **kNick said:**
> Yeah, i know Dual boot can be a bitch, but this time i really got it smack in my face. thanks for the reply, i think i'll just somehow back up all the important files and format the drive, then install Windows again. Will report back later.... if not sooner.

Just make sure you get Dad's files safe!

If my son zapped mine he'd be living in the shed in the garden for a month or two....

Good luck with the backup!

---

### Post by kNick on 2006-10-07
Hold on now..... Bah, figures. Can't access the files, can i? Since the partition is "unknown". any solution? The only thing running on the PC right now is the Ubuntu LiveCD. Since i'm new to Linux, i dont know what i got to work with. Help >.<

(lol, i just feel like . <- that small, compared to my usual geek-ego which is otherwise huge. I'm linux newb >.<)

Anyone willing to help via MSN, feel free to PM me here. i'd really really really appreciate it.

---

### Post by CatKiller on 2006-10-07
For the purposes of backup, so that you can get back to this point if you happen to make it worse (!), you don't need to be able to actually **read** the files as such. If you have a second hard drive that is the same size or bigger than the one you are backing up, and assuming that you've put your dad's drive as Primary Master and the other drive as Primary Slave, then the command ```
dd if=/dev/hda of=/dev/hdb
```will make a bit-by-bit copy of your dad's drive onto the other drive, messed-up filesystem and all. The command ```
man dd
``` will tell you more about this command. **Make sure that you get the *if* and *of* parts correct** otherwise, you'll end up blanking your dad's drive. ```
man mount
```should tell you more about the hard drive device names.

This will take a while to complete, depending on how large the drive is.

Then you can experiment somewhat with attempting to fix the partition table in the knowledge that you won't be more screwed than you are now.

EDIT: [This post]("http://ubuntuforums.org/showthread.php?t=269214"), or [this one]("http://www.ubuntuforums.org/showpost.php?p=1557220&postcount=10"), may explain a bit about what mount points are - they might not, though, because they're mine - or [this Wiki entry]("https://help.ubuntu.com/community/Mount").

Good luck.

---

### Post by kNick on 2006-10-07
[COLOR="Red"]UPDATE[/COLOR]

I fixed the MBR... windows now TRIES to boot, but bluescreens half-way through loading. It seems some files are missing.

Any tips on what to from now on?

---

### Post by odinfromvalhalla on 2006-10-07
try the [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php")

---

### Post by gn2 on 2006-10-07
Here's how to do a Windows Repair Install: [http://www.pcstats.com/articleview.cfm?articleid=1755&page=5](http://www.pcstats.com/articleview.cfm?articleid=1755&page=5)

It's an article about replacing a MoBo, but applies equally to your problemo.

Just make sure to back-up first...

Here's another excellent source of info on XP: [http://www.theeldergeek.com/](http://www.theeldergeek.com/)

---

### Post by adrian15 on 2006-10-10
> **kNick said:**
> [COLOR="Red"]UPDATE[/COLOR]

I fixed the MBR... windows now TRIES to boot, but bluescreens half-way through loading. It seems some files are missing.

Any tips on what to from now on?

I supose that the partition table is not exactly the same you had before the lost of it.

Try to re-generate again your partition table with testdisk from a live cd or a ms-dos floppy.

You can also use the gpart command from a console from a live cd. I do not know if it is included by default in knoppix or not.

adrian15

---

### Post by bulldog on 2006-10-10
Try the live cd and mount your windows partition.

Now you can read them and copy them to a cd or another hdd.

Boot the live cd and make a mountpoint```
sudo mkdir /mnt/rescue 
```
mount with ```
sudo mount -t ntfs /dev/??? mnt/rescue 
```

Now you can acces the partition by clicking your mountpoint.

---

