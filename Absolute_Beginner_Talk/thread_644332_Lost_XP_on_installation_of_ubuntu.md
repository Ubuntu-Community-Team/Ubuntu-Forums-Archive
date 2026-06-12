---
title: "Lost XP on installation of ubuntu"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Mike Atnip on 2007-12-18
Hi.  I am new at Ubuntu but wanted to ease into LInux.
I downloaded, burned, and ran the Live CD successfully.  I poked around a bit, and thought I would put it on the hard drive so I could see how it performed there.
So I clicked on the icon, and went through the process.  On the one part, I set to "use longest contiguous space" or whatever it is worded.  I thought this would neatly partition off a few gig and I could then have a dual boot system.
Ubuntu works fine.  But I cannot find anything of XP, including my latest work that I stupidly did not back up.  :-(((((((((((
I found Super Grub and tried all options on that, but nothing brings back XP.  When I set the settings back to go to XP I get a black screen with blinking curser.  After a couple of minutes any key makes a beep.
I am a newbie, and so I need newbie talk.  I like Ubuntu and the whole Open Software concept, And I can pretty easy say goodbye to MS.  But I really would like my docs, photos, etc back!
Help!
I am using a Dell laptop Inspiron 1000 with 40gb harddrive and 512 ram.  I had about 10 gb open when I loaded Ubuntu.  Ubuntu works fine and I am using the browser and email with my previous broadband setup without a glitch.

---

### Post by Duck2006 on 2007-12-18
From the terminal

Applications>>Accessories>>Terminal

Type

sudo fdisk -l

and post the output hear.

---

### Post by Mike Atnip on 2007-12-18
michael@michael-laptop:~$ sudo fdisk -l
[sudo] password for michael:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4701    37760751   83  Linux
/dev/sda2            4702        4864     1309297+   5  Extended
/dev/sda5            4702        4864     1309266   82  Linux swap / Solaris
michael@michael-laptop:~$

---

### Post by neanderthalman on 2007-12-18
uh oh.  I'm no guru, but I'm pretty sure you've accidentally repartitioned and reformatted your entire drive.

**Don't panic**.  Despite having been formatted, your data is likely still there.  You will need some sort of data recovery software to get at it.  I'm far too new to linux to know what to use, but I had good luck with a windows program called "GetData: Recover My Files".  Save my bacon, and about six years worth of photos.

I'm sure someone here knows of the best path foward.

---

### Post by Duck2006 on 2007-12-18
> **Mike Atnip said:**
> michael@michael-laptop:~$ sudo fdisk -l
[sudo] password for michael:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4701    37760751   83  Linux
/dev/sda2            4702        4864     1309297+   5  Extended
/dev/sda5            4702        4864     1309266   82  Linux swap / Solaris
michael@michael-laptop:~$

Windoze does not show up on your drive so i say you have installed ubuntu over your xp install.

---

### Post by inversekinetix on 2007-12-18
Seems like you have installed over the windows installation.  That ubuntu installer is not as user friendly as it should be.  You will have to reinstall windows again. Do you have disks?

---

### Post by ByteJuggler on 2007-12-18
If you have data you absolutely need to try to recover, the first thing to do is to stop making any alterations to the disk until you have a full disk image backup, so if any recovery efforts screw things up even worse, then you can go back to the image.  I would highly recommend you buy a backup hard disk of equal or greater size to the one you have currently.  You can use Linux from the LiveCD to backup/image your disk accross to another, I/we can help you do that.  

Once you have a backup, you should try an NTFS file recovery/undelete program, apparently [File Scavenger]("http://www.quetek.com/prod02.htm") is very good (I have it on good authority that it is.)

---

### Post by Mike Atnip on 2007-12-18
I do not have data that would be worth me spending a lot of money to recover, but I am willing to give it a try and if I lose it, well, I lose it.  I do not have the Windows disk as I bought the machine off ebay used.
If I reinstalled XP somehow, would that bring up all the files not covered over by Ubuntu?
And are there any Open source equivalents to File Scavenger?
Looks like I am in Ubuntu-land for sure.  I intend to stay.  Just don't really like the instantaneousness of my transition.  :-)

---

### Post by Duck2006 on 2007-12-18
> If I reinstalled XP somehow, would that bring up all the files not covered over by Ubuntu?

No, because you would have to reformat the part of the drive where you partition for your windoze install will go, then reinstall windoze so most of what you have lost your not going to be able to recover.

---

### Post by monte48lowes on 2007-12-18
I highly recommend using 'photorec'. This program is designed to recover photos and other files from memory cards etc. It will recover every file it can find from a hard drive. You will need some place to put those files though. If you have an external hard drive that would work great. It is available on the live CD, which is where I recommend running it from.

Mike

I have used this program to recover family photos after a hard drive crashed, with a corrupt super block.

---

### Post by Skidpad on 2007-12-18
> **Mike Atnip said:**
> Looks like I am in Ubuntu-land for sure.  I intend to stay.  Just don't really like the instantaneousness of my transition.  :-)
Glad to hear you are accepting this!  Usually when this happens around here, there are threads with lots of capital letters, exclamation points, and threats by one's significant other.  :D

Sorry to hear about your data, but Welcome Aboard.  You already have the one thing many people in your situation don't - the right attitude. Cheers.

---

### Post by sstusick on 2007-12-18
> **Skidpad said:**
> Glad to hear you are accepting this!  Usually when this happens around here, there are threads with lots of capital letters, exclamation points, and threats by one's significant other.  :D :lolflag: 
> **Skidpad said:**
> Sorry to hear about your data, but Welcome Aboard.  You already have the one thing many people in your situation don't - the right attitude. Cheers. I second that. 
Good luck, Mike.

---

### Post by nowshining on 2007-12-18
don't worry we've all lost things that we'd wish we didn't have. :) u'll be upset a night or two and things going on and on thru ur brain but after a week u'll be calmed down and as the time passes on u'll move on from it and work from there and make great progress into the linux/ubuntu world.

---

### Post by Mike Atnip on 2007-12-18
> **monte48lowes said:**
> I highly recommend using 'photorec'. This program is designed to recover photos and other files from memory cards etc. It will recover every file it can find from a hard drive. You will need some place to put those files though. If you have an external hard drive that would work great. It is available on the live CD, which is where I recommend running it from.

Mike

I have used this program to recover family photos after a hard drive crashed, with a corrupt super block.

Mind giving me some more direction with this one?  Are you referring to the Ubuntu LiveCd that I created?  ANd would it work to transfer them to a SD Card via USB?
What I had hoped to do was run Ubuntu and neatly go over into XP and copy files.  Sweet dreams, eh?
thanks to all of you for your input and encouragement!
mike
Ok, edited to include that I found this by Google, and have it downloaded.  How do I use it in conjunction with live disc?

---

### Post by pdlethbridge on 2007-12-19
Mike, try going here for some more info. Testdisk is in synaptic
[http://ubuntuforums.org/showthread.php?t=448817](http://ubuntuforums.org/showthread.php?t=448817)

---

### Post by agerg on 2007-12-19
For what its worth...I also made the tragic misake of killing windows (4 days ago) on a live cd install! Tis linux all the way now:)

---

### Post by ByteJuggler on 2007-12-19
> **Mike Atnip said:**
> I do not have data that would be worth me spending a lot of money to recover, but I am willing to give it a try and if I lose it, well, I lose it.  I do not have the Windows disk as I bought the machine off ebay used.
If I reinstalled XP somehow, would that bring up all the files not covered over by Ubuntu?
And are there any Open source equivalents to File Scavenger?
Looks like I am in Ubuntu-land for sure.  I intend to stay.  Just don't really like the instantaneousness of my transition.  :-)

Reinstalling XP is likely to possilbly further overwrite parts which may currently not have been already covered over by Ubuntu.  You should ideally not do anything that writes to your hard disk until you've had a go at recovering what you need to recover.  If you only have one pc with this one hard drive then you're a little stuck as far as recovery is concerned I'm afraid.  You really need at least another disk that you can work with.  As for other data recovery programs, the only free (as in beer) tool for Windows/NTFS undeletion I can think of offhand is ["Recuva"]("http://www.recuva.com/"), maybe worth a look.  Most of the data recovery programs for Windows however have free demo-modes so you can try them and see how much they can see/recover before committing money to them.

---

### Post by Mike Atnip on 2007-12-19
> **ByteJuggler said:**
>  You should ideally not do anything that writes to your hard disk until you've had a go at recovering what you need to recover.  If you only have one pc with this one hard drive then you're a little stuck as far as recovery is concerned I'm afraid.  You really need at least another disk that you can work with.

Ok, I think I get the drift.  The files, at least some of them, are probably not overwritten and are still there.  But to get them out, I need a place to put them because if I recover them out of the HD and save them back on to the same HD, I end up overwriting other data that I may want.
So, a feasible option for me is to put out a few bucks for an external HD and then move them out with LiveCD.  Once the files I want are on the external HD, I simply pull them back on to the internal HD.  (ANd I keep them backed up on the external one for future botches like I just did. :popcorn:  Am I on track?
Or would it be better to load Ubuntu on to the external harddrive and pull the files out that way?

And another question.  I thought I used the "put into largest contiguous space" option when I put Ubuntu onto my harddrive.  Was this the wrong option?
IMO, there should be a splash screen that says "you are about to overwrite your hard-drive, are you sure you want to do this?"  And, "have you saved your needed files before beginning?"  There are some of us dummies out here!

---

### Post by philinux on 2007-12-19
Good idea just use the ext HD for your recovered files.

---

### Post by monte48lowes on 2007-12-19
Your first thought there with using the external hard drive a backup is the method I would use. 

Summary:

1. Boot live CD
2. Attach external hard drive
3. Use 'photorec' to recover files from hard drive and write them to the external hard drive
4. Re-install winXP (if you so choose)
5. Re-install ubuntu
6. Sort through the thousands of files on external hard drive to find the ones you need
7. Copy needed files back to internal hard drive

This is not an all-inclusive howto, just a summary for understanding. BTW, I ended up with over 300,000 files when I ran photorec. It will recover any file it can find. And that's why it's good. :D

Mike

---

### Post by az on 2007-12-19
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

That has any data recovery software you could want and it is all free-libre, meaning it is not limited to demo-only.  It's a live cd, so it doesn't need to be installed and therefore will not overwrite any data.  You should download the iso image on another computer.  You should stop using the affected computer immediately.

You can data-carve your files from your overwritten partition.  Depending on how full your drive was, you should be able to recover a significant amount of data.

Use Photorec or Foremost.  You can either use the REscue Remix or just boot the live cd and install photorec or foremost from the repos, as suggested.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Mike Atnip on 2007-12-19
I tried using photorec.  I'm lost.
Using LiveCd, I downloaded the files,  Then right/clicked on extract on the photo_static file.
This takes me to an "extract" option that allows me to pick the "places" I would like to lok for files, the files types, and options.
Alas, I cannot find any documentation on how to use this, and dont know where I whould start looking to extract.  Can anyone guide me to some documentation for dummies.

---

### Post by Chaz_UK on 2007-12-19
If it makes you feel any better I accidentally deleted all of our daughters first birthday vids when i recently reformatted my desktop to dual boot ubintu.
I backed up all my music, pics amongst other things.... All except the "videos" folder.

I'm going to tell my wife *after* Christmas i think...... :)

---

### Post by joecool362 on 2007-12-19
Sorry to say but I personally think you can say good by to windoze and micropain because you wiped your hard drive well installing Ubuntu, and unless you want to go out and by a copy of windoze from the store for a hundred bucks and install it... you might as well stay with Ubuntu because if you get desktop effects to work it is way cooler than even  vista:sad:.

---

### Post by Duck2006 on 2007-12-19
This one is using knoppix to recove data it may help.

[http://www.ibm.com/developerworks/linux/library/l-knopx.html](http://www.ibm.com/developerworks/linux/library/l-knopx.html)

---

### Post by pdlethbridge on 2007-12-19
You might want to do this if you have to reinstall ubuntu. Create 3 partitions, 1 each for the OS ubuntu, Home, and swap. Mine is set this way and all my photos and settings are in home so when I reload the OS, my files are still there. When you get to the screen on install that asks if you want to auto or manually partition, do manual. My 80 gig is set for 750 mg for swap, 10 gig for home and balance for /.(OS) If you want windows, put in another partition at the beginning of the drive, then /, then home, then swap.

---

### Post by az on 2007-12-20
> **Mike Atnip said:**
> I tried using photorec.  I'm lost.
Using LiveCd, I downloaded the files,  Then right/clicked on extract on the photo_static file.
This takes me to an "extract" option that allows me to pick the "places" I would like to lok for files, the files types, and options.
Alas, I cannot find any documentation on how to use this, and dont know where I whould start looking to extract.  Can anyone guide me to some documentation for dummies.

Boot the live cd
open a terminal
run:
sudo apt-get install testdisk foremost
Plug in your external hard drive
run:
sudo photorec /dev/sd(whatever - probably /dev/sda in your case)
follow the prompts and use the text menu.  Tell it to save recovered data to where your external hard disk is mounted.

Once you have use photorec, you can try foremost.  It does the same thing as photorec, but works differently.

See:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by hyper_ch on 2007-12-20
> **inversekinetix said:**
> That ubuntu installer is not as user friendly as it should be.
The ubuntu installer is user friendly but nothing can prevent from people doing thing that they don't fully understand.

---

### Post by Mike Atnip on 2007-12-20
> **hyper_ch said:**
> The ubuntu installer is user friendly but nothing can prevent from people doing thing that they don't fully understand.

Ahhhh.  You got me here!  
:lolflag:

Well, when all else fails, read the instructions.  So I plan to read now.  Actually I was planning on going slow and reading as I go.  My ignorance pushed me into this desperation.
Thanks for all your help out there.  I can say this personalized help is 1000% better than what I would expect from Microsoft.
I guess you can consider this thread ended for my part, until I get my mind caught up to where my OS is at.  That may be a while.:popcorn:

---

### Post by hyper_ch on 2007-12-20
I hope you did not lose any really important stuff or that you can get it back somehow.

But know what, I'm sure you'll never make that mistake again.

---

### Post by Mike Atnip on 2007-12-21
> **pdlethbridge said:**
> You might want to do this if you have to reinstall ubuntu. Create 3 partitions, 1 each for the OS ubuntu, Home, and swap. Mine is set this way and all my photos and settings are in home so when I reload the OS, my files are still there. When you get to the screen on install that asks if you want to auto or manually partition, do manual. My 80 gig is set for 750 mg for swap, 10 gig for home and balance for /.(OS) If you want windows, put in another partition at the beginning of the drive, then /, then home, then swap.
Can you tell me or direct me as to what format the Home should be?
I have forgotten about rescuing my files.  I successfully partitioned my 40 gb hard drive into 4 parts: app. 10 for XP, 16 for Kubuntu, 10 for my Home, and the rest for swap.
I now have the dual boot working (it pays to read the instructions well :-)  ), but I want to format the Home for a place to store my files that can be accessed from either XP or Kubuntu.
Ntfs?

---

### Post by dondad on 2007-12-21
> **Skidpad said:**
> Glad to hear you are accepting this!  Usually when this happens around here, there are threads with lots of capital letters, exclamation points, and threats by one's significant other.  :D

Sorry to hear about your data, but Welcome Aboard.  You already have the one thing many people in your situation don't - the right attitude. Cheers.

A similar thing happened to me, except I did not overwrite the whole XP partition, but resized it and something went wrong. I was able to get most of my data off from it, deleted the partition, redid Ubuntu using the whole disk and never looked back.

---

### Post by wispygalaxy on 2007-12-21
[COLOR="Indigo"]I can relate to what you are going through.  I accidentally clicked on "Guided--use entire disk" during the Gutsy install, and I lost Windows on my laptop along with all my files.  I can't stress how important it is to backup your data.  I had my important data on a flash drive, luckily.  We are here to help you, so don't feel too bad!  8)[/COLOR]

---

