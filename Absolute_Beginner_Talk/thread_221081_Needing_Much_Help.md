---
title: "Needing Much Help"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2006-07-22
I have had a lot of problems.

First I installed Ubuntu, everything ran great.  Then I decided to reinstall my XP.  It was running slow and I had my everyday stuff up on Ubuntuand I already liked it.  So I moved some 1)KEEPER files over to my 2 HD, reformatted the first HD with XP on it, reinstalled Ubuntu on my first HD, moved the KEEPER files back over to my first HD, reformatted my second HD, and reinstalled XP.

Then I found that my pc automatically booted to XP and not Ubuntu.  So I installed [GAG]("http://gag.sourceforge.net/"), and I utilized the 2)[Super Grub Disc]("http://adrian15.raulete.net/grub/tiki-index.php") to try and get back into my Ubunto install.  Nothing has worked.  And I am a super-noob so I feel as if I am just scratching at the problems and making them worse.  If i had known that installing 3)[XP on a second hard drive]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") was such a bad idea, I would have done differently.  But now, without losing those files, I seem to have painted myself into a corner as far a fresh installs go.  I could partition more on my 2nd HD but I am a noob, and I dont want to mess up anymore.

As I see it I have 3 problems.
1) Keeper Files:  I have used some different drivers to basically look at my Linux HD.  [More in this thread]("http://www.ubuntuforums.org/showthread.php?t=220631&highlight=ext2").  I have also tried to find the files by using the Live CD to boot up in ubuntu but I cant find them anywhere.  I mean I can not, physically, while pointing and clicking through my Ubuntu File System, find them.  Yes, I do feel dumb.  I saved copies of them to my ubuntu desktop after  a fresh install.  If I could get those copied to my XP HD, I could install Ubuntu fresh again.
2)GRUB:  This is where I think my problem is right now.  But I have a very limited Linux skills in which to try a fix.  Its been a days worth of trial and all error and I cant figure it out.  I know that I have to edit GRUB somehow to get windows to think it is on the 1st HD.  I know that XP messed with the Master Boot record when I reinstalled it.  I tried to correct that but I keep getting errors or I cant find the grub.conf.  If this gets fixed, I think it is an easier one for somebody with the correct knowledge, then everything should work. 

3)XP:  I hate it and I wish I could get rid of it.  It is really the source of all the problems here when you dont factor in the user.  Would it be easier to physically take my pc apart and switch the HD's status?  Switching their master and slave status?  

Sorry for the long post ( as I continue typing) but from the forum archives, I am getting pieces of the puzzle from everywhere, and the complexity of the issues, at least to me, are overwhelming.  I would deeply appreciate a Ubuntu Sensei to guide me through these troubling times.

Thanks

---

### Post by brentoboy on 2006-07-22
I think you should attack this one step at a time in the following order:

1) find your important files, and make a CD (if possible)

2) Reinstall everything.  -- windows first, followed by Ubuntu.

(there are other ways to skin this cat, but this is by far the easiest I know of)

So,
for step 1, you need to kick in your liveCD.
If I am not mistaken, it has links to the local hard drives on the desktop.
Open up hda1 (or whichever one is your linux drive)

Does it have all the old linux files? (not necessarily your important data, I mean just any files, is it empty? or is there life in there?)

If it has your old files, and you want the ones you put on your desktop, then you can *hopefully* find them located at /home/<cornbreadly>/Desktop

If they arent in there, what is?  anything?

---
lets get to that point and continue from there.

---

### Post by Shortgeek on 2006-07-22
Well, if you're up to it, you could take apart your computer and do #3. But while it COULD be easy and fun, I'm not sure you would like it. But otherwise, which is the problem:

1. Instead of GRUB, Windows boots without offering you a choise.
2. GRUB loads, but puts Windows XP as default.
3. Other.

Sorry if you said so in your post, but I'm not sure.

---

### Post by confused57 on 2006-07-22
Since you have 2 hard drives, see if this thread might help:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you installed Ubuntu connected as the master drive, maybe you can just add the Windows entry to grub(Ubuntu as master and Windows as slave).  I'm not sure if I really understand how you have everything set up now.  This may work if you're able to boot into Ubuntu now, connected as master drive.

---

### Post by Cornbreadly on 2006-07-22
Okay, I quickly dismantled my PC and moved the prong clips denoting master and slave.  Booting Up, was nice, at least windows didnt come up.  But nothing came up.  So here I am in Ubuntu Live Cd.  

My Lrg HD with an Ubuntu install is Master, and the XP which was, until recently, working, is slave.  Sounds better.

I went poking around about 1) Keeper Files and nothing is listed under home but "Ubuntu" which I assume is this Live Session.  But I looked at the properties of Home and it lists 4 files.  3 Hidden?  And I can't change the permission because i am in this live  Session.  Any thoughts?

And now that I have switched the  HDs, should I run SGD again?  Try and Reinstall Grub through the Alt. Install ubuntu CD?  Thoughts?

Thanks for the quick replies by the way.

---

### Post by Cornbreadly on 2006-07-22
[This is the error that popped up when windows failed to load]("http://www.tinyempire.com/shortnotes/files/ntldr_missing.htm")

Its seems easy enough to fix but I am worried about the sequence i do these things in.  Its how i got here.

---

### Post by brentoboy on 2006-07-22
ubuntu is the user on the live cd
/home is in the directory structure used by the Ubuntu live CD as though it was a hard drive

is there an icon in the top left for your sda1 or hda1?

if not, what icons are on your desktop?

---

### Post by Cornbreadly on 2006-07-22
I was looking at my home directory through Nautilus.  It had an icon for "File System"

I dont think I can mount my XP HD because it would take me restarting ubuntu, which is just a live session right now.... which means I have the install and example icons on my desktop.

---

### Post by confused57 on 2006-07-22
From the live cd, you might want to open a terminal and see what the output of:

```
sudo fdisk -l
```
The -l is a small "L"

Also, grub could be reinstalled from the Live CD:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You might want to post the output of the above command.

I've never used it but here's a link to the super grub disk:
[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by brentoboy on 2006-07-22
in system > administrative > disks
you can see what disks are available.
and you can see where your installed ubuntu drive is mounted in your filesystem (if it is mounted at all) if it isnt, you can mount it from there, and go in and find your files.

---

### Post by Cornbreadly on 2006-07-22
Its there.  I tried to enable it and I was denied.  Inaccessable.

Should I partition a seperate ubuntu install?  Partition a data segment?

That way i can go in with a working ubuntu, hopefully move the files to the data segemnt, reinstall everything once again, keeping the KEEPERS seperate, and finally be at peace?

---

### Post by brentoboy on 2006-07-22
what's it called?
/dev/hda1
/dev/sda1

hda2

---

### Post by Cornbreadly on 2006-07-22
hdb1

but I also have 2 more drives listed from where I switched their master and slave status...

arrrrrrgggghhhhh...

is there a god of Linux to pray too?  What direction does Linus live from ohio?

---

### Post by brentoboy on 2006-07-22
ok
open up a terminal and type this (or cut and paste it one line at a time)
```

cd ~
mkdir my-drive
sudo mount /dev/hdb1 /home/ubuntu/my-drive

```

now, use nautilus
in your home, there should be a my-drive folder

is it there?  is there stuff in it?

---

### Post by Cornbreadly on 2006-07-22
YOU ARE AMAZING!!!!

Its there!  Ok... what should I do next?  Use that NSTF writer thing and put them on my XP HD?  Can I switch back my HD's now or should I leave them like this?

---

### Post by brentoboy on 2006-07-22
it is decision time...

do you have a burner on that pc?

if not, how large are the files you want to save? mp3s? movies? what are we dealing with here?

the best thing I can think of is to use the disk admin tool you used to discover you were hdb1 and wipe your ntfs using that.

then, create 2 partitions on it.  the first, ntfs, the second fat32.  if you cant create an ntfs from the ubuntu live, then make it anything else, we can deal with it later.

you can read / write fat32 from both windows and linux, so make that partition large enough that it can hold your shared stuff.

(32 GM is the max a fat32 can be)

once you have it, we will mount it and copy stuff over...

check in when you get that far...

---

### Post by brentoboy on 2006-07-22
I've been thinking about your situation...
It is probably safest at this point to reinstall windows now.

your "windows" drive is the master drive right (hda1)

so close down your liveCD environment, and boot from the XP cd.

when you have the option to choose which drive / partition to install xp on, you should delete the existing windows ntfs partition.  and create a new one with at least serveral gig (how big is the drive?)  if it is 40+ GB then save 32 GB for the shared fat32 drive, and make the first partion NTFS (the 8+ GB)  and install XP on the ntfs drive.

once you are into windows, use the disk manager to create a fat32 partition on the rest of the drive.  Then, reboot -- back into your Ubuntu live CD. We will remount your ubuntu drive, and copy your files onto the fat32 partition...

---

### Post by Cornbreadly on 2006-07-22
Ok.

I already have the first partition you asked for.  But this does sound a bit easier.

I have a 120 GB as my master right now.

So now I will reformat the entire drive.  I have 32 GB planned out for Fat32 and the rest of the 80 GB for NTFS?  but it will all be NTFS at the XP install right?

So the second HD isnt going to have an operating system on it according to your plan?  Will there be any lingering effects from the Master/Slave switch i pulled earlier?  Is the MBR record going to be reset?

---

### Post by brentoboy on 2006-07-22
dont make one big ntfs from the whole drive for windows xp.
make a single partition.  I would leave it around 32 GB, that is plenty unless you intend to rip DVDs inside of XP, or you have a file collecting habit that you just cant break.

leave the rest of that entire drive unpartitioned.

make sure you arent formatting the drive that has your favorite data on it (the one that still has ubuntu on it even though you cant boot to it.)

--
after xp is installed, we will set you up with a fat32 partition.
then reboot to live ubuntu, and copy files off of your ubuntu partition.

then, we will install ubuntu on what is effectivly hda3 - what's left of your windows drive after you give 32 to ntfs, 32 to fat32 .  There will be 50(ish) GB left over for 2GB of swap and 48GB of ubuntu installation.

we will setup what is now hdb1, and add it to your ubuntu system as /home  so that you can have a huge home partiotion.  (I assume your hdb is a huge drive too)

installing Ubuntu AFTER windows will give you a properly installed grub that will let you boot to either without a hassle.

---

### Post by Cornbreadly on 2006-07-22
Ok I am back.  Sorry, I jumped the gun and installed to a full NTFS on my 120 HD.  I do plan on ripping DVDS and collecting so I think it will work out.  Can I make a Fat32 with G-part when I get back into the live session?  I hope, I just got done setting everything up...

What should i make my second HD?  Fat32, NTFS, or a bunch of partitions?

---

### Post by brentoboy on 2006-07-22
your second hard drive will end up having ubuntu on it, you should probably make it ext3.

but dont do that until after you save your data.

do you have a burner?

How big is your second drive?

---

### Post by Cornbreadly on 2006-07-22
Will I be able to go through G-Part in the Live Session and make a 32 GB fat32 partition?  Then, after I install Ubuntu, I can transfer the files, then reformat my second HD as fat32 also because windows and linux can use it.

Do I make any sense?

2nd HD is 60GB

---

### Post by brentoboy on 2006-07-22
that makes sense, but you have it a little bit out of order.

you need to copy your files over to the fat32 partition BEFORE you install ubuntu!

so, the steps go as follows:

boot to live CD

Resize ntfs, make 32 GB of room for a fat32

use the mount command to mount your fat32 partition (so you can write to it from linux)

use the mount command to mount your existing ubuntu insallation so you can steal *valuable* existing data from it.

use nautilus to copy it all over.

once you like it, reboot to windows, and look to see that your ntfs partition still boots (resizing an ntfs is only a *mostly* safe thing to do)

then, install ubuntu.

it doesnt do any good to install ubuntu until you are sure your files are safely on a fat32, and you are sure that the xp installation on your ntfs drive is working.  if you have to reinstall windows after the partition resize, you need to do so before you add ubuntu  (windows has to be installed and working before you add ubuntu -- unless you are a master jedi)

---

### Post by Cornbreadly on 2006-07-22
And I am barely registering as a Padawan...   Thanks for all your help.  I will check back if any of this goes to the dark side...  OK enough star wars ref.

I see the light at the end of the tunnel.

---

### Post by Cornbreadly on 2006-07-22
One quick question...  Ubuntu should be going...?

Not on the 32 GB fat32 partition I am going to make in G-Part from the live session...

But Ubuntu goes on the 2nd HD... which will be fat 32 also...?

---

### Post by brentoboy on 2006-07-22
good enough...

if the needed mount commands give you a hard time, let me know.

you might have to be super user to write to the fat32 drive (at least with a generic mount command.  you can do this by running 
```
 sudo nautilus
```
when the time comes, then you will be in "super user file mananger" and you should be able to read/write to fat32

by the way, I am going out to eat with my wife in about a half hour, before then, I will be watching for any questions to have, but it might be 2 or 3 hours after that.

---

### Post by brentoboy on 2006-07-22
> **Cornbreadly said:**
> One quick question...  Ubuntu should be going...?

Not on the 32 GB fat32 partition I am going to make in G-Part from the live session...

But Ubuntu goes on the 2nd HD... which will be fat 32 also...?

no, use ext3 for the ubuntu partition.
it can be larger than 32 GB, and it is a way better file system.

---

### Post by aysiu on 2006-07-22
brentoboy is right that Ext3 is better than FAT32, but GParted can make FAT32 partitions larger than 32 GB, I believe. Windows, on the other hand, cannot.

You may also want to use ```
gksudo nautilus
``` instead of ```
sudo nautilus
```

---

### Post by brentoboy on 2006-07-22
enter aysiu...

it looks like when I go to dinner, if you are still working on this, you will be in good hands.

aysiu is one of those master jedi's we were talking about.

I think he is the guy who killed Darth Xubuntu

:)

---

### Post by Cornbreadly on 2006-07-22
Quick Update:

Right now it is going well...

Successfully i have:

[B]Installed XP

Reformated a fat32 partition on my XP master HD

ensured that XP works well under resized partition

copied over essential files from old Ubuntu install to fat32 partition

backed those essential files up on my XP partition in proper and easy for wife to find places[/B]

Thats where i am at right now.  So from what the amazing help has told me to do i will now:

[B]reformat slave HD in ext3 under live cd installation

install ubuntu on slave HD

enjoy[/B]

Do I have it all down?

---

### Post by aysiu on 2006-07-22
What are these "essential files" from your old Ubuntu installation? I'm not sure if they'll survive FAT32, depending on whether they're configuration files (.gnome2, for example) or just personal files (your pictures, music, documents, for example).

---

### Post by Cornbreadly on 2006-07-22
personal files.

MP3's, pics, writing...  all the stuff that you passively collect but can never really get rid of with a clean conscience.  

I am still in the back-up process so I will let you know how it turns out.  Thanks for your concern.

---

### Post by brentoboy on 2006-07-23
I would never recommend against having two copies of your data, so putting them on the ntfs isnt a terrible idea, but technically it is the same drive as the other one, and both are visible in windows, so I would recommend putting those essentials in your ubuntu home folder more than recommmend doubling them up on your windows folder.  at least then if you have a harddrive crash, no matter which one goes down, you are still in business.

anyway, I would set up the "my documents" folder to be "D:" or "E:" (whichever that fat32 partition ended up being.

if you right click my documents (either in the start menu or the desktop -- whereever it is these days) you can change the location on the properties page.  Then, stuff gets saved there, and it is accessable to both OSes.

---

### Post by Cornbreadly on 2006-07-23
Its done!  Everything worked out, and I got the files i needed.  I couldnt have done it without you guys.

Ill be seeing you in other threads concerning stupid linux questions.

---

