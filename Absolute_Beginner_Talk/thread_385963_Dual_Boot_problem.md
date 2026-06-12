---
title: "Dual Boot problem"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Quilpole on 2007-03-16
As a Linux absolute beginner I have run the live cd with fair success and after due consideration and one or two false starts I have installed Ubuntu.
I have two internal hard disks and two external. All were NFTS format.
I backed up the contents of the slave internal disk to one of the externals and started the install of Ubuntu let it format the slave and gave it a chunk of the slave to install on.
Everything went fine. Restarted and up came grub with a choice of operating systems. I ran Ubuntu and and did the updates etc. Ubuntu works fine but when I try to start Windows I get the Windows splash screen for a few seconds and it crashes. When I try again I get the normal "Windows has recovered from a serious error" message and the choice of safe start etc. Whichever I try it still crashes.
I realise I can probably (I hope) get Windows back back by restoring the MBR from the installation cd. This would lose me Ubuntu.
Can anyone explain what is happening and how I can install Ubuntu without it happening again?

---

### Post by buuntuu! on 2007-03-16
hi there!
i am not sure, but maybe it's the fact that you installed on the second HD that messed things up for you...
i stumbled upon a [thread]("http://www.ubuntuforums.org/showthread.php?t=368909&highlight=dual+boot+seperate+hd") of someone who had a similar problem. follow the links of posts #6 and #8, they might be helpful in your situation.

why don't you just install both xp and ubuntu on the master and keep the slave for files? would probably make things easier...

---

### Post by Quilpole on 2007-03-16
I did consider putting Ubuntu on the primary drive, but since I have only recently had to reload windows and all the software I did not feel like messing with it - just in case.
Besides it is partitioned with a recovery partition as well as a couple of others and I did not want to mess with that. I thought that giving Ubuntu a whole disk to play with would be OK and as far as I can gather it is fine to put it on a different disk. In fact it works very well - I am using it now. I just can't get Windows to run.
I will follow up your suggested thread and see if it helps.

Many thanks.

---

### Post by buuntuu! on 2007-03-16
if it doesn't work out for you on hdb:
after intensive search on various forums and wikis i wiped my rescue-partition after burning the recovery cds, it's safe to do so.
ubuntu runs fine on logical partitions too, so if you've made an extended partition you could create some room there...

---

### Post by Bigbluecat on 2007-03-16
I don't think it is a problem with having Ubuntu on the second disk. That is how I have my dual boot set up. 

Grub seems to be working and successfully pointing to the windows boot loader. You would not get the splash screen if this phase had not been successful. 

Once in this phase it is purely a windows problem as grub has done it's job and plays no further part so it sounds like something has become lost or corrupted with your windows install.

Open a terminal and enter sudo fdisk -l. Post the results back here so we can have a look at your disks and partitions.

This may or may not help but let's see.

---

### Post by Quilpole on 2007-03-16
I hope that this makes sense to somebody - it don't mean a lot to me.

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24321   195358401   44  Unknown

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               2        3643    29254365    7  HPFS/NTFS
/dev/hdd2   *        3644       18890   122471527+  83  Linux
/dev/hdd3           18891       19457     4554427+   5  Extended
/dev/hdd5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       30401   244196001    7  HPFS/NTFS
andrew@andrew-desktop:~$

Any help appreciated.

Andrew.

---

### Post by rusty4r on 2007-03-16
I agree with BigBlueCat, which partition or drive contains the windows op system that your trying to boot

---

### Post by Bigbluecat on 2007-03-17
I had an odd problem with windows a week ago where it would not boot. Did not get to the splash screen but was not a grub problem. This was after a BSOC epsiode though.

In my case Testdisk did not show any partition problems.

I ran the Windows recovery disk and it could not see the C: drive. In the end it seemed that for some reason it had re-named by C:, D: and E: partitions as D: E: and F: and the C: drive was no my external back up drive.

The solution was to turn off my external drive and then everything magically sprang back.

I noticed that you have on or two external drives. It may sound weird but turn them off and try booting.

---

### Post by Quilpole on 2007-03-17
I tried disconnecting the externals as soon as things went wrong. It made no difference.
As far as I know the primary drive is in an "as bought" state. I have not changed the partitions.

Regards,

Andrew.

---

### Post by Bigbluecat on 2007-03-17
OK.

Let's look at the output from your fdisk command and see if it matches what you think your drives should be.

/dev/hda is your primary hard drive. It's 200G but for some reason the file system is unknown. That's not a good sign. I would have expected NTFS. It also does not seem to be partitioned.

/dev/hdd is presumably your second internal drive. 160G. Has both NTFS and Linux partitions. 

/dev/sde must be one of your external drives. 320G. Not partitioned. NTFS file system.

/dev/sdf is the second external drive. 250G. NTFS and no partitioning.

Is this what you would expect? I'm a little concerned that the file system on hda is not recognised.

---

### Post by Quilpole on 2007-03-17
hda is the primary drive and it has C: D: E: partitions - or it had.

Partition editor shows it as one extended NFTS partition. D: & E: are logical partitions.

Andrew.

---

### Post by Bigbluecat on 2007-03-17
At this point I would be tempted to use the Windows recovery disk. Boot from it and hit r to get to the recovery console. It should give you an option to try to repair the install.

BE AWARE: This approach will re-write the MBR and you will lose the ability to boot to Linux. We can restore grub easily from the LiveCD.

There are no guarantees with this. I had to take this approach last time and it worked.

---

### Post by Cannonade on 2007-03-17
I've been reading through this and I'm a little confused as to where abouts Windows is supposed to be.

I am guessing that your arrangement is Windows on hda with the unknown file system (that is rather scary!:? ) and that on hdd, you have a separate NTFS partition and the other partitions are for Linux. Then you have two internal drives. - Please correct if this is totally wrong!;) 

I have a similar set up to this. hda with Windows, hdb split into NTFS and Linux partitions, and then one external drive. I wouldn't think the external drives would cause a problem because they don't affect the boot order, they are automatically shoved to the bottom of the list and they will change drive letter because they are not permenant, but they should not affect the drive letters of your internal drives.

I would also like to know where you installed grub to. Was it installed on the MBR of hda or hdd? If it's on hda, you could try repaired the MBR of Windows and then using the LiveCD or Super Grub Disc to repair grub and install it to the Linux partition. If it's on hdd, then well...! I dunno what to suggest.

---

### Post by Bigbluecat on 2007-03-17
Cannonade

I don't think it is a grub or MBR problem because he sees the windows splash screen so the system gets beyond the initial grub or MBR boot loader stage. It fails at the later windows stages which makes me think it is an issue with the hda drive or file system.


If this is so then restoring the MBR may not fix the issue. 

However i tis possible the running three commands from the recovery console may work:

fixmbr
fixboot
bootcfg /rebuild

This may revive the system for windows. However, if there are corrupted boot files on the windows drive then we may be left with no operational system.

Either way we will be using the windows recovery disk to get things back and then having to re-install grub to bring back Ubuntu.

---

### Post by Quilpole on 2007-03-17
Guys,

Remember I am an Absolute Beginner with Linux.

I have two internal drives. The OEM and the second I installed for data storage - eggs and baskets! The externals are for backup and storage of picture files. 

Where grub was placed, I have no idea. I cleared the data off my second drive, onto the external drive,  so as to give Linux plenty of room to play in. Did the install from the live cd. Where it put grub was up to it. 

It all went very smoothly - as far as I could tell.

---

### Post by Bigbluecat on 2007-03-17
Sorry. 

Well the default for grub install is the MBR (master boot record) of the first hard drive (your windows drive /dev/hda).

Your bios will point the system here. The first part of grub residing here is essentially a pointer.

This will point to your second drive with linux installed. On this drive you will have a folder /boot/grub.

In this folder is a file called menu.lst. Have a look at it. This contains details and series of sections which tells the system where to look for OS kernels to boot (including windows - look right down at the bottom of the menu.lst file)

Have a look at Herman's page. Very useful for dual boot and grub issues.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I also recommend keeping a copy of SuperGrubDisk around. Just in case:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

However, my belief is that this is all academic but useful to know. What you have is a windows problem and not a linux problem. Since you see the windows splash screen you are way beyond the grub bootloader and it has successfully done it's job of pointing the system at where to look.

OK.

Now in windows it will look for NTLDR and NTDETECT.COM and boot.ini. These are the windows boot files. Unfortunately I don't know them nearly as well as grub. NTLDR (NT Loader believe) must do something similar to the menu.lst in that it should point to an executable windows kernel. Now. since you get a splash screen this seems to be OK. But somewhere in the windows boot process it gets messed up.

Since this is a windows problem we need your windows disk to solve it. When you boot from this it gives you an option of entering the recovery console. The unfortunate thing with windows is that it believes it should be the only OS on a system. So using windows recovery will remove the grub boot loader and restore windows only (with some luck). 



So - first a simple question - do you have your windows install disk.

Have a look at this for some background information.

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

Once you are in the windows recovery console it will ask what version of windows you wish to recover. Hopefully you will see C:\WINDOWS. If you don't and you see D:\WINDOWS or some other drive letter we may have a problem with the windows partition tables or just the external drives (turn them off first to be sure).  If this happens stop and get back on line. We will need to try to recover your partitions (tricky)

Once you are in C:\WINDOWS you are in a kind of DOS shell. There are three commands to enter.

fixmbr   - this removes grub and restores the windows bootloader
fixboot
bootcfg /rebuild

once you have entered these you can quit and try restarting the system. Grub will be gone so you will not be able to boot to linux until we restore it.

If this does not work we may have to go back to the windows recovery console. There is an option to let it try to repair the system.

Make sure you still have your Ubunutu LiveCD around. We will need it to recover the system if this does not work.

---

### Post by Quilpole on 2007-03-17
Bigbluecat,

Many thanks for the comprehensive reply. I have been computing for some time and never really got to grips with CPM never mind DOS.

I recently had to reinstall Windows and have all the necessary disks. It was the Windows problems that made me finally take the plunge into Linux, especially since it now seems more user friendly. Unfortunately I do need Windows as well, so it is not possible to migrate completely to Linux. Though it seems that, inadvertently I have!

Visitors coming so I cannot follow through your suggestions until Sunday.

Regards,

Andrew.

---

### Post by Bigbluecat on 2007-03-17
I'll keep an eye on the thread. When you get a chance to try windows recovery post back. I've had to use this twice in the last 6 months. Get a little nervous each time. But I'm pretty solid at restoring grub and getting linux back.

---

### Post by Quilpole on 2007-03-18
Oh bother!

Went into recovery console.  J:\WINDOWS

I imagine it starts then looks for stuff on the missing C: drive can't find it and gives up.

---

### Post by Cannonade on 2007-03-18
Just a suggestion, but have you tried to see if you can repair the Windows regestry? Maybe it got corrupted somehow, because the Windows regestry is the most easy thing in the whole world to corrupt! This Windows repair facility will detect the system file and install it in the correct place.

Of course, I certainly agree that removing Windows completely will solve all the problems! But when things go right, Windows and Linux coexist quite happily.

---

### Post by Quilpole on 2007-03-18
First. The grub menu finishes with:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I have not tried the Windows repair route - as yet.

Something occured to me in the wee small hours. I have Norton GoBack installed - it has got me out of the Windows mire a couple of times. Could this be causing a problem?

---

### Post by Quilpole on 2007-03-18
First. The last item in the Grub menu.lst is:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I have not gone as far as trying Windows recovery - as yet.

It came to me in the wee small hours that I have Norton GoBack installed - it has got me out of the Windows mire a couple of times. Could this be causing the problem?

---

### Post by Bigbluecat on 2007-03-18
OK.

As Cannonade suggests the windows registry is where it stores the drive names. 

You could try GoBack to recover things. See if it works.

Or try the repair facility. This is how I recovered last time

EDIT: Switch off or remove your external drives first. This was confusing my system last time.

---

### Post by Quilpole on 2007-03-18
GoBack does not kick in at start up, as it did with a pure Windows system. I just get grub and a choice of OS.

External drives are off - plugged into my laptop, so that I can still function. I am a bit limited because the laptop does not have all the software that the desktop has.

In device manager the primary drive is there but it does  not show any details. The secondary drive has details of the partitions etc.

I will have a stab at the repair facility, when I feel up to it.

I did download Supergrub and have - tentatively - played with it. I tried to start Windows and got the same result - started and then crashed. I do not feel knowledgeable enough to attempt some of the more advanced features. Advice would be gratefully received.

---

### Post by Cannonade on 2007-03-18
There is also a utility called Ultimate Boot CD which can be got from here:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
It allows you to do different stuff, but I would be careful with what you play around with because some of it is CMOS and BIOS related.

But if it's not a boot problem, then this wont really help. But there are some disc utilities on there that may or may not give a clue as to where your file system has got to.

---

### Post by Bigbluecat on 2007-03-19
Unfortunately it does look like either your windows registry or partition table is corrupted so SuperGrubDisk will most likely not help here.

My only suggestion here is the windows repair facility.

---

### Post by Cannonade on 2007-03-19
If the partition table is corrupt, you could have a look at this site:

[http://www.ptdd.com/fixboot.htm](http://www.ptdd.com/fixboot.htm)

But if it's more than that, then yes, the only option is to run Windows recovery.

---

### Post by Quilpole on 2007-03-19
Hi,

In recovery console, when I map the drives I get J: as being where Windows is installed and J: is on the primary hard drive. C: is on the secondary drive and is followed by K: and L:. These are the Linux partitions. I tried the boot fix command and just lost Linux, but Windows goes a bit further before falling over because it cannot find a file.

At the moment I am ploughing through the available commands and Microsoft's knowledgebase (?) to try and find a simple way of changing the letters around.

---

### Post by Quilpole on 2007-03-19
Progress at last.
Norton GoBack came up trumps and sorted the drive letters out - after a lot of thought.

I now have C: D: E: on the primary disc all NFTS and a small NFTS on the F: drive - the secondary. Windows - of course - thinks that the rest of the disc does not exist, since it has Ubuntu on it.

Next question is - how do I get a dual boot operating without this happening again?

---

### Post by Bigbluecat on 2007-03-19
Excellent progress.

Now we need to restore grub. For this you need your liveCD or Super Grub Disk.

Let's assume the liveCD. Pop it in and boot from it.

Once inside open a terminal.

Then type:

```
sudo grub
```This will bring up the grub command line.

Next we are going to find the location of your linux boot files (as grub names them). So enter:

```
find /boot/grub/stage1
```The will return a location such is (hdx,x).  In your case I might expect (hd1,1). This names the disk and partition in grub terms. Grub always starts counting from 0. So (hd1,1) is the second drive, second partition.

Now you will use the location returned in the next set up:

Enter:

```
root (hdx,x)
``` where you have replaced x,x with the location returned from the find command.

Now we are going to write grub back to the MBR.

Enter

```
setup (hd0)
```This writes grub to the MBR of the first hard drive. This is where the bios points. 

Lastly we will quit from grub.

```
quit
```Now we should have grub and your mutli boot menu back.

A word of caution. I have heard stories that Norton GoBack does not play well with grub.  I used to have GoBack and did not have a problem but who knows.

Shutdown from the liveCD and reboot normally. With luck you are up and running with a dual boot system.

Try booting linux. then try Windows. If there are issues here we may need to make adjustments to you menu.lst but we can tackle that when we get to it.

---

### Post by Quilpole on 2007-03-19
Many thanks Bigblue.
I was so relieved to get things back to what passes for normal in Windows, that I have had a couple of drinks to celebrate.
I will try your suggestions in the cold (sober) bright day of Tuesday, which happens to be my birthday and if it all works it will be the best present I will get. 

Regards,

Andrew.

---

### Post by Bigbluecat on 2007-03-19
Happy Birthday for tomorrow.:)

---

### Post by Quilpole on 2007-03-21
Oh Well!
I had a nice birthday. But ...
Back to square one. I will restore things with GoBack but I am rather concerned in case things go pear shaped again and I do not have GoBack installed. The Norton recovery disc should work without GoBack - shouldn't it?

---

### Post by Bigbluecat on 2007-03-21
I don't really know Norton. My wife does. The recovery disk should be independent of GoBack.

good luck

---

### Post by johnmax on 2007-03-21
I have vista on an SATA drive with a FAT32 partition for data exchange and a second ATA100 drive as a slave off my DVD R/W with Ubuntu loaded on it's own 74G partition with a second formated in NTFS for future growth. I set my BIOS to boot off the second drive and can select either Vista (ugh) or Unbutu without problems. I suspect windows is the problem.

John

---

### Post by belikralj on 2007-03-21
My suggestion is the same as the previous post (not mine but the one above). I had a problem with Partition Magic, grub error 15 or 18 can't remember. But what happened was that Partition Magic tried to start before the OS and messed the whole thing up. To fix this I installed Windows without my second hard drive plugged in (now I see I didn't have to) and then Ubuntu but I installed grub in the MBR of the second hard disk (it too was the only one plugged in the machine at the time) then added that last line you posted (not your one but it's the same for everybody) to my menu.lst file and setup BIOS to boot of the second hard disk. That's the best way in my opinion neither windows has anything on the ubuntu disk nor the other way around, haven't had problems since. I would suggest following all the instructions just installing grub on (hdx) where x is the first x from your grub...stage1 search, and then setting your bios to boot of that disc. But it will most likely work the other way as well.
Anyway welcome to Ubuntu :guitar:

---

### Post by zagor on 2007-03-22
Same issue here on a Dell Inspiron 1501.
I installed Edgy 64 on the PC, where Vista was preinstalled.
Started up with the pci=nomsi boot option to see the disk.
Partitioned during the Ubuntu install leaving untouched the 2 Dell partitions (one FAT16 for Dell boot, one Vista/Dell recovery ntfs) and resizing the main Vista partition.
Ubuntu install went smooth and fast.
Vista was automatically added to grub.
No way to pass the stupid scrolling cursor, though, when trying to boot Vista.

I don't have GoBack or anything similar.

I'm a little confused from all your posts and my simple question is:
Why should a reinstall of grub after a reinstall of microsoft BCD shold work?
My understanding is that the "procedure" is:
[LIST]
[*]start Vista in recovery mode through Vista CD or recovery partition
[*]issue the "Bootrec.exe /FixMbr" command to restore BCD
[*]start (hopefully) Vista and check that everything is fine
[*]boot Ubuntu liveCD and chroot to reinstall grub (or use SuperGrubDisk and boot directly into the installed Edgy to reinstall grub)
[/LIST]

Now grub should start Vista as well.

But why?
How does this differ from the original grub installation?
I guess the answer is that the issue is not grub or BCD, but the resizing of the partition which is not accepted by Vista if not done by itself..... Am I right?

Shall I go on with the above procedure or should I try something different first?

Thanks
F.

---

### Post by rusty4r on 2007-03-22
Yes but you were successful in my opinion because you resized onlly the Vista partition and left the recovery partition alone. If I read that right.
> 2 Dell partitions (one FAT16 for Dell boot, one Vista/Dell recovery ntfs) and resizing the main Vista partition.

I think Quilpole inadvertantly made changes to his recovery partition which could be a little bit of trouble if he ever needs to reinstall windows but I think it can probably be fixed and there's a possibility that it's ok now

---

### Post by Quilpole on 2007-03-22
Johnmax,
You are right - Windows is the problem! That is why I am trying to get things running smoothly - so that when Windows decideds to fall over I can function while putting it back together.

---

### Post by Quilpole on 2007-03-22
Firstly. I deliberately installed Ubuntu on my second hard drive and left the OEM one strictly alone. If your manufacturer suppies you with all the CDs with the software on it is possible to reload everything without the recovery partition - but it is a lot quicker.
The main problem seems to be that something - probably only Bill Gates knows what - changes the drive letters. Windows keeps insisting it is on drive J: Norton sorts it out as long as I FIXMBR from the recovery console. However, Ubuntu is not accessible anymore - no grub.

Now for the interesting bit. I tried SuperGrub and it showed Ubuntu and Windows, in the usual grub style menu.  I cursored down and tried to boot XP. It went a lot further than it had before - beyond the splash screen and even got as far as the mouse pointer. Then it crashed and rebooted. "Oh dear." I said expecting to be back running recovery console. Since it had started SuperGrub again, I thought I would see if it would run Ubuntu and it did.

After closing down I tried a normal restart and it went straight into Windows!

Doh!

---

### Post by Bigbluecat on 2007-03-22
My suggestion now is to keep your windows and Ubuntu isntalls completely separate as you have a dual drive system.

There are some detialed instructions on this forum but here is the jist of it.

Take out your windows master drive (hd0) and install your Ubuntu drive in the master position.

Install Ubuntu into the master drive.

Install your windows drive as a second drive (slave) position.

When you boot it will only be Ubuntu.

Now windows only likes to be the 1st drive master so we need to fool it a bit. To do this we edit menu.lst and a map commands to the windows section.

Now when we retsart you should see grub give you a choice of windows and Ubuntu.

The beauty of this system is that you are not writing grub to the MBR of your windows drive and if you ever want to you can just place the windows drive in the master position and boot as if nothing has happened.

I'll do some searching to see if I can fnd how to thread.

---

### Post by Bigbluecat on 2007-03-22
There is some good info here. Maybe one of these methods is better for your system

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dual+boot)

---

### Post by Quilpole on 2007-03-23
[QUOTE=Bigbluecat;2338055]There is some good info here. Maybe one of these methods is better for your system

The computer system or my nervous system?

I will explore the link that you gave and in the meantime settle for booting via SuperGrub. At least I can now explore Ubuntu and start learning how to do useful things.

My thanks to everyone for their help.

---

### Post by MichaelSM on 2007-03-23
Hi. I'm not too sure if this will help, but I was happy with my outcome. I have an old Celeron 1.7 PC, and it has two HDs installed. One is an 80 gig partitioned with Xandros and Window$ XP, the other a 40 gig with Ubuntu 6.10.
With everything plugged in-and don't ask me about Master/Slave jumpers, because I think they're just as I had them when they worked alone- I just started it all up then hit F8 which got me into a part of BIOS with a window which allowed me to select either IDE 0 or IDE 1 as a first boot option. I must have picked the right one (sorry I can't be more exact as I am a newbie) because now when I power up I get the Xandros multiple choice starter which lists the OS options available. I just use the down arrow to select the OS I want to use. or, since I have tons of stuff on Xandros, that OS starts automatically as default after about 30 seconds.
It's conceivable that I just lucked in. I don't know if the Ubuntu 6.10, my preferred OS, would give a similar choice of OS if I'd selected the other IDE option in BIOS. And NO! I have zero interest in changing something which works. Um, sort of...this can all get a bit anal.
Cheers, Mike.

---

### Post by jake8 on 2007-03-26
> **Quilpole said:**
> ... I will restore things with GoBack but I am rather concerned in case things go pear shaped again and I do not have GoBack installed. The Norton recovery disc should work without GoBack - shouldn't it?

I use Goback currently -  Do any of you know of an GoBack type software that actually works on Vista and multi-boot environments?  I found out from the folks at symantec that GoBack won't be supportting Vista.

I found RollBack Rx ([http://www.horizondatasys.com/169614.ihtml]("http://www.horizondatasys.com/169614.ihtml")) as a good solution, but I am unsure, being a long time user of Goback -  Have any of you had any experience with Vista or RollBack Rx?

Thanks in advance.

---

### Post by pixelpainter on 2007-04-02
I am a bit of a newbie myself with Linux, but it seems the problem you are having is with xp not Linux. I am not familiar with goBack... but as a suggestion, you could try using Acronis Disk Director, you can make an acronis boot disk, and then change the drive letters there to match your needs.
there is a lot of info  in this thread, but as I understood it, your xp partition was changed from c: to J:
Firstly make sure that you have the correct settings for your XP drive and partition in the boot.ini on your xp boot partition. (if this setting is incorrect, you will not be able to boot even if the drive letter is correct) Then  boot into Acronis and change the drive letters to correct ones.
I hope this helps.. I have run into similar problems when shifting around my drives and partitions and Acronis did the trick for me :)

---

