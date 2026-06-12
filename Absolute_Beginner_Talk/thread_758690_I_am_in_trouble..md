---
title: "I am in trouble."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by ergl on 2008-04-18
I downloaded on my desktop an installation of Ubuntu - It was supposed to install, I followed the instructions until my internet connection went down. Now I am stuck. The system would not boot nor I could not restore the Hard Drive back to Windows- although the BIOS could still see it, FDISK would just hang. - I am trying to restore it to FAT again so I can start over - Any advice would be appreciated. Thanks

---

### Post by PmDematagoda on 2008-04-18
I am sorry, but while I can comprehend what you are saying, I don't really comprehend as to what the true problem is or how it came to be.

Could you please make your problem a little clearer?

---

### Post by itix on 2008-04-18
Uh... you did not burn ubuntu on to a CD?
You can use gparted (System => something, probably administration) on the live CD and from there format the drive to FAT32, but Windows won't be there any longer if you have already formatted the drive to ext3. I DO hope you have backed your data up so that you can restore it if this would happen. I recommend Ubuntu over windows of course, but that's only me.

I'd also recommend that you with Gparted create one FAT32 and one Ext3 partition so that this problem won't happen again. It's a fairly easy-to-handle program. I got the hang of it directly when I used ubuntu =p

---

### Post by itix on 2008-04-18
My guess is that he has installed ubuntu but somehow managed to erase the windows drive as I suspect he was trying to do a dual boot.

Using the GUI gparted is his best bet I'd guess.

To ergl: Just create two partitions, one FAT32 and one ext3 if it is a dual boot you're aiming for. Install windows on the FAT32 and Ubuntu on the ext3 and it'll create swap by itself.

---

### Post by erlyrisa on 2008-04-18
I'm going to take a guess at this but...
did you try and install via the WUBI install?

(download the little application - WUBI ... and install Ubuntu as a file on XP? , the install proceeds right ther from a booted XP install and you have to wait while it downloads?)

(becuase it that's the case... that didn't work for me either - but that was about 6 months ago)


if it was a Wubi install than nothing is lost.

---

### Post by ergl on 2008-04-18
Thanks for the advice - I am really stuck - I vaguely remember what I did. All I remember is that I chose Dual Boot over Windows - the program downloaded and I ran it - It asked for a name and a number too - It was at the point when it asked what mirror I should take and I chose the one for the unitedstates - then my connection failed and that when my situation began, can't get back into my HD -

Yes Itix - I got it, just now -:confused: Didn't burn the ISO - I have started to burn out the Iso into a CD - so far, burnt 2 CDs, with problems - Would you recommend that I download the ISO again?

Elyrisa - it's not the Wubi:confused: I am sure that I didn't use that software, as that's the first time I heard of it. Right now, my desktop is Zero - just hangs. So, I can't really do anything about it until I revive it back to Windows, or get Ubuntu installed. Thanks for the advice anyways.

Thanks for the advice - I'll work on it, maybe burn the ISO and that would get it going, The bios reports the Hard Disk - the PC is a pentium 800 mhz Asus with 512 mem - Should've work - Thanks again.

---

### Post by erlyrisa on 2008-04-18
did you download a small program and execute it in windows?

becuase if that's what you did (and it was official) then that is called Wubi


--normally the live cd requires you to boot to Ubuntu from the cd first (no downloading)

---

### Post by itix on 2008-04-18
If I don't know really. Unless you have another computer to burn the CD from I think it's kind of hopeless. If so, try downloading the iso again and burn it to a CD.
It might be a damaged iso. You can't burn from the live-CD environment unfortunately unless you have dual cd trays.
If you are used to windows partition editor on the windows disc, you might want to create the windows partition first from there and then create the linux ext3 later on the leftover empty space. I remember that being what I had to do when I wasn't used to linux.

If you don't manage to get back into your windows partition and you must reinstall it, make sure you install windows first since windows don't like competition and disble Ubuntu upon install.

If you have a spare computer to watch this, this is the best screencast to help with the dual boot:
[http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot&ei=-swISPDrGo-GjgK554yoAQ](http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot&ei=-swISPDrGo-GjgK554yoAQ)

---

### Post by maniac_X on 2008-04-18
If you are going to be burning a Live CD image(.iso), then be sure you burn it at the slowest possible speed your burner will allow. This will help prevent any errors during the burn process.

---

### Post by anewguy on 2008-04-18
When you say it just hangs, do you mean at a boot of your PC without a CD in the drive (in other words, you can't boot your PC at all)?  Do you get any messages - boot disk not found, grub xx, anything?  Are you presented with a boot menu where you have to select Ubuntu versus Windows?

If not, I suspect your installation got to the disk partitioning, aborted for whatever reason, and has now left your hard disk with a bad partition table.  You can try installing Windows again and see if that works, or you could somewhere download and burn a copy of the Ubuntu LiveCD and go from there.  I'm not sure if Windows will install without first doing fdisk.  You could run that from a Windows boot/install floppy or CD, or use the Ubuntu LiveCD and do it.  

Keep in mind that if you want to dual boot:

(1) Install Windows first if not already installed.  If it is a fresh install, run fdisk first to set aside a partition for Windows but leaving minimum of 4 gig free in another partition to install Ubuntu in.  If you already had Windows installed, be sure to run a defrag before proceeding (and as always, backup important files prior to anything).  Note the used/free space on the disk.

(2) Boot using the LiveCD, then select Install

(3) At the partitioning manager, be sure to select manual.  Leave your existing Windows partition alone, then add a swap partition and a minimum of 1 ext3 partition and specify it's mount point as "/".  If you did NOT need to do a fresh install of Windows, and no extra partitions are shown, you will need to manually select resize of the Windows partition, remembering to leave plenty of free space in the Windows partition (judge from the used/free space as mentioned in step 1).

(4) Follow the rest of the on-screen instructions and let the install run.

:)

---

### Post by ergl on 2008-04-30
Thanks - I am now ready for new "troubles". I finally got Ubuntu to install and I'm using it now. [http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

Thanks again.

My ubunture begins![http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

