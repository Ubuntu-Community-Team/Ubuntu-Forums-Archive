---
title: "I NEED HELP! how to restore the Apple EFI!"
date: 2009-06-19
forum: Apple Hardware Users
---

### Post by jjrecort on 2009-06-19
Hello..

I wanted to give a try to Ubuntu on a new Macpro.

I installed Ubuntu in a second disk without any problem
Mac is booting with Ubuntu and DVD (MACOX or LiveCD)
BUT IS NOT BOOTING/RECOGNISING the MACOX disc
I have formated and reinstalled the MACOX again on the disck and nothing
I have take out the Ubuntu HD and still nothing.

I need to restore the original Apple EFI to have the computer back to it's original state

it's that possible? or I have "bricked" the macpro forever?

I installed Ubuntu thinking that will not damage the hardware!

thanks in advance!

---

### Post by jimv on 2009-06-19
If you hold down the Option key while you boot, does it let you select the harddrive with OS X installed?

---

### Post by jjrecort on 2009-06-19
Nope!

I only get the ligth grey screen (like I'm on the boot chooser) but nothing appears
If I load the MACOS DVD it appears
if I connect the Ubuntu HD it appears (as windows)
if I load the LiveCD it appears (as windows)

but the primary HD (Macintosh HD) with the MACOX system is not appearing.

---

### Post by MikeTheC on 2009-06-19
*re-reads original post...*

*doh!*

Never mind. Sorry...

Alright, so a better question to ask (should have done so in the first place) is how did you go through the partitioning and setup of Ubuntu?

Are you sure you still have a viable partition table for Mac OS X, or that you have a viable Mac OS X install?

---

### Post by Richardcavell on 2009-06-20
This can happen if you have blessed a file or folder that the Mac cannot find at bootup. The computer wants to find the blessed file, and run it.  If it can't find it, it bricks itself.  Firstly, rearrange your disks so they are the same as they were the last time you got your computer to boot up successfully.  You probably want to have an OS X partition on your internal hard disk and to make that blessed.  That way, you can always boot.  rEFIt includes a 'refitblesser' program in your startup items that automatically blesses itself wherever it is installed.  So if you connect an external hard disk with rEFIt installed on it, and it boots from that, it will bless itself.  Then when you disconnect the external hard disk and try to boot, you can't boot anything at all.  The long-term solution is to ensure that rEFIt doesn't bless itself from anywhere other than your internal hard disk.

It's highly unlikely that you need to flash your EFI.  First, try rearranging all external hard disks and optical disks the way you had them the last time it worked.  The idea is to get into OS X somehow and bless an OS X partition that has a rEFIt /efi folder on it.

If all else fails, try booting with the P and R keys held down.

Richard

---

### Post by MikeTheC on 2009-06-20
> **Richardcavell said:**
> If all else fails, try booting with the P and R keys held down.

While holding down the Command and Option keys, btw. ;)

---

### Post by jjrecort on 2009-06-20
SOLVED!

first,

I already did the PRAM clear, with no results
just a note to clear that when I said ALT key it's option in the US keyboards

if it can help to others,
this is what I did to lead to the problem.

1. open a new macpro and complete the preinstallation
2. install a second brand new disk in bay 2 (no formated)
3. boot with LiveCD
4. Install Ubuntu 9.0.4 with the default settings in disk 2 (didn't touch anything on disk 1)
5. reboot.

what happened?

the Mac was not booting (blinking folder)
then,

rebooted with option key pressed  > ligth grey screen > nothing
rebooted with liveCD > LiveCD booted with no problem

what I did then?

1 reinstall again ubuntu this time modifing the booting info at the computer (can't remeber exacly the letters)
2.again I didn't touch the disk 1 (macosx)

result > the same behavior

third try

1. reinstall again Ubuntu from LiveCD on disc2
2. this time in the advanced booting I set the booting to the disk 2
3. again I didn't touch the disk one

results

voila!

1. Macpro booted from Ubuntu, great!
2. From Ubuntu I can mount and browse the disk 1 (macos x)

I tougth I was done!

then I restart pressing the option key to reboot from the Mac OS disk
and on the Boot manager I only got the Ubuntu HD marked as "WINDOWS"
no trace of the Disk 1 with MAC OS X

what I did:

1. booted with MACOSX DVD
2. the MACOSX DVD recongized the 2 discks! Ununtu and Macos
3. I tried to set the "startup disk" to the Mac OS X disk, but was not working
4. I Installed again the MACOX on disk 1 erasing the disk

and nothing!

5. I tried to physically take out the 2nd disk with ubuntu > same behavior

at this point Is when yesterday I wrote you in the forum.

and this morning some fresh idea come to my mind, and Voila! worked!

so HOW I SOLVED THIS.

1. booted with MACOSX DVD
2. Launch DISK UTILITY > the MAC OSX Volume is recognized and mounted
3. REPARTITION THE DISK
4. I Installed again the MACOX on disk 1


SOLVED!, now boots with the MACOS X!

now I'm finishing to update the MACOS X.. as soon is finished I will plug again the disk with Ubuntu and check if is still working and I have a neat dual boot.



Thanks for all,
And Sorry for my English if have lead to some confusion
I'm Catalan, so English is not my mother tonge.

---

### Post by jjrecort on 2009-06-21
Hi!

I already tested again booting with two disks and it works!

not as neat as a 20 years mac user will expect, but it works,

what are the glitches:

1.When you boot on MACOS X-- the ubunty disc will appear as unformated and launches "Disk Utility", just click ignore and that's all!

Solution: maybe there is a possibility to format the Ubuntu HD as other format recognizable by MACOX?


2. Ubuntu boots with a text screen with three options a kind of safe mode and memtest mode.. like windows.. if you press enter (for the default option) or wait the timeout everthing (seems) fine.

The funny thing is I have lost the Wacom control.. while with the LiveCD was working fine. but this is for another thread!

Thanks to all for their help!

---

