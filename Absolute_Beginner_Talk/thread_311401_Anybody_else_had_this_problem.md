---
title: "Anybody else had this problem?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by djrobthaman on 2006-12-02
Hi everyone,

I posted a very similar thread in the installation section but got no reply.  Don't mean to spam but still having no luck.  Has anyone else had this problem?  Has anyone been able to fix this problem?  Any feedback would be great.

I really want to be able to dual boot my PC (actually thinking of doing a full switch=-over to linux considering how frustrated I have been getting recently with Windows).  And I think Ubuntu looks really great.  I booted up the live cd (the desktop cd, 64 bit version) and it was pretty slick.  Loved it.

I inititiated the install.  It detected all my hard drives and I had no problems.  After the install when it told me to eject my CD I did so and pressed any button.  Loads of buttons actually.  And the system wouldn't restart.  After a while I got fed up and decided to hold down the power button and turn off the PC manually.  Did it, and restarted.

Grub started up great.  I selected the option to load Ubuntu and... nothing.  Actually, I got a message saying that it couldn't boot from hard disk (maybe not the exact phrasing.  I've since installed suse and can't remember the exact message it gave me.  After that I could get back to the main menu and booted to Windows fine).  This is annoying because I really wanted ubuntu.  What do you guys think I can do to fix it?

My specs are below:

MB: Foxconn 925XE7AA-8EKRS2 925XE 775
CPU: Intel Pentium 4 541 Prescott 3.2 GHz LGA 775
RAM: G. Skill Extreme Series 1GB 240-pin DDR2 533 (PC4200)
Video: ATI 100-714600 Radeon X1300 256MB DDR PCI Express x16 All-In-Wonder 2006 Edition
HD:
Seagate Barracuda ST3320620A 7200 RPM IDE Ultra ATA100 320GB (x2)
Western Digital Caviar SE WD2000JB 7200 RPM Ultra ATA100 200GB
Another 180GB drive I salvaged from my brother's Dell



Thanks,
Douglas

---

### Post by Shatrat on 2006-12-02
Really not sure what went wrong with the installation, but you certainly have plenty of hard drives.  Do you have room to make a couple partitions on one of them and try installing Ubuntu again?  If you have room to make some partitions for it there is nothing stopping you from tinkering around to try and get a working Ubuntu install without disturbing SuSE.

If you continue having problems with finalizing the installation maybe you should try disconnecting any devices not necessary for the installation, maybe it's having trouble unmounting something.

---

### Post by roboghast on 2006-12-02
[http://www.ubuntuforums.org/showthread.php?t=252820](http://www.ubuntuforums.org/showthread.php?t=252820)

This is my own experience with dual booting from the same hard drive - also search the forums under "dual boot" 

roboghast

---

### Post by IYY on 2006-12-02
Was the error with Grub (the boot manager), or did it actually try to boot Ubuntu? If it's Grub, then I think it's happening because of old BIOS on your motherboard and your unusually large hard disk.

I've had a Grub problem on my 200GB disk, and not on my 80GB and this is the explanation I got after some research.

---

### Post by djrobthaman on 2006-12-02
IYY
I honestly don't know if it's grub.  I don't really know how it works other than that it lets you boot more than one OS.

Grub works fine with suse.  I don't know if that's any indicator though.

I used to have a smaller hard disk around but I think I got rid of it :(.  So I can't test that out.  I don't know if it makes a difference to test it out on a drive that actually is of a smaller size, but I was installing ubuntu on a 50gb partition.

It did actually try to boot.  Or I thought it did.  It just gave me that message that it couldn't boot.  Maybe it didn't try to boot.

roboghat
I'll look at the link.  Thanks.

Thanks to everyone.  I'm gonna try and do another install now.  See if it runs.  Maybe I'll be able to give a better description of the problem this time if it happens again.

Douglas

---

### Post by djrobthaman on 2006-12-02
So,

Back on Windows again.  For some reason I couldn't even boot the CD.  The boot menu loads, but I can't really go anywhere beyond there.  If I click on start install or check cd for errors I get the following read out:

Booting from the kernel

[32.11117] PCI: Cannot allocate resource region 2 of device 0000:01:00.0
[32.11157] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[32.11211] PCI: Cannot allocate resource region 2 of device 0000:01:00.1

I rebooted a few times and got the same readouts, but with different numbers in the square brackets.  You guys know what this means?  Or any way of getting the CD to boot?

Thanks again,
Douglas

---

### Post by waltrothfuss on 2006-12-02
I have had this happen many times before.  Find an old dos boot disk that has fdisk on it, or download freedos and burn the iso.  Boot from the dos boot disk or freedos cd.  Once you get to a command prompt, enter the command "fdisk /mbr" (without the quotes, of course) and hit enter.  This will kill the master boot record on the hard disk. Continue to use fdisk to delete all the partitions on the hard disk and leave it completely unpartitioned.   Then I recommend you install your other operating system first, such as windows xp, by installing its installation disk and booting from it into the install program.  During the windows installation you will have the opportunity to partition the hard disk.  Only partition enough to run your windows stuff.  Leave the rest unpartitioned for linux.  Finish the windows install.  Once that has completed, check that your hard disk will boot into windows as it used to.  If not, then the boot sectors on your hard disk may be damaged.  Try again with a new hard disk.  Once it boots into windows okay, shut it down and reboot using your linux cdrom and install linux. During the installation it will ask you if if you want to use the entire hard disk, or the unused space and some other choices I don't recall. Install it to the unused space.  The grub loader (assuming you are installing Ubuntu) will install itself onto the hard disk and when you subsequently reboot the computer grub will let you choose which operating system you want it to boot into, windows or linux. Watch for grub to display a message on the screen to hit a key for options, else it will boot into its default choice which should be linux.

---

### Post by djrobthaman on 2006-12-02
Walt,

Thanks for the info.  One question though.  How is using fdisk and executing fdisk/mbr and then deleting all the partitions different from loading the windows cd and deleting them in there before the install?

Also, do you think I'd have to delete all my hard drives or just the one I want to install the OS in.  

Thanks,
Douglas

---

### Post by waltrothfuss on 2006-12-03
Hi, Douglas -

I have tried it before by just installing windows, and it does not work to correct the damaged master boot record.  I don't have a clue why not; but killing the master boot record using fdisk does work.  The partitions just need to be deleted on the drive where the master boot record is being installed - that is, the drive you intend to boot from which should be the C drive.

Walt

---

### Post by djrobthaman on 2006-12-03
I see.

Will try that one very soon.

Thanks a lot,
Douglas

---

### Post by waltrothfuss on 2006-12-03
Douglas -

When you enter the fdisk /mbr command, make sure there is a space between fdisk and /mbr.

Walt

---

### Post by djrobthaman on 2006-12-23
HI everyone,

I finally tried what Walt suggested.  I downloaded the freeDos CD and deleted the master boot record.  Used fdisk to delete all the partitions and installed Windows followed by Ubuntu.  This went fairly well I thought because the liveCD booted the first time I loaded it in (that didn't always happen before).

ANyway, long story short, I'm still having the same problem.  Anybody know what I could do to fix it?

Thanks,
Douglas

---

### Post by gn2 on 2006-12-23
Maybe try doing it this way: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by djrobthaman on 2006-12-25
Actually,

did it another time and now I've gotten a little bit further.  The splash screen loads and it gets as far as "mounting root file system" (or something like that).  Then after a while it says "waiting for root file system to mount" and it gets stuck there.

Any suggestions for getting over this hurdle?

Thanks for all your help,
Douglas

EDIT:Now that I think about it.  I think I used the 6.06 install dvd as opposed to the 6.10 cd.  I have about 10 ubuntu install discs laying around here from the numerous ways I've tried to install it.  And it makes sense since when I tried to install 6.06 previously that was exactly what happened ("mounting" followed by "waiting to mount").  I don't know if this sheds any light on my 6.10 issues. Or if maybe it means it's possible for me to install 6.06 with some fixes and then upgrade to edgy from there.  Any suggestions would be really appreciated.

Thanks again

---

### Post by djrobthaman on 2006-12-26
Hmm...
My edit didn't bring the post to the top.  That's strange.  Thought it would do that.  Anyway, any suggestions based on the info in the edit?

Thanks,
Douglas

---

### Post by djrobthaman on 2007-01-02
Hi everyone,

I'm back again.

So don't ask me how, because I don't know how (nothing different happened other than the CD actually booted and I followed the instructions), but I got ubuntu working on my machine for maybe 3 days.  Then the grub loader died (at least I think it did.  I booted about 5 times and the boot menu wouldn't load).  So I installed again and it worked fine or so I thought.  It booted fine after the install and I did nothing to it.  I didn't even install my video drivers.  Just shut it off.  Went back to Windows for a day and now I'm trying to load ubuntu and it won't load.  The grub menu loads fine and it sees all my OS's (windows, ubuntu and suse) but will not load ubuntu.

Whenever it loads it says something like:

Decompressing the kernel...

[32.11117] PCI: Cannot allocate resource region 2 of device 0000:01:00.0
[32.11157] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[32.11211] PCI: Cannot allocate resource region 2 of device 0000:01:00.1

Actually I don't think that's right.  The last three lines are right and decompressing (something) is in there before as well but there are a couple extra lines before the allocation errors.  I'll reboot and write them down and edit it back into the post.

Any suggestions?

Thanks a lot,
Douglas

PS  I don't know if this might help.  But on both occasions when I installed ubuntu and got it to work, the only way it would actually load would be to wait the 9 seconds that the menu waited for an input before going to the default OS.  And even when I did wait all the lines above would display and then I think maybe another and it would boot.  If I didn't wait and  selected ubuntu before the time was I would get the same output as above.

PPS  I feel like this is a bit all over the place.  Sorry if it is.  I'll try and clarify anything that doesn't make sense.

---

### Post by squrl on 2007-01-02
I had a simialr problem and punched F8 or F12 and the windows or bios gave me a choice of which drive I wanted to boot. Found out that grub was picking the wrong drive.

---

### Post by djrobthaman on 2007-02-07
Hi everyone,

It's been a long time now since Ive been able to get ubuntu to install.  I still can't even get the live cd to load.  I;ve tried using both of my cd drives, but to no avail and still get pretty much the same msg after I select the "boot livecd or install linux" option:

Decompressing Linux... done
Booting from the kernel

[32.11117] PCI: Cannot allocate resource region 2 of device 0000:01:00.0
[32.11157] PCI: Cannot allocate resource region 0 of device 0000:02:00.0
[32.11211] PCI: Cannot allocate resource region 2 of device 0000:01:00.1

And it just freezes right there.  I know I've been asking the same question about the same problem a lot and for a long time, but is there any new info on bugs that might cause this and workarounds for them?  Or does anyone maybe just have a fresh suggestion on what I could do?

I've formatted and deleted the master boot record countless times.  Nothing.  Downloaded every possible alternate CD.  Even the 32 bit versions and still nothing.

What do you think?
Any ideas?

Thanks a million,
Douglas

---

