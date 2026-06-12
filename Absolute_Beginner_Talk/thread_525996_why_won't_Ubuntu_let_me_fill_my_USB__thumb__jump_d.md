---
title: "why won't Ubuntu let me fill my USB / thumb / jump disk?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by ChrisC on 2007-08-15
Aaaaaaargh .....

I have a 512 MB SD card and a flash reader.  If I take a brand new card, I can throw lots of files on it.  But I can't figure out how to delete those files and then fill it with other files.  It Just Won't Work.  I tried deleting and ejecting multiple times, and it always happily reports free space available but won't let me add anything,  I even tried formatting (System -> Admin -> Disks -> /dev/sdb ) and that went poorly.

Please heeeeeeeelp meeeeeeee ....

---

### Post by ChrisC on 2007-08-15
FYI, here's what df says:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1               495048    158288    336760  32% /media/usbdisk

So it's not like I'm even close to full.

---

### Post by Ripfox on 2007-08-15
Open the window, go to view and check "Show hidden files" then delete the .trash file. They go there first before permenant deletion.

---

### Post by some_random_noob on 2007-08-15
> **ripfox said:**
> Open the window, go to view and check "Show hidden files" then delete the .trash file. They go there first before permenant deletion.
True. I had this problem once before. I wondered what the hell was happening, so I tried opening the flashdrive on a Windows XP machine and it showed me a ".trash" file. Then I discovered that the files starting with "." were hidden in Linux. Opps!

Problem solved I guess?

---

### Post by Ripfox on 2007-08-15
Yes, how shall I obtain my 25 bucks? :neutral:

---

### Post by Ripfox on 2007-08-15
Yep, I knew this guy was phishin' with that 25 dollar garbage. For the future, no one expects to be offered or paid real money for answers here. I thought I would ask you where it was to test my theory that you would not respond, and I was right. Just ask, no need for bribery. :popcorn:

---

### Post by ChrisC on 2007-08-15
I've paid out before.  I'm also sending a check tonight to a Debian developer who maintains a package particularly important to me.  Be a little more patient next time before jumping to conclusions.  Some people in this world are honorable.

Thanks for the hidden file tip.  I meant to mention that in my original post.  You can show hidden files at the command lines with "ls -al", and there are none.

Meaning I still have the problem :( ...

---

### Post by Ripfox on 2007-08-15
Like I said, I wouldn't even accept the money, because this is a community support forum, and it's not how it works. I think you do it to try to get faster answers, and I doubt it will work on this forum.

---

### Post by ChrisC on 2007-08-15
Actually I do it just to get ANY answers.  You can check my posting history for the carefully written threads I've posted that have gone nowhere.  Yes, of course I search before posting.

My time is very valuable to me, and having to constantly come back and bump threads and beg and plead for answers is a collosal time sink.  Ideally I'd pay for a proper support package, just for my 5 stupid problems per year, but I can't find anything other than Ubuntu's $250/year commercial option.  Haven't investigated lately though, and I would be happy to hear of new options on that front.

As Jamie Zawinski said, Linux is free only if your time is worthless :)  I'm willing to pay to make it a bit less of a time vortex.

Anyway, USB drive problem remains.  Is there an official Ubuntu way to blank out a USB drive? (SD card in my case)

---

### Post by Hobo Joe on 2007-08-15
> **ChrisC said:**
> 
As Jamie Zawinski said, Linux is free only if your time is worthless :)  I'm willing to pay to make it a bit less of a time vortex.

Anyway, USB drive problem remains.  Is there an official Ubuntu way to blank out a USB drive? (SD card in my case)

How rude!


To answer your question, try deleting all the files, and then unmounting it right after, in my experience removable media doesn't delete files until you try to disconnect them.

---

### Post by Ripfox on 2007-08-16
> **ChrisC said:**
> Actually I do it just to get ANY answers.

Well there it is I guess.
Like I said I doubt it will incease the amount of help you get, just be more patient. :)

---

### Post by tgalati4 on 2007-08-17
I had a similar problem with Sony Memory sticks.  I think it has something to do with the file protection (Digital Rights Management).  You can delete the files but the FAT thinks the space is still in use.

My cheesy solution was to stick it in a Sony camera and reformat inside the camera.  It worked!

For your SD cards, try finding a device that will format them and you may have some luck.

---

### Post by blinktude on 2007-08-17
have you tried emptying the trash can when the SD card is in your computer?

---

### Post by ChrisC on 2007-08-25
> **blinktude said:**
> have you tried emptying the trash can when the SD card is in your computer?

Thanks blinktude, but that doesn't work either.

I've tried deleting everything, emptying the Trash, looking for hidden files, and reformatting the card using System -> Admin -> Disks.  Every time I get the exact same result:  it says that it has 500 MB free, but when I try to copy 154 MB of data to it, it fills up just before the last of the files makes it in.  At that point it says it has about 350 MB free, but refuses to accept another file.  None of the files are larger than 3.4 MB and most are around 1 MB.

Just now I even tried manually deleting the partition and reformatting it, using fdisk and mkfs.vfat, and while those steps seemed to work fine, the file copy failed exactly as above.  It's as if the FAT table is sucking up huge blocks for each file, but that would only cause a problem if I was copying in many many tiny files, which I am not.  It's only ~220 files.

I don't have a camera for this type of card so I can't stick in there and delete / reformat there.  In fact that's what I do for my Memory Stick cards, in my Sony camera, because Ubuntu similarly misbehaves on those.

This actually involves some photos of deeply personal value to my family so it's real punch in the gut that I can't get this to work.

At this point my only recourse seems to be to use new, blank cards.  How ridiculous is that?  Sigh.

Or go buy a USB card reader and stick it into a Windows computer and fix this there.  Quite the failure of Ubuntu then, no?

Notwithstanding the haters posting earlier in this thread, I will still happily pay if you happen to help me solve this.  Thanks.

---

### Post by vpjr on 2007-08-25
Dear chrisC,


ven

---

### Post by vpjr on 2007-08-25
dear ChrisC

Please post the result of a "mount"

regards,

ven

---

### Post by asmoore82 on 2007-08-25
> **ChrisC said:**
> Or go buy a USB card reader and stick it into a Windows computer and fix this there.  Quite the failure of Ubuntu then, no?

If DRM(Digital Restrictions Management) is involved, this would be a failure of Humanity at large.

I would try blanking the card before partitioning/formatting it ...
```
~ $ dd if=/dev/zero of=/dev/sdb
```
assuming it is still 'sdb' after [re]pluging it.

---

### Post by christhemonkey on 2007-08-25
This happened with my little brothers ipod nano (essentially just a USB stick), i never could get it to free up the space that was taken up with apparently nothing.

Had to resort to windows im afraid. :(


Try checking the disk for errors with fsck?
```
fsck.vfat -a /dev/sdWhatever 
```

---

### Post by asmoore82 on 2007-08-25
Also, must ask just incase ...

how old is this flash chip?

---

### Post by ChrisC on 2007-08-26
> **asmoore82 said:**
> If DRM(Digital Restrictions Management) is involved, this would be a failure of Humanity at large.

Agreed!

> **asmoore82 said:**
> 
I would try blanking the card before partitioning/formatting it ...
```
~ $ dd if=/dev/zero of=/dev/sdb
```


Ahhh, good tip asmoore82, and while testing it out I got my hopes up about this working and me sending off my check :)  Alas, it didn't work, exact same thing as before.  Here's exactly what I did:

```

sudo fdisk /dev/sdb    (to delete the existing partition)
sudo dd if=/dev/zero of=/dev/sdb  (to blank out the drive, took 6 minutes with this 512 MB flash drive)
sudo fdisk /dev/sdb    (to recreate the partition, used type 0x6 which is FAT16)
sudo mkfs.vfat -F 16 -n usbdisk /dev/sdb1   (to format that new partition, 16-bit FAT)

```

and then I tried to copy the files in again, and it failed exactly the same way as always.  Am I setting the partition type and then formatting the partition consistent with that declared type?

To answer the other questions:
 - SD card is about 6 months old
 - mount always works, been letting Ubuntu automount, I don't know the mount command syntax
 - fsck.vfat results are:

```

$ sudo fsck.vfat -a /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 220 files, 19773/61878 clusters

```


WEIRD.  I give up, I'm buying a card reader tomorrow and fixing this in Windows.  I hope ...

Thanks guys for your help!  Anything further is still appreciated.

---

### Post by ChrisC on 2007-08-26
Bought the card reader, plugged it into Windows laptop, inserted SD card, formatted it, took card over to Linux machine, all files copied over fine.

It's a damn shame.  $25 went to big box electronics retailer instead of one of you Ubuntu guys.

---

### Post by arvevans on 2007-08-27
I just spent this afternoon using a 1 GB flash drive to transfer lots of files from an older computer to a new one.  My file clearing procedure was as follows:
[LIST=1]
[*]Insert USB Flash drive
[*]Click on it's icon when it comes up on Desktop.  This opens the file viewer.
[*]If there are any files there goto EDIT/Select All and then to EDIT/Move to trash
[*]close the file viewer window
[*]Right-click on the flash drive icon and select EJECT, wait until it says you can remove the drive
[/LIST]

That worked for me.  Hope it works for you.

---

### Post by ChrisC on 2007-08-28
Thanks, several people suggested that.  Yes, that would be the expected behavior.  No, that didn't work for me.

What a curious sig ...

---

### Post by FuturePilot on 2007-08-28
I wonder if formating with GParted would have worked....

---

### Post by dwhitney67 on 2007-08-28
> **ChrisC said:**
> Thanks, several people suggested that.  Yes, that would be the expected behavior.  No, that didn't work for me.

What a curious sig ...

have you tried to remove the files on the SD memory wafer using the old fashioned way... in other words the command line.

Insert your SD wafer.  Determine where it is mounted.  I have an SD wafer from my DigiCamera.  It gets mounted at /media/disk.  Let's see... to delete a file:

[FONT="Courier New"][INDENT]$ cd /media/disk
$ cd DCIM/100KZ650
$ rm -f 100_0276.JPG
$ cd ../../..[/INDENT][/FONT]

The trailing change-directory command is done so that the device can be unmounted (otherwise the system will complain the device is 'busy').

Then unmount volume either using Gnome interface or

[FONT="Courier New"][INDENT]$ sudo umount /media/disk[/INDENT][/FONT]

Re-insert SD wafer to verify file is gone and indeed it is.

---

### Post by Jetjoint on 2007-10-16
This is a bit of a crazy work around .......... I have the same problem........but it works for me.

After inserting the card or usb stick I start gparted. I select that drive from the pulldown menu top right.
I then right click on the entry for that drive in the main window and select unmount.

I then go up to the Gparted menu top left and select refresh devices.

Magically the missing space reappears .....

To use the drive just remount it by selecting it from the Computer menu........


Hope this helps

:mrgreen:

---

### Post by scaine on 2007-10-16
I've had this problem with my 2Gb mini-SD card since I got it.  I have to do all my file copying using an old Windows XP laptop which has an SD slot on it.

In fact, I can't even copy files to my SD cards in Ubuntu - that's never worked for me.

When I tried the Gparted method above, I get :

======================
libparted : 1.7.1
======================
Unable to open /dev/sdf read-write (Read-only file system).  /dev/sdf has been opened read-only.

I therefore don't have the option to umount it.  I can umount it with sudo, unplug it, plug it in again and read the files on it just fine - but I can't write to it.

sudo chmod 777 /media/DATA/
chmod: changing permissions of `/media/DATA/': Read-only file system

It's pretty infuriating.  I haven't checked launchpad yet - anyone else come across this?

---

