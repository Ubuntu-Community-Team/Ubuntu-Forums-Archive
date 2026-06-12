---
title: "external harddrive ntfs concerns"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Bobtheknight on 2006-12-09
Greetings

In this Christmas season many of electronics stores near me are almost halfing their external hard drive prices.  So I am tempted to buy one.  

I know there has been problems with linux reading ntfs format on windows partitions.  I also know that you have to format a drive(USB) before you can use them.  Will this be a problem for my external drive?

I seem to be able to read/write my USB key which is formatted using a windows box fine.

Are there any extra things I should be aware of buying an external hard drive?

Thanks for all the help.

---

### Post by bscbrit on 2006-12-09
There should be no problem _reading_ an nfts drive and, recently, there has been software released that also allows writing to ntfs, but I have not tried it and cannot say how good it is.

Reading from an external drive does not require reformatting.  Writing to one has the same problems as above.  FAT and FAT32 are no problem and you can read from ntfs but I'm still not sure about writing to one.

---

### Post by Herman on 2006-12-09
>  I know there has been problems with linux reading ntfs format on windows partitions. What? Who told you that? Catweasel? :D  (Just joking).
Linux has no problem *reading from* an NTFS drive, it's just *writing to* one that most people don't recommend.
>   I also know that you have to format a drive(USB) before you can use them.  Will this be a problem for my external drive? I seem to be able to read/write my USB key which is formatted using a windows box fine.  Well I format my USB drives with [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"). It's no problem at all. If the drive comes formatted with NTFS, and you don't like it that way, just reformat it to ext2, ext3 or reiserfs with GParted LiveCD. Simple! :D
>  Are there any extra things I should be aware of buying an external hard drive? Hmmm :-k
I guess it depends on how you plan to use one. I have a nice external usb drive made of a laptop hard disk in an aluminium caddy that's just the right size to be easily carried around in a pocket if I wanted to, but most of the time it just sits around on my desk. It's 60.0 GB, and cost about $120 for the hard disk, plus $20 for the caddy. That was around a year ago, they would be cheaper now.
A usb thumb drive can be from $30 for a 128 mB model the size of my little finger, to $75 for a 1.0 GB one not much larger physically. I'd say the larger (GB) they are, the cheaper they are on a per GB basis. Smaller in physical size per GB is better and more valuable though, who wants to be carting a big old heavy brick around?
On the other hand, if it's only going to be sitting around on a desk, then there are 300 GB models available for the same price as a laptop hard disk but they are the 6"x4"x1" inch size and too heavy to carry in even a large pocket (you'd need a belt and suspenders), but they would be the best value of all on a per GB basis.

I made a new how-to today on adding Grub to a USB drive if you're interested in it, Grub makes a USB drive even more useful,
NEW!   How to add Grub to your USB thumb drive......................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive.")

Regards, Herman :D

---

### Post by Bobtheknight on 2006-12-09
Okay, so linux reads ntfs, but sometimes doesn't write to it.  Is there anyway to know if write succeeded?  Like If I am able to open a file correctly under linux environment after I copied from linux does that mean it worked?

Are there additional concerns writing to ntfs partition (ie. corrupt other files?)

And finally... does external hard drives work similar enough to a USB key(at user level) that if I can use my USB fine I really shouldn't get my panties into a knot over this?

Oh and thanks for Gparted-LiveCD tutorial.  I havn't looked at it yet, but I will because I plan to make my external drive bootable.  (Or at least with a partition that does so)  

Would you recommend Gparted over QTparted?

Thanks for the help

---

### Post by Frank Golden on 2006-12-09
> **Bobtheknight said:**
> Okay, so linux reads ntfs, but sometimes doesn't write to it.  Is there anyway to know if write succeeded?  Like If I am able to open a file correctly under linux environment after I copied from linux does that mean it worked?

Are there additional concerns writing to ntfs partition (ie. corrupt other files?)

And finally... does external hard drives work similar enough to a USB key(at user level) that if I can use my USB fine I really shouldn't get my panties into a knot over this?

Oh and thanks for Gparted-LiveCD tutorial.  I havn't looked at it yet, but I will because I plan to make my external drive bootable.  (Or at least with a partition that does so)  

Would you recommend Gparted over QTparted?

Thanks for the help
I have two Linux distros sharing a HDD with XP Pro on my laptop
in addition I have several external USB HDD's the external drives
are NTFS and the XP Pro partition's are NTFS. They are easily
mounted and read from in either distro but I choose not to 
use the "experminental" software to write to NTFS. Too experimental.
This prevents me from messing up the NTFS stuff. I have a Fat32
partition on my laptops HDD specifically for shareing between Linux and XP. If I need to save data from linux to an external drive I can save it first to my Fat32 partition and then copy it over using XP.

You could format your USB drive Fat32 and be done with it.
Be aware of the 4GB file size limit in Fat32 though. You would then have full R/W priveleges.

---

### Post by Herman on 2006-12-09
> Okay, so linux reads ntfs, but sometimes doesn't write to it. Is there anyway to know if write succeeded? Like If I am able to open a file correctly under linux environment after I copied from linux does that mean it worked? Are there additional concerns writing to ntfs partition (ie. corrupt other files?) I don't really know, I have never had much to do with NTFS myself. I have tried it out. I have not tried writing to it. I imagine it would corrupt the whole filesystem and I wouldn't try it unless I was trying out the software bscbrit mentioned. Maybe I'll convert a FAT32 Windows install to NTFS tomorrow and try writing to it and see what happens, in a test computer, just for the fun of it. I'll let you know. 

You can copy files from NTFS into Linux or open files and read them from Linux, either of those things are called 'reading'.

'Writing' is pasting files into NTFS or opening files in NTFS from Linux and changing them and saving the changes. Those are things we normally don't try to do with NTFS. I don't think you would really know if a write 'succeeded'.  What if it did something damaging to the filesystem that didn't show up until later on? Yes, I imagine a bit of filesytem corruption would spread to other files. I'm only guessing though, I'm only a beginner with learning about filesystems.
> And finally... does external hard drives work similar enough to a USB key(at user level) that if I can use my USB fine I really shouldn't get my panties into a knot over this?
 Well mine works exactly the same way. It's really simple. I just plug it into a USB port the same as a usb thumb drive and Ubuntu mounts it, when I'm finished I either leave it plugged in or right click the icon on the desktop and click 'eject' to unmount it. Always remember to do that, don't just unplug them without ejecting (unmounting) them first. That might cause filesystem damage even on a good filesystem like ext3.
Also, if you choose a linux filesystem like ext3, you can run filesystem checks on it from Ubuntu or from GParted LiveCD. Here's a link,            Running a filesystem check on an ext3  filesystem....................................................................[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")
I think USB drives are great. It's much faster and easier to copy large amounts of data to a USB disk than it is to make lots of CDs or DVDs when you want to make a big backup. Better value for money too, especially in the long run. :D
>  Would you recommend Gparted over QTparted? I do use QTParted sometimes when I am using a Knoppix CD or another KDE operating system like Kubuntu. It's a good 'Parted based partitioner.
GParted is the ultimate though, especially GParted LiveCD. I consider it by far the most advanced partitioning software available that I know of anyway. It can do lots of things no other partitioning software can do, and it still keeps getting better. :D

Regards, Herman :D

---

### Post by Herman on 2006-12-09
Well I converted Windows from FAT32 in one of my computers to NTFS but no matter what I did i couldn't write to it. So I made a seperate NTFS data partition and I still can't write to it, I have tried reasonably hard and been rather persistent. It seems like a waste of time.
If you buy a usbdisk that is formatted with NTFS, I would say the best thing to do would be to delete the filesystem and reformat it with some other filesystem. (With a GParted LiveCD).

FAT32 would be good if you want Windows and Linux to both be able to read and write to it. 

Ext2 or ext3 or reiserfs if you want a little more security. (If you loose it or someone steals it and whoever picks it up doesn't know anything about Linux they might not be able to 'see' anything in it and snoop around through your files. Actually, you could set the Linux file permissions so that even if they do know Linux only you can read and write to it if you wanted to, as long as they don't know your password.
Linux file permissions are a big and interesting subject. It's well worth learning about and practicing up on. Hmmm, :-k I could learn more about that myself, it's been a while since I looked into that. It's very useful. I think I'll go try out some cmod and chown commands out and see what I can learn.

Here are a few links I have looked at already that look interesting. I would recommand a Linux filesystem like ext3, it would be good to be able to use these great Linux file permissions to keep your data in your USB drive secure and private.
[**File** security]("http://www.faqs.org/docs/linux_intro/sect_03_04.html")     |    [**Linux** Files and **File Permissions**]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html")    |    [**File Permissions** - **Linux** Forums]("http://www.linuxforums.org/security/file_permissions.html")

Regards, Herman

Here, this should the trick! :D
```
 sudo chmod -R 700 /media/usbdisk
``` After that code has been applied to your usbdisk, you will have full access to it but no-one else will be able to open it. Linux is cool! :cool:

---

### Post by bscbrit on 2006-12-10
Herman, do not rely on file permissions to secure your data in event of loss.  It is trivial to boot a linux computer as root and change the permissions to something else.

Only encryption can provide some level of protection, but it is fairly easy to set it up under linux.

Thank you for trying the experiment, although it doesn't sound like you have installed the experimental ntfs software that I read about.  I cannot find a link for it at present, but I will go back to reading the magazines and see if I can find it.

---

### Post by Herman on 2006-12-10
Thanks bscbrit,
It seems like you are correct. I actually did use my wife's computer to change the file permissions and open a usbdisk I had used that chmod command on, but I thought maybe I did something else wrong. Your opinion confirms my suspicion that it is not as secure as I thought. I'm still playing around and experimenting with it and reading more, but I got called away for a while.

I didn't try installing any special ntfs software. I have read that software for writing to ntfs from Linux is getting very good now, but I have no need for it except for experimental purposes.
Right now I'm really interested in learning all about Linux file permissions and I think I will be spending some time studying up on  those. 
Thank you for correcting me, I do appreciate it.
Regards, Herman  :D

---

