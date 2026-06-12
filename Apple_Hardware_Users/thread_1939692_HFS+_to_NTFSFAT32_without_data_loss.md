---
title: "HFS+ to NTFS/FAT32 without data loss"
date: 2012-03-12
forum: Apple Hardware Users
---

### Post by DreamcasterTM on 2012-03-12
Hi guys.
I want to convert the FS of an exteral USB HD from HFS+ to either NTFS or FAT32 (although I would avoid the latter).
I would be happy to choose the ext3/ext4 FS, but I do sometimes plug in the HD into a Windows PC...  

Gparted does not seem to handle HFS+ partition, even if it recognizes it.

Would the 'Edit Partition' command in Ubuntu Disk Utilities do the trick?

I really don't want to lose the data on that HD.

Cheers,

Dreamcaster

P.S.
HFS+ writing permission on Ubuntu would also solve my problems, but I don't want to mess with things I barely know. I have already added NTFS writing capabilities to my Ubuntu installation, though...

---

### Post by coffeecat on 2012-03-12
> **DreamcasterTM said:**
> Gparted does not seem to handle HFS+ partition, even if it recognizes it.

You have to install the package hfsprogs before Gparted can create a hfs+ filesystem, possibly the package hfsutils as well. However, I don't think this is what you need, because...

> **DreamcasterTM said:**
> I want to convert the FS of an exteral USB HD from HFS+ to either NTFS or FAT32 (although I would avoid the latter).

If you want to convert a partition from hfs+ format to ntfs, you simply do it by reformatting it, but this **will** cause data loss. You cannot "convert" one filesystem of one family into another without data loss. The only exceptions are conversions within one family of filesystems such as ext2 to ext3, or ext3 to ext4. Gparted should be able to reformat your hfs+ partition to ntfs without any difficulty. If you want to do this you would need to copy your data to another physical medium, reformat the partition and then copy the data back again.

> **DreamcasterTM said:**
> HFS+ writing permission on Ubuntu would also solve my problems

Ubuntu can write to the non-journalled version of HFS+ out-of-the-box. No need to install anything. If you want to do this, you would need to remove the filesystem journal using MacOS. You would still run into (solvable) permissions problems though because your UID in MacOS would probably be different from in Ubuntu, and you would have a non-journalled filesystem which is less robust than a journalled one. It is possible to force mount a journalled HFS+ filesystem from Ubuntu read-write, but this is not something I personally would rely on.

> **DreamcasterTM said:**
> I have already added NTFS writing capabilities to my Ubuntu installation, though...

I don't understand what you mean by this. Ubuntu has had NTFS write capability out of the box using the ntfs-3g driver for years now.

---

### Post by DreamcasterTM on 2012-03-12
> **coffeecat said:**
> I don't understand what you mean by this. Ubuntu has had NTFS write capability out of the box using the ntfs-3g driver for years now.

Yes, sorry...my bad.
It was something that happened after installing ntfsprogs, a gpart addon.
That had somehow messed my NTFS writing permissions and I had to uninstall/install a few packages before being able to write on NTFS disks again.

About your answer: thank you so much for explaining all those things to me.
I am still a newbie and I do realize that sometimes I just speak out of inexperience.

One more question: force mounting a HFS+ Journaled FS is the only method you can write-access it on Ubuntu? Is there nothing out there that allows you to 'normally' write on such FS?

Tata ):P

---

### Post by coffeecat on 2012-03-12
> **DreamcasterTM said:**
> It was something that happened after installing ntfsprogs, a gpart addon.
That had somehow messed my NTFS writing permissions and I had to uninstall/install a few packages before being able to write on NTFS disks again.

Just as a FYI, and for anyone else coming across this, I guess you're using 11.10 Oneiric (or 12.04). With the version of ntfs-3g that came with earlier versions of Ubuntu, you needed to install ntfsprogs for the various functionalities that comes with that package. This is no longer necessary in Oneiric, since ntfs-3g now includes those various utilities. Indeed, ntfsprogs now conflicts with ntfs-3g and when you installed ntfsprogs, the package manager would have told you that ntfs-3g was going to be removed. Don't worry - you're not the only one who has missed that. Without the ntfs-3g read-write driver the system falls back to the older kernel read-only ntfs driver. Which is why you had to re-install ntfs-3g to get back your ntfs write capability. 

> **DreamcasterTM said:**
> One more question: force mounting a HFS+ Journaled FS is the only method you can write-access it on Ubuntu? Is there nothing out there that allows you to 'normally' write on such FS?


Force mounting a journalled HFS+ filesystem is only something I have read about (if you search you will find threads here about this). It's not something I would like to try myself. The fact that you have to execute a force option at all suggests that it is not 100% reliable. And no, short of disabling the journal on your HFS+ filesystem, I know of no other way of writing to hfs+, at least reliably. The problem is that you are asking Ubuntu to deal with a non-native proprietary filesystem for which the Linux devs have had to reverse-engineer (I guess) a driver.

You are not alone! :) I use Ubuntu >90% of the time, but I have an old-ish Mac Mini running Snow Leopard and I occasionally have to use Windows. Choosing filesystems for external storage media which satisfy all three OSs is difficult. My solution is to have multiple backups on several different filesystems.

---

### Post by DreamcasterTM on 2012-03-24
**coffecat**,
I am following your piece of advice and I am not at step 2, after disabling journaling on MacOS.[INDENT]Btw, I believe that is something OSX does by *forcing* somehow, since you either need to do it by this CL code in terminal:
```
yourcomputer:~ youruser$ sudo diskutil disableJournal force /dev/disk*N*s*N*
Password: 
Journaling has been disabled for volume *VOLUMENAME* on disk*N*s*N*
```or by pressing the ALT key in the menu with DiskUtilities.
Read [here]("http://castyour.net/disable-hfs-journaling-leopard-use-disks-readwrite-linux") for more information.
[/INDENT]After disabling journaling on that HD and I am now running into sharing problems.
How can I solve that?
I have found [this]("http://ubuntuforums.org/showthread.php?t=1586723") thread. Do you think it will help me?

Thank you

---

### Post by coffeecat on 2012-03-24
I'll answer briefly, as I'll have to log off soon and won't be back for some hours.

Don't confuse the force option in the MacOS terminal for removing the filesystem journal from the force option that I mentioned earlier for mounting an HFS+ journalled filesystem in Ubuntu.

You mention sharing problems now which I don't recall was part of the problem at the beginning of the thread. Sharing implies sharing over a network. Is this what you are doing? If so, and if your hfs+ external drive is connected to a Mac, then there probably would have been no need to disable the journal.

Perhaps if you describe your setup in detail and what is going wrong, we could take it from there.

---

### Post by DreamcasterTM on 2012-03-24
> Don't confuse the force option in the MacOS terminal for removing the  filesystem journal from the force option that I mentioned earlier for  mounting an HFS+ journalled filesystem in Ubuntu.Roger that. I thought 'forcing' meant more or less the same thing on both OSes, since also MAC OSX is based on Linux. My apologies.

I am not trying to share the HFS+ external drive over a network. I just need to be able to read/write into it from my Ubuntu 11.10 netbook.

After disabling journaling on Mac OSX I now get this message when I try to copy a file on that HD in Ubuntu:
[I]Error while copying "filename.ext".
Error opening file '/media/Verbatim 500GB/filename.ext': Permission denied[/I]

or this when I try to copy a whole folder:
[I]Error while copying.
The folder "FOLDER NAME" cannot be copied because you do not have permissions to create it in the destination.[/I]

I believe this is about permissions, then.
And you had already mentioned this could be happening after disabling journaling:
> You would still run into (solvable) permissions problems though because  your UID in MacOS would probably be different from in Ubuntu

---

### Post by coffeecat on 2012-03-25
> **DreamcasterTM said:**
> 
After disabling journaling on Mac OSX I now get this message when I try to copy a file on that HD in Ubuntu:
[I]Error while copying "filename.ext".
Error opening file '/media/Verbatim 500GB/filename.ext': Permission denied[/I]

or this when I try to copy a whole folder:
[I]Error while copying.
The folder "FOLDER NAME" cannot be copied because you do not have permissions to create it in the destination.[/I]

I believe this is about permissions, then.
And you had already mentioned this could be happening after disabling journaling:

Sorry I haven't got back earlier - very long day yesterday and my brain wasn't up to much by the end of it! :)

Co-incidentally, I'm trying to help someone with a similar HFS+ in Ubuntu permissions problem in another thread as well. Different underlying issue, but same permissions problems rearing their ugly head and the reason seems to be that occasionally MacOS (presumably when in a bad mood) creates files with 700 permissions.

Let's just recap. You have a non-journalled HFS+ USB drive which you use to swap personal data files between Ubuntu and MacOS? Have I got that right? I do exactly the same and I have come across irritating permissions issues as well. The good news is that they are solvable. Here's my quick and dirty solution and then some suggestions for fine-tuning.

I'm assuming that the partition label for your HFS+ partition is "Verbatim 500GB" because it would appear to be mounted on "/media/Verbatim 500GB". The instructions below use that mountpoint, so you need to adjust that if the mountpoint is different. One minor complication - you have a space in your partition label which is always an inconvenience. We need to escape that with a backslash in the terminal commands.

First - plug the HFS+ drive into Ubuntu and let it be automounted. I'm suggesting here that you change ownership of all your files to your Ubuntu UID. In my experience that seems to work a bit better:

```
sudo chown -R yourusername: /media/Verbatim\ 500GB/
```

Substitute your Ubuntu login name for "yourusername" and don't forget the trailing colon. The next command is slightly contentious but I'll give my reasoning. Change the permissions on all files to the most liberal possible, with:

```
sudo chmod -R 777 /media/Verbatim\ 500GB/
```

The disadvantage of 777 is that all your files will become executable. However, you need the executable bit set on all the folders otherwise they won't be accessible in MacOS if you have chowned to your Ubuntu account (or vice versa). The fine tuning that I mentioned would then be to chmod all the files in each folder and sub-folder to 666, but you would have to do that folder by folder. Post back if you need any help of clarification about that.

---

