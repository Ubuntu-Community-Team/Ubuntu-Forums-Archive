---
title: "After trying Ubuntu, I cannot boot Windows. Urgent, please help."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by breadfan on 2008-03-25
First of all let me tell you that I have NEVER used an "Urgent, please help" title before, I know it's a lame method of requesting help, but I am in danger of losing data that I can never get back.

I downloaded Ubuntu Desktop 8.04beta, burned the .iso and booted Ubuntu.
Then I restarted the PC, but the BIOS said that my RAID failed.

I am using two Identical 500GB disks in RAID0.
My RAID setup reports that only the second disk is part of the RAID volume, and reports that the first disk is a non-RAID disk.
The only options that I have from the RAID setup is to
a) Delete the RAID volume
b) Restore disks to non-RAID status

in both options I get a warning that all my data will be lost.

I exited the RAID setup and booted Ubuntu again, to ask here for help.
What can I do?

Please help, I am desperate. And please, answer only if you are 100% sure, in the disks there are unique data that I simply cannot afford to lose.

---

### Post by Blue_Lander on 2008-03-25
If I understand correctly and you booted directly from the livecd, then none of your data or either of your hard drives should have been affected at all. 

In that case, it would be a bigger problem than Ubuntu, possible drive failure, raid controller failure, or something else. Best thing to do is to NOT boot the computer anymore than you have to, because if its a damaged hard drive you could cause more potential damage. 

Before I go on, are you SURE nothing was installed off the disc? What all did you do inside Ubuntu, exactly?

---

### Post by freebeer on 2008-03-25
If you only ran the live CD (and didn't install), then Ubuntu shouldn't have done anything to your drives.  I'm unfamiliar with RAID, so I don't have a solution for you to try to fix.  However, if you run the Ubuntu Live CD again, you should be able to read the data on the disks and back up the critical stuff before you attempt a repair.  I've done this with a Windows disk that Windows claimed was unformatted.

---

### Post by kushykush on 2008-03-25
He did not say he was using Ubuntu in the live mode. That would have affected nothing.  It appears that he installed Ubuntu on a Raid configuration.  

If you need an answer then please clarify how you installed Ubuntu?  What did you do when it came to partitioning your drive?  Is the GRUB start up menu comes up?  Is it showing all your Operating systems?  If nothing comes up then you have messed up your MBR.  

Your old data is all there, at least nothing should have happened to it.  How you will get to it is another story!!

---

### Post by breadfan on 2008-03-25
It can't be a drive fault.
It can't be a coincidence, drive losing RAID status right after I booted ubuntu.

When the Ubuntu CD booted, I chose the first option (Try Ubuntu without changing my computer, or something along those lines).

In Ubuntu, I did the following:

a) Checked my e-mail in Firefox
b) Played the example media files (Ubuntu video, aesop fable) and ran Gimp
c) Played a game of Sudoku for a minute (did not finish it)
d) restarted

I seriously doubt that any of the above actions could do such a thing.

---

### Post by Blue_Lander on 2008-03-25
> **breadfan said:**
> It can't be a drive fault.
It can't be a coincidence, drive losing RAID status right after I booted ubuntu.


Why can it be neither of those things? 
Little more info on your system may help us out here.

---

### Post by breadfan on 2008-03-25
Thanks for your anwsers.

To clarify, I did not install Ubuntu,
No such thing as drive partitioning came up.
If Ubuntu messed up my MBR, it didn't ask me before it did, that's for sure.... :(

---

### Post by Blue_Lander on 2008-03-25
You may try booting a Windows XP disc using the repair option, and running the following command after logging into the recovery console.

```
fixmbr
```

---

### Post by breadfan on 2008-03-25
Info on my system:

Core2Duo @ 2.4 GHz.
4 GB RAM DDR2
Gigabyte mobo DS3R (I think)
Two Seagate disks 500MB each running as RAID-0
nVidia 8800GTS 640MB
Vista Ultimate 64bit

I never though I'd say that in my life, but I desperately need my Windows back...

---

### Post by breadfan on 2008-03-25
This does not make sense.

I think that the operating system should not view the drives as independed drives.
I thought the would be regarded as a single drive, the RAID operation being masked.

I am really afraid to try and fix anything while my RAID volume is incomplete.
I think the way to go it rebuild the RAID volume, and then try using the Vista DVD to repair...

---

### Post by Moop on 2008-03-25
It's been a while since I used a raid array but have you checked the hdd's in the bios to make sure they are set for raid mode and not sata mode? Maybe something changed in the bios?

---

### Post by Blue_Lander on 2008-03-25
Honestly, it makes little sense to me as well. Aside from a type of failure, I don't see what else could have happened with what you have done. Hopefully someone smarter than I will come to the rescue. 

Make sure rebuilding your RAID will not wipe any data, because all your files *should* still be completely intact. If you don't have means to do so, you may take your computer to a repair shop, as they will be able to remove your drives, access them externally on another computer, and at the very least retrieve your files.

---

### Post by breadfan on 2008-03-25
Blue_Lander, thanks for trying.

Moop, I checked the bios. Nothing has changed, except that the RAID bios reports that the first disk is not a RAID disk, and therefore the RAID volume has failed.

Can Ubuntu see the disks through the RAID BIOS and modify just one of them? I hope not, but it seems so... 

This is a relatively new PC, that was working without a glitch, right until I tried Ubuntu. The whole thing took less than one hour. It would seem impossible that the hdd somehow had a failure just then.

---

### Post by frank002 on 2008-03-25
If you did not install Ubuntu and just booted off the live cd, I seriously doubt Ubuntu changed anything in your bios or did any damage to your raid array.

---

### Post by kolisikepu on 2008-03-25
> **Blue_Lander said:**
> You may try booting a Windows XP disc using the repair option, and running the following command after logging into the recovery console.

```
fixmbr
```

Can you confirm that you've tried what Blue_Lander suggested??  What he suggested is what I was going to suggest as I always mess up my Linux partition and then have to get rid of it and work with my Windows.

If you don't have an XP CD, then I'd recommend finding one quickly.  I'm not going to suggest to goto to a torrent site such as "http://www.mininova.org/" and download a Windows XP iso from there either.... :lolflag:

Go into recovery mode and "fixmbr".  If your MBR has corrupted itself, then this will help.

---

### Post by breadfan on 2008-03-25
@frank002: My friend, I do not claim that Ubuntu changed my BIOS.

It is a fact that I booted off the live CD.
It is a fact that after restarting the machine without the Ubuntu CD my BIOS reports that the first disk of the former RAID volume is not a raid member any more.
It is a fact that I cannot boot Windows anymore, and that I cannot access precious data, the kind of data that would make someone be sad for years for its loss.

I don't know what could cause that, the only reason I can think of is that Ubuntu somehow managed to write something to the first disk, bypassing the BIOS-defined RAID volume. Again I repeat that I don't know if this is correct, and I don't know how could such thing happen, I just can't think of anything else. And, to be frank, right now I don't care how it happened, I don't hold any grudges to Ubuntu or anyone, I just want to find a way to restore things, ANY way.

If there is a kind soul that could help, an entire family would be forever in gratitude for the help. Thank you.

---

### Post by kushykush on 2008-03-25
If you did not install Ubuntu then surely it is a bug in the Ubuntu live CD because it should not have done anything to your system.  You should report the bug.

Now, you do not mention which Windows are you using.  XP or Vista?  Whatever, it appears that your Windows boot loader got messed up.  You will have to get the Windows install disk.  If XP you can fix the MBR throuh the recovery console.  If Vista then use "Repair Windows"  when using the install disk.  If Windows Vista is unable to repair automatically, click the command button and use "bootrec.exe" -- once you execute that you will see a bunch of accepted commands.  Use "bootrec /fixMBR.  It shoud fix your MBR.  Restart.

---

### Post by breadfan on 2008-03-25
@kolisikepu:

The machine was running Windows Vista Ultimate 64bit.

I do have the original Vista DVD, and I do have an original Windows XP Professional CD.

However, you have to understand that I cannot afford to experiment. I really need to proceed with caution here.

I don't think that the problem could be fixed before the old RAID volume is restored. If I try fixmbr now, it will try to create a valid MBR in the first disk alone, not the RAID volume. I think that the way to go is rebuild the volume, and try to run fixmbr or any other recovery mechanism of Vista after that. But I am not sure, and I cannot take any chances without someone's confirmation.

---

### Post by breadfan on 2008-03-25
@kushykush:

Do you think that I should run Vista Repair with the situation as it is now?
This is a really weird situation. The RAID BIOS reports a RAID volume with only one member disk, which is impossible. The other disk appears as a non-RAID disk. In order for Vista to be able to repair, it should see both disks as a single RAID volume, shouldn't it?

---

### Post by kushykush on 2008-03-25
Look you have not lost any data.  Nor have you lost your Vista installation.  What you have "lost" is your raid configuration. Therefore, instead of worrying about the Raid, I would worry about getting Vista up and running. Once you have Vista running it will recognize all your drives (irrespective of the raid formation).  You can then back up all your data. And then try to restore the Raid.  Because as you said, if you try to undo or redo the raid config now, you can lose all your partition and the data. 

I lost my Windows Vista first install because Suse and later Fedora messed up my Vista boot loader.  Please keep in mind that Windows Vista boot loader will not allow GRUB or other to reside on its MBR.  Ubuntu actually recongizes that.  And it did not install GRUB in the MBR as Suse and Fedora did.

Now, in your case we do not know what happened.  But the fact that you cannot start Vista tells me that Windows boot loader where its MBR resides is messed up.  You may have to use bootrec.exe to actually rebuild the bootloader (Vista provides that command) and then see if you can bring up Vista.  Once Vista comes up go into administrative tools/disk management and see what happened to the disks.  If you still want the raid you will have the chance to back up/copy all your precious data.  Repeat if you try to do the Raid through your Bios/MOBO it will wipe out your hard disks.

---

### Post by breadfan on 2008-03-25
OK. Keeping my fingers crossed.
Will try this and report back.

---

### Post by breadfan on 2008-03-26
This is one of those things without explanation, one for the twilight zone...

Windows Vista repair needed RAID driver, and I had to remove my floppy from the machine (because my other computer has no floppy).

When I came back, I plugged the floppy back to my PC and turned the machine on. And then...

I watched in awe as the tho hdds were being recognized as a health RAID volume, and my machine
booted Vista without a glitch, as always.

Mind you, I did turn the computer off and on again before, the only difference is that the first time I did not pull the power cable off.

I cannot explain what happened and why, not that it matters now. It's almost 7:00am here, and I really need to go to bed, but I am going to buy another disk and back up my files first thing tomorrow.
I aged ten years in one night...

My heartfelt thanks to all you people for trying to help a man in dispair.
I'm so happy that my system is back.

---

### Post by maniac_X on 2008-03-26
There is an important lesson here that so many times gets overlooked by millions of users no matter which OS they are using. If you have valuable data, it should always be backed up some place safe or several safe places. Doing so will prevent premature aging ;) Glad things worked out for you in the end **breadfan**.

---

### Post by waspbr on 2008-03-26
I think ubuntu has been a victim of circumstance here. It was at the right place at the wrong time, considering the liveCD shouldn't (and doesn't) affect you computer unless you install it. So odds are that this was going to happens regardless of the live CD.

All you can do now is get yourself a cold beer relax, I'd also advise you to consider investing in one of those big (big as in memory big not physically big) external firewire/USB2.0 hard rives to  back up your essentials. 

That's the only thing I can think off aside from installing ubuntu, but even if that doesn't work, look on the bright side, you will be drinking a nice cold beer.

---

### Post by remcov on 2008-03-27
Hi all,

I am having the exact same situation here as breadfan, luckely my system is so brandnew that i did not blink to do a complete wipe. 


1) installed widows vista64
2) tried to install ubuntu 7.10, failed ( still do not know how and why ) 
3) reset, reboot and now both my raid drives are RED.
4) disconnect power cord, wait a sec and reboot
5) all works perfect, untill i try to install ubuntu. then we get the whole thing again i tried a few times ;)

6) tried to install 8.04 alternative.
7) Came as far as partitioning, but the thing locked up at 36% for 30 min at least
8) After this proberbly my mbr got messed and even while my raid drives were green windows would no longer boot.
9) redid the raid, out of precaution installed vista64


This kinda annoys me, i bought this system planning to run ubuntu and use vista for games only. Using ubuntu 8hours per day @ work, never any problems.
I really prefere it over any windows!


System specs:

E8500 @ stock
gigabyte x38 ds4
4gig of dominator 1066
nv 9800x2
2x 250 baracuda in raid 0

Any ideas?

---

### Post by kushykush on 2008-03-27
Installing any Linux based OS in a raid environment is a tricky affair and not as straight forward as you think.  Here is some guidance.  No one should install Ubuntu (or for that matter any Linux based system) directly.  it will mess up your raid and more.  Here is some guidance.  It is old but the basics are still good:

[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

That is what happened with the other fellow here also.  The lesson is clear. DO NOT INSTALL UBUNTU ON A RAID formation without the use of special Linux software and instructions.  Do your research fellows, before you attempt such a thing which is bound to fail.  Ubuntu is not to blame here.

---

### Post by remcov on 2008-03-28
Thanks, i had no idea it would be so tricky.
Windows vista seemed to go fine, because i followed the install vista on raid instructions;)
It's my first raid, and my first pc after a period of 5 years not having one:popcorn:

I will try that installation guide on monday and post back with the results.

---

