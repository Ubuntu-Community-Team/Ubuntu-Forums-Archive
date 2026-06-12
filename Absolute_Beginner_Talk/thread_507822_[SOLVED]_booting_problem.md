---
title: "[SOLVED] booting problem"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-07-23
My Ubuntu 7.04 is working working almost perfectly except a  problem.Whenevrer I try to boot into Ubuntu the progress bar stops in the middle and open up a black screen where it checks the filesystem and other things.In the whole long list there is a line that goes "...hdb1 has not been checked for ..... days...".Then the computer  restarts  and Ubuntu boots normally.Where is the problem?

BTW,my system clock is not right.

---

### Post by mlentink on 2007-07-23
Tiotally normal behavior. Linux will check youyr filesystem automatically after a certain number of boots. 
Sort of making sure your pc is still in goood health

---

### Post by davidjmayo on 2007-07-23
> **mlentink said:**
> Tiotally normal behavior. Linux will check youyr filesystem automatically after a certain number of boots. 
Sort of making sure your pc is still in goood health

Just to confirm it's totally normal. This happens every 30 or so boots
Nothing to worry about

---

### Post by ryanVickers on 2007-07-23
And you'll notice if it ever does have a real problem, it will actually tell you what's wrong and wait for you to read it insted of windows which just quickly flashes something like this:
checking or fixing some files
checking or fixing some more files
checking or fixing some more files
checking or fixing some more files
1 or more files were checked or fixed

(or)

there was one or more unrecoverable errors encountered

:lolflag:

---

### Post by chatterjee on 2007-07-24
It may be a normal behaviour but it happens every time the machine is booted(not once in 30 boots).

The list is long and the screen disappears too fast to be wholly copied.But in the middle of the list it says something like...."fsck died with exit status....[FAILED]..." Why is it showing?There must be something wrong.

Thanks in advance...

---

### Post by candtalan on 2007-07-24
> **chatterjee said:**
> It may be a normal behaviour but it happens every time the machine is booted(not once in 30 boots).

The list is long and the screen disappears too fast to be wholly copied.But in the middle of the list it says something like...."fsck died with exit status....[FAILED]..." Why is it showing?There must be something wrong.

Thanks in advance...

You said earlier that your system clock is not correct. This may mean that your bios battery is down and some data items are not being retained. I do not know, but could guess that maybe the file check sequence relies upon something related to these functions?

---

### Post by chatterjee on 2007-07-24
May be.I've to replace the BIOS battery because system date also is incorrect.

---

### Post by ryanVickers on 2007-07-24
> It may be a normal behaviour but it happens every time the machine is booted(not once in 30 boots).

The list is long and the screen disappears too fast to be wholly copied.But in the middle of the list it says something like...."fsck died with exit status....[FAILED]..." Why is it showing?There must be something wrong.

Thanks in advance...
That doesn't sound good!  A check is normal, but it should only happen occasionally, and it should not have errors (unless something is wrong of course)!  I would look into why the filesystem is having a problem - all the data on the drive is currently at risk if you want my opinion!

---

### Post by w4ett on 2007-07-24
> **candtalan said:**
> You said earlier that your system clock is not correct. This may mean that your bios battery is down and some data items are not being retained. I do not know, but could guess that maybe the file check sequence relies upon something related to these functions?

I agree:  Replace your battery on the MOBO.   Then reset your bios setting to include the system clock.  This SHOULD fix the problem.  

The battery maintains power to the CMOS memory, which keeps your system motherboard bios settings (including system time) between bootups

---

### Post by mlentink on 2007-07-24
No It should not check at every boot. I hope you do have a recent backup, if not, backup NOW.

I'd advice to replce your CMOS-battery, check if that helps, but if not, run some diagnostics on the drive. I can tell you which ones off hand

---

### Post by chatterjee on 2007-07-24
Please reply in detail friends!It's really a cause of concern,:(I think.Which diagnostic tool should I use and how?What additional information do you need to thoroughly understamd the matter?

NB:The system didn't behaved that way for next two boot ups and I've done nothing about the problem!:confused:

Here is the log:
> Log of fsck -C -R -A -a 
Fri Jan  3 00:07:26 2003

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 0 files, 1/1161666 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00, 76:20/00, 77:20/00
  , 78:20/00, 79:20/00, 80:20/00, 81:20/00
  Not automatically fixing this.
/dev/hda6: 618 files, 196098/2062319 clusters
/dev/hdb7: Superblock last mount time is in the future.  FIXED.
/dev/hdb7 has gone 48046 days without being checked, check forced.
/dev/hdb7: 11/2611200 files (9.1% non-contiguous), 126003/5217100 blocks
fsck died with exit status 1

Fri Jan  3 00:07:38 2003
----------------

---

### Post by sexymomma on 2007-07-24
I too boot to black screen. I have an MSI 939 board, AMD 3800+ dual X2 CPU, X1300 ATI card, 1 gig RAM, 250Gig IDE hdd, 80 Gig hdd, Acer 19" widscreen Monitor. I had Ubuntu installed as dual boot on a partition on 80 gig IDE hdd along with windows, and I gave daughter the 80 gig, bought a 250 Sata hdd, installed windows XP Pro on 250 IDE hdd, and had an impossible time installing Ubuntu on the 250 Sata, I kept getting black screen after I clicked to install, no matter what vga resolution I chose, or safe graphics or even Cntrl-Alt-F1 and installed the fglrx driver that way. I did get Ubuntu to install in text mode when  I used a copy of the Alternative Ubuntu iso. But now Ubuntu is in the boot loader and I click to boot into Ubuntu and I still get black screen, even using recovery mode. Help :(: I don't know if Ubuntu prefers IDE  drives, but I have too much data to lose if I were to partition the IDE hdd in order to try installing onto that.

---

### Post by w4ett on 2007-07-24
> fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hdb5: 0 files, 1/1161666 clusters
dosfsck 2.11, 12 Mar 2005, FAT32, LFN

This is the problem...yoor BIOS clock is wrong......The FIRST Thing you need to do reset your system clock....it is not being maintained by the CMOS Battery, which probably means you need to replace your battery, OR you reset your BIOS WITHOUT resetting the clock.

We need to reset the clock BEFORE troubleshooting any additional issue.

---

### Post by w4ett on 2007-07-24
> **sexymomma said:**
> I too boot to black screen. I have an MSI 939 board, AMD 3800+ dual X2 CPU, X1300 ATI card, 1 gig RAM, 250Gig IDE hdd, 80 Gig hdd, Acer 19" widscreen Monitor. I had Ubuntu installed as dual boot on a partition on 80 gig IDE hdd along with windows, and I gave daughter the 80 gig, bought a 250 Sata hdd, installed windows XP Pro on 250 IDE hdd, and had an impossible time installing Ubuntu on the 250 Sata, I kept getting black screen after I clicked to install, no matter what vga resolution I chose, or safe graphics or even Cntrl-Alt-F1 and installed the fglrx driver that way. I did get Ubuntu to install in text mode when  I used a copy of the Alternative Ubuntu iso. But now Ubuntu is in the boot loader and I click to boot into Ubuntu and I still get black screen, even using recovery mode. Help :(: I don't know if Ubuntu prefers IDE  drives, but I have too much data to lose if I were to partition the IDE hdd in order to try installing onto that.

Please post a new thread...this is not related to the OP's  original problem/thread.

---

### Post by ryanVickers on 2007-07-24
> This is the problem...yoor BIOS clock is wrong......The FIRST Thing you need to do reset your system clock....it is not being maintained by the CMOS Battery, which probably means you need to replace your battery, OR you reset your BIOS WITHOUT resetting the clock.

We need to reset the clock BEFORE troubleshooting any additional issue.
Just out of curiosity, why would the little battery have anything to do with a boot/filesystem problem?  If this sounds really stupid, then please explain in *more* detail :)

---

### Post by w4ett on 2007-07-24
> **ryanVickers said:**
> Just out of curiosity, why would the little battery have anything to do with a boot/filesystem problem?  If this sounds really stupid, then please explain in *more* detail :)

For more detail:  The file system integrity is controlled in part, by the system file timestamps....fsck will run automatically upon approximately 30 days/bootups.....If the system clock is off you get file system errors due to files being 'timestamped" days or even years in the past (in the case of a bad battery or incorrect manual setup of the system clock) when the system clock is inconsistant  between filechecks.

---

### Post by chatterjee on 2007-07-30
Thank you very much,my problem was with the CMOS battery.I replaced it,changed the BIOS settings,saved it and the problem was solved.Thanks again for your kind assistance!

---

### Post by ryanVickers on 2007-07-31
> **w4ett said:**
> For more detail:  The file system integrity is controlled in part, by the system file timestamps....fsck will run automatically upon approximately 30 days/bootups.....If the system clock is off you get file system errors due to files being 'timestamped" days or even years in the past (in the case of a bad battery or incorrect manual setup of the system clock) when the system clock is inconsistent  between filechecks.

hm, I had no idea it was that important!  I thought it was mostly just for keeping the time, and that the time wasn't *that* important!  I'm just wondering about if this would happen if your system (ubuntu) clock isn't dependent on a file or the BIOS clock (like mine; it syncs up to servers overt the internet).

---

### Post by w4ett on 2007-07-31
> **ryanVickers said:**
> hm, I had no idea it was that important!  I thought it was mostly just for keeping the time, and that the time wasn't *that* important!  I'm just wondering about if this would happen if your system (ubuntu) clock isn't dependent on a file or the BIOS clock (like mine; it syncs up to servers overt the internet).

The problem is that before you O/S loads, the CMOS contols your system integrity, System Bus operations, Boot order and the like.  If the OS timestamp and different than  BIOS  memory time (the CMOS) this will at the very least force a FSCK with every boot, because Ubuntu sees an fault condition in the filesystem.

---

### Post by ryanVickers on 2007-07-31
Ok, thanks for all that, it makes sense now. :)

---

