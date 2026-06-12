---
title: "Windows boot problems (dual boot with ubuntu))"
date: 2012-11-20
forum: Any Other OS
---

### Post by iowabeakster on 2012-11-20
I don't know where else to ask this.  So I'll try here.

Wife's computer: Asus B43S laptop (intel i5)
OSs: Windows 7, Ubuntu 12.04 (dual boot from grub)

I am trying to troubleshoot.  And I can't figure out if this is a hardware issue... or a bootloader issue... or what.

...history below... (skip to last paragraph for actual questions)

The computer dual-booted both OSs fine since april.  A week or two ago.  Things started to go wonky on both OSs.  Ubuntu would sometimes hard-freeze after loading the desktop.  I could not get to a tty (no keyboard, no mouse).  A hard shut-down was required.

When windows was booted, a error would often say that Windows had not shut-down properly (start-up repair would then run).  This happened even if Windows had acutaly been shut down properly. When running, sometimes the computer would instantly crash and fully shut itself off.

Sometimes when powering on, grub would not come up, the BIOS screen would not come up, the Asus splash screen would not come up... nothing... the screen would not even turn on (not just black... but did not turn on at all).  Only some dummy lights would come on with the fan.  Repeated cycling of power will randomly get the computer to boot to grub (and then to the problems above).

The problems are intermittent.  Sometimes it boots fine (especially if it has been running very recently).  I can't figure out a pattern to reliably reproduce the issues, or reliably get it booted.

So, I decided to restart fresh.  I restored Windows from the "factory fresh" restore DVD's that I made on the first day she got the computer.  I reinstalled Ubuntu (which she uses for everything but Netflix).  updates... yadda...yadda...  Everything worked fine for about 24 hours.  Then all the above started again.

I reinstalled Widows for the second time, I have not reinstalled Ubuntu again.  It is still having boot errors as above (even with no grub anymore).

I am fairly sure that it must be a hardware issue.  But I want to try everything before we send it off.  With an intermittent issue, and with my luck, they won't be able to reproduce it at the repair facility.

Is there something in the windows bootloader that is retained when a restore from DVD's is done.  Is the bootloader completely wiped and reinstalled fresh from restore DVD's?  I have no idea how windows works (or the restore process).

---

### Post by oldfred on 2012-11-20
I am assuming it is BIOS/MBR not the newer UEFI/gpt?

Does Disk Utility, click on drive and does Smart Data show any issues with hard drive?

Have you run chkdsk in Windows and e2fsck in Ubuntu. Hard shutdowns can cause issues with data on drive. 

If forcing Ubuntu down remember the elephants first.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

    
But since it is both systems, it does sound more like a hardware issue.

How Windows boots/ multi-boots. And really any BIOS/MBR system but grub2 does not use PBR just MBR. Longer article but pictures useful.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


[       ]("http://www.multibooters.co.uk/multiboot.html")
 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by iowabeakster on 2012-11-20
It is BIOS.

I am running some Windows system tool to check for HD errors  (looks like this going to take a while).  I am not familiar with Windows or its system tools. 

I ran a memtest from grub the other night (for a couple hours at least).  No errors.

Ubuntu in not installed at all right now (we are all prepared to send it in for service).  So there is no ext-2,3,4 type file system partitions to test anymore.

I read the article about MS boot loading. I understand quite a bit more now.  But, I sill don't know if doing a system restore from DVD's will over-write the windows boot programs or just system files.

Good tip about hard shutdowns in Ubuntu. I couldn't get it to work on my desktop. It just kept on taking tons of screen shots.

After many attempts, I found I have to mash alt+printscreen+r+e (all 4 simultaneously) then i..s..u..b...

Thank you for the help and info.


--edit--

I just did some looking around in the BIOS set-up menus.  I guess the computer has UEFI (but UEFI option was disabled).  UEFI was also listed as the third option in the boot sequence options, but since it was disabled, it has never been utilized.  I will play with it and see...   

There was also some PXE ROM option, too. ?

---

### Post by iowabeakster on 2012-11-23
I've packed it to send to the Asus repair facility... marking as solved.

---

### Post by sdowney717 on 2012-11-23
> I reinstalled Ubuntu (which she uses for everything but Netflix

You can now run Netflix on Ubuntu using firefox and wine.
So you will be allowed to not deal with the dual boot just for Netflix.
It is working very well. If you setup wine and firefox first, then install the netflix - desktop, it will register all windows type firefox's to work with silverlight. Or you can delete hidden folder .netflix-desktop and when you run the Netflix app icon by clicking on it, it will reconfigure to do the same. Otherwise, you will get a firefox stripped of menus for netflix.

---

### Post by iowabeakster on 2012-11-25
> You can now run Netflix on Ubuntu using firefox and wine.


Thanks for that info.  That's going to make my wife very happy when she gets her machine back from repair.  

I gave up hope for netflix on ubuntu long ago.

Hopefully it runs on the integrated chip decently. The AMD video card in her Asus still isn't working with Ubuntu (I given up hope on that too).

---

