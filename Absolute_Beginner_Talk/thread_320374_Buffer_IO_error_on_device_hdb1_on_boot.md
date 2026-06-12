---
title: "Buffer I/O error on device hdb1 on boot"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2006-12-17
When booting ubuntu, i get lots of 
Buffer I/O error on device hdb1, logical block xxxxxxxxx errors. What is wrong, and how can i fix them? Thanks!

I did a search on it but no one replied the thread.

---

### Post by maxamillion on 2006-12-17
Couple things to check, first off I would recommend running some sort of drive fitness test or S.M.A.R.T. on it to make sure it is not faulty, and from there boot the live cd, make sure the hard drive is mounted and then run fsck on the file hard drive to check the file system.

---

### Post by dannystaple on 2006-12-17
> **nyxynyx said:**
> When booting ubuntu, i get lots of 
Buffer I/O error on device hdb1, logical block xxxxxxxxx errors. What is wrong, and how can i fix them? Thanks!

I did a search on it but no one replied the thread.

It is good you did a search. Can you provide a link to the thread? It is probably reasonable to link the two threads so people in trouble can find the other when searching. 

Now the problem you are having, has it occurred for a long time, just recently, or only when using Ubuntu? It actually sounds like a potential hardware issue, with the hard drive failing. I would strongly recommend that you back up your data (only the stuff in home) to another drive or medium as soon as possible. Can you perform, from a command line "df -h" and post the results here?

```
df -h
```

Following a backup, you will probably want to scan the disk for errors. fsck - "File System ChecK" is a tool that will check a drive for errors, and report them. 

```
fsck /dev/hdv1
```

If you can't boot, you might need to do this from the liveCD, including the backup.

---

### Post by xpod on 2006-12-17
I once used to get a load of similar errors when loading the live cds....it would jump to a black screen with about 8 of those errors which would pop up every minute or so,After about 10 minutes the cd would carry on loading normally...never did completely understand what caused them:

Mines was`nt device hdb the errors were but dev/hdd etc etc although once i replaced the cd drive they stopped completely.:-k 

Hope you figure it out but take precautions just in case like advised...you never know:( 

Good luck

---

### Post by nyxynyx on 2006-12-17
That thread is at [http://ubuntuforums.org/showthread.php?t=303808](http://ubuntuforums.org/showthread.php?t=303808)


result of 'df -h'

Filesystem                Size       Used    Avail    Use%     Mounted on
/dev/hda2                  9.7G       3.2G    6.0G       35%      /
varrun                       506M        72K       506M     1%     /var/run
varlock                       506M        4.0K       506M     1%     /var/lock
udev                           506M       120K       506M     1%    /dev
udevshm                     506M           0       506M     1%    /dev/shm
lrm                           506M       19M       488M    4%    /lib/modules/2.6.15-27-386/volatile
/dev/hda1                   106G       41G         65G        39%     /media/hda1
/dev/sda1                    299G       286G       13G         96%    /media/sda1


when i run fsck /dev/hda1 i get :

fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for dev/hda1

havent tried the live cd

---

### Post by xyz on 2006-12-17
I experienced this = dead HD. Sorry ..and,who knows, it may not be this way in your case.
You could use (SMART as said above) and/or save your important data and run:
[Darik's Boot and Nuke]("http://dban.sourceforge.net/")
It didn't help my drive at the time but it can...I guess if it's not beyond repair.
Good luck and let us know...

---

### Post by dannystaple on 2006-12-17
> **xpod said:**
> I once used to get a load of similar errors when loading the live cds....it would jump to a black screen with about 8 of those errors which would pop up every minute or so,After about 10 minutes the cd would carry on loading normally...never did completely understand what caused them:

Mines was`nt device hdb the errors were but dev/hdd etc etc although once i replaced the cd drive they stopped completely.:-k 

Hope you figure it out but take precautions just in case like advised...you never know:( 

Good luck
Well it would be different. The letters after hd depend on which order the device is identified to the bios, the primary master would be a, primary slave b, and hdd would be the secondary slave. I have had to replace CD drives more often than hard drives.

> **nyxynyx said:**
> That thread is at [http://ubuntuforums.org/showthread.php?t=303808](http://ubuntuforums.org/showthread.php?t=303808)


result of 'df -h'

Filesystem                Size       Used    Avail    Use%     Mounted on
/dev/hda2                  9.7G       3.2G    6.0G       35%      /
varrun                       506M        72K       506M     1%     /var/run
varlock                       506M        4.0K       506M     1%     /var/lock
udev                           506M       120K       506M     1%    /dev
udevshm                     506M           0       506M     1%    /dev/shm
lrm                           506M       19M       488M    4%    /lib/modules/2.6.15-27-386/volatile
/dev/hda1                   106G       41G         65G        39%     /media/hda1
/dev/sda1                    299G       286G       13G         96%    /media/sda1


when i run fsck /dev/hda1 i get :

fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for dev/hda1

havent tried the live cd
Hda? I thought your problem was hdb?

Now why does hdb not even show up in the df output? What does "fsck /dev/hda2" do?

---

### Post by nyxynyx on 2006-12-17
i did fsck /dev/hda2 and got:

/dev/hda2 is mounted.

WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.
Do you really want to continue (y/n)?

Seems dangerous, so i chose n.

---

### Post by dannystaple on 2006-12-17
> **nyxynyx said:**
> i did fsck /dev/hda2 and got:

/dev/hda2 is mounted.

WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.
Do you really want to continue (y/n)?

Seems dangerous, so i chose n.

Yes, good plan. You can do this without the risk if you boot from a liveCD, make sure that /dev/hda2 is not mounted, and then fsck it from there. It is worth doing.

---

### Post by xpod on 2006-12-17
> Well it would be different. The letters after hd depend on which order the device is identified to the bios, the primary master would be a, primary slave b, and hdd would be the secondary slave. I have had to replace CD drives more often than hard drives.

erm...cheers:-? 

I was just alluding to the fact that it does look indeed like it could be a dodgy bit of hardware regardless of what it was or how it was setup:-? 
Only ever had to replace cd drives myself thankfully,all the hd`s so far have been fine apart from my own occaisional ERRORS;)

---

### Post by dannystaple on 2006-12-17
> **xpod said:**
> erm...cheers:-? 

Sorry - not meant to have come off as a flame.
> 
I was just alluding to the fact that it does look indeed like it could be a dodgy bit of hardware regardless of what it was or how it was setup:-? 

I quite agree, however, there are a few things in software that could cause this, although it is unlikely a newbie would have tinkered with hdparms, that can cause problems if misconfigured. 

> 
Only ever had to replace cd drives myself thankfully,all the hd`s so far have been fine apart from my own occaisional ERRORS;)
I have had a couple of older drives fail, because I tend to let my family take my cast off's (I go through a fair bit of hardware). I have even seen one month old drive fail, probably because it was simply from a bad batch - it actually started making a knocking scraping sound.. Ample warning to anybody to keep backups..

---

### Post by xpod on 2006-12-17
> Sorry - not meant to have come off as a flame.

Not all..my self conscious getting the better of me:rolleyes:  lol

> ve had a couple of older drives fail, because I tend to let my family take my cast off's (I go through a fair bit of hardware).

lol...All my pc`s hd`s,cd`s are my family and friends cast offs.......I only acquired one a few months back(win) to learn the basics on while we waited for this new vista thing to come out..rather than jumping in and buying a new pc there and then.

It`s all a bit of a blur but somewhere along the way ubuntu "happened" and now i got a house full of the bloody things with more pc`s, cd`s,hd`s & hdb`s than i could ever possibly need](*,) 

I wait patiently for my first knocks,scrapes and clicks:D

---

### Post by Amistad28 on 2007-01-06
Hello all,

i´m completely new is the world of linux. but i would like to ask your help.
I have formated my hard disk and created to partitions.

1 for linux and the other one for windows.
but i have head thats it better to install first linux and then windows.

but now i try to install Linux from the cd and after a while i get the following error.
[17179603.016000] Buffer I/O error on device hdd, logical block XXXXXX

does somebody what this error is and what i need to do.

thanks for your help.
a new user.

Regards.
Amistad28

---

### Post by dannystaple on 2007-01-06
Hi Amistad28,

Okay - lets start by having some info. Which CD are you using, how did you get it, and what drives (hard drive, cd, dvd etc) do you have on the machine?

HDD is normally designated for the secondary slave, which may actually be the CD drive. So you either haev a slightly dodgy IDE cable to the drive, a dirty CD, a badly written CD, a CD drive with dirty heads or a dodgy CD Drive. 
I recall(sorry - not in a position to reboot and test) that there is an option in the startup menu of the distribution CD's to verify the CD - I would start there.

Cheers,
Danny

---

### Post by warlock_handler on 2007-03-12
Hey i had a similar problem... 
and i figured what was wrong.. there were some bad sectors in the HDD and hence i was getting that error.. so what i did was formatted my HDD and this time while installing uBuntu i selected manually partition your HDD.... i put the root, /home, /urs, /boot, /var etc is different partitions i had made... and it really helped out.. ohh my suggestion whatever be your RAM create a SWAP partition that is atleast twice or three times more of that size..

---

