---
title: "[SOLVED] Recover NTFS files from ext2?"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by hung0702 on 2007-12-26
I've made a terrible mistake. Out of negligence, I accidentally installed Gusty in my Vista partition rather than my old Ubuntu partition. I then reformatted the old Ubuntu partition to see if I could install Windows there and use recovery program to recover the NTFS files in the other partition; it wouldn't install. I'm extremely hesitant about booting Gutsy in the Vista partition.

I need, or at least I think I need, a bootable CD that will allow me to recover the NTFS files from the newly formatted ext3 partition and put it onto an external USB HDD. I guess I could throw the drive in another computer and use a standard recovery program if worst comes to worst. I need to recover about 150 GB. about 2/3 of that is movies and music that I can live without, but the rest are family photos, and I just can't bear to lose them. 

If you need my computer information, it's an [_**HP m7657c**_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883107508"). &#8592; Link

Backstory: I couldn't update openoffice.org, and I couldn't reinstall it so that it would update, and it was unusable otherwise. In my typical stubborn manner, I decided that it would be easier to reinstall Gutsy and see if it would update. But when I went to choose the partition, I&#8212;for some self-loathing reason&#8212;assumed that the Ubuntu partition was the third drive on the list, despite being fully aware that my Vista is on sda3. Super stupid. And on Christmas, too.

Here's a graphic representation of the drives
_____Several days ago_______Early Yesterday_______Late Yesterday_
_sda1______Swap________________Swap______________Swap_
_sda2______Gusty________________Gutsy______________Blank_
_sda3______Vista___&#8592;___Recover______Gutsy______________Gutsy_
_me_______:)________________:confused:_____________ :cry:

Hope the rest of you are having Happy Holidays!

---

### Post by jonmartin on 2007-12-26
Ouch, that doesn't sound good. I don't know of any tool that will actually do that. Because you have installed over the windows partition lots of you old data may actually have been overwritten. But on the other hand, the installation may only have overwritten unimportant windows system files that you can reinstall anyhow and left your personal documents alone. All I can say is good luck!

---

### Post by LowSky on 2007-12-26
happy holidays, but just so you know you formatted your vista partition, and for almost all purposes its gone. When you installed Ubuntu it erased the NTFS partitoin and create a EXT3 partition over it. Sorry buddy but there is almost nothing you can do but try to find one a company that does disaster recovery of hard drives, and see if they can get to the info... it will cost you alot of money, I've heard it can cost into the thousands!!!

---

### Post by Mithrilhall on 2007-12-26
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Also, if you can find a Winternals ERD Commander disc you should be able to recover some stuff. I've wiped a NTFS partition once and installed Linux on top of it and was able to recover about 95% of my files I needed.

---

### Post by hung0702 on 2007-12-26
But isn't it the same as formatting an old NTFS partition into an new NTFS partition? Sure it's supposed to write a new partition over it, but somehow recovery programs can recover data from it. 

Also, didn't this happen to people when Windows switched from FAT32 to NTFS? I'm sure people had problems then and I'm sure someone found a way for that solution. I guess I'll just keep looking around.

---

### Post by hung0702 on 2007-12-26
Mithrilhall, I'm sorry I missed your post. It looks very promising. I don't know how to say this, but I'm glad someone else had the same problem as me! Please don't take it the wrong way!

---

### Post by hung0702 on 2007-12-26
Could I ask you exactly which version of the Winternals you used? Will it work with Vista stuff?

---

### Post by Jerry N on 2007-12-26
Like I said to the last guy in your situation - just restore all your essential files from your backups.

There are two kinds of computer users, those who back up their files and those that haven't experienced a major data loss yet.  

Jerry

---

### Post by Mithrilhall on 2007-12-26
It doesn't sound like he has any backups, so why bother suggesting that he use his backups?

The version I used was Winternals 2005. I recovered almost all of my family photos, mp3s and other files. I would think the 2005 version of Winternals would work since it is the same file system (NTFS).

---

### Post by Mithrilhall on 2007-12-26
I haven't tried any of these links but here ya go...


[http://www.keshzone.com/2007/11/new-links-for-winternals-erd-commander.html](http://www.keshzone.com/2007/11/new-links-for-winternals-erd-commander.html)

P.S.

Don't give up. You should be able to recover some of your data.

---

### Post by hung0702 on 2007-12-26
I'm assuming you had an NTFS partition somewhere on your old HDD when you were trying to recover it. Unfortunately, all of mine are ext3 and thus ERD Commander won't work. It starts booting up, but then fails before anything really loads. It gets to the XP-like bootup screen and as soon as the little progress bar make a single passover, a BSOD appears. It says I should run CHKDSK /F. I've tried using the command prompt from the Vista DVD and it says that it can't because the disk is locked.

---

### Post by Mithrilhall on 2007-12-27
Have you tried out Hiren's BootCD? It should have plenty of tools that'll give you a hand.

I'll explain what I did when I wiped my NTFS partition.

I was screwing around with a bunch of different Linux distros at the time. I had 2 physical hard drives in my computer; 1 with Linux and one with XP. I was installing a Linux distro at the time and I was watching a movie on my other computer and wasn't really paying attention to the prompts and installed a Linux distro on top of my XP install when I wanted it on my Linux drive.

Needless to say I was pissed. I ended up installing XP back on the drive and I used the Winternals disc to get back my data (I'm sure reinstalling Windows back on that drive didn't help with my data recovery). I ended up getting most of my data back.

---

### Post by hung0702 on 2007-12-27
I see. I think winternals needs some core components from Windows in order to work. I'll try installing XP on the old Ubuntu partition and see if it'll recover the other one. But, wait, let me get this straight: you reformatted the drive back to NTFS!? So I can reformat it back to NTFS and use some other NTFS Recovery bootcd that doesn't require any Windows components? I've been curious about whether or not that would wipe my data completely clean or not, but if it worked for you then I'll try it. Could you please confirm or deny anything above?

---

### Post by hung0702 on 2007-12-27
I tried Hiren's Bootcd but the drivers won't load. Perhaps it is looking for drivers on the HDD that aren't there. EXTCD.sys loads, but pretty much nothing else. None of the SCSI drivers work either.

---

### Post by psusi on 2007-12-27
Ubuntu CAN'T be installed to an NTFS partition.  If you are saying that you reformatted the partition to ext3, then installed Ubuntu, then your files are gone.  Whenever you have files that you don't want to loose, you need to back them up regularly, or sooner or later, you WILL loose them.

---

### Post by hung0702 on 2008-01-20
So I finally got around to finding a computer with a spare SATA port and lo and behold, I recovered the data. All I did was install the drive as a slave, booted windows, let it recognize (technically, it didn't recognize, since My Computer wasn't showing the Ubuntu partition), rebooted, and used GetData for NTFS.

Conclusion: Worked. So if anyone is googling "how to recover data from an NTFS drive that has been formatted into ext3" and people tell you that there's a low chance of recovery, know this: BS! Worked for me!

---

### Post by Mithrilhall on 2008-01-21
I'm glad this worked for you.

Even if you format the drive and put a new OS on it, there is the possibility that you can get some of your data back.

---

