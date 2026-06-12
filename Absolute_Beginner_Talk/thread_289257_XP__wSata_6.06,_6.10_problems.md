---
title: "XP  w/Sata 6.06, 6.10 problems"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Nation5 on 2006-10-30
I first used 6.06 on my old computer with Win98 SE.  I just followed all the directions and did all the auto partitioning and on the next boot, I was brought to the GRUB loader screen, no problems.
Now with my new computer, 250GB SATA, Win XP Pro, I had installed XP knowing that I would use 6.06 on this computer as well.  So only partitioned 150GB to windows and left 100GB unallocated.  When I went to use the Live CD, I installed with the option for the CD to use the remaining HD space and do it automatically, as on my previous system.  Something went wrong, and I couldn't boot, and I could no longer boot Win XP, and all my files were lost, (not much at the time, but still a pain in the butt to reload everything).
So I had to reinstall XP, by the way, 6.06 did not recognize my Ethernet so no updates were possible.
Now I have alot of files that I cannot afford to lose.  I downloaded the prerelease of 6.10 and tried it on my old HD's, while unplugging my 250GB.
The live CD recognized my ethernet so I was able to get internet, i was very happy.  So i decided to move on with the install. It got to 57% and stopped when the HD started making a loud, repeating click, and now that HD is shot I guess, (30GB).  Then I tried it on my 20GB, and that freezes on the initial boot screen everytime.
Now I just DL'ed the official 6.10 release and I am going to try it out on the 20GB HD again.
Any thoughts on why I've had the trouble with these?

---

### Post by ReaderRat on 2006-10-30
I don't know how many HDs you have (physicslly) installed on your system, but mixing SATA and PATA (IDE) drives causes some issues. Here is something on that:
[**Mixing PATA/SATA Drives**](http://ubuntuforums.org/showthread.php?t=204428)

---

### Post by Nation5 on 2006-10-30
Thank you for your reply.  I believe that when I first tried the install, (6.06), I had mixed HD's (SATA and PATA).  But what about when I isolated the installation HD by only having the PATA hooked up?  I just read somewhere here that burning the ISO on a fast setting is bad.  I have a 6 year old CD burner with a max of 8x I think.

---

### Post by ReaderRat on 2006-10-30
I burned 12 ISO copies, for friends & myself, at 52X and they are now coasters. When I got the burn down to 4X, most all discs were okay. Be sure you check the disc checksum . It is an option on the LiveCD. (BTW, it takes a while to check 'squashfs" file.)

---

### Post by Nation5 on 2006-10-30
Well, when I said that it froze during OS Boot, the progress bar that swings from left to right to left, completely stops, and nothing happens for a while.
On the first try of 6.10 pre-release it never stopped at all, and proceded to run the OS.  Both HD were Maxtor, just one was 30GB, and the other 20GB.
This may or may not matter, but one of the things I tried on the 20GB HD was with a Floppy Boot Disk, I erased all logical/DOS/etc. partitions on the drive, and it froze on the same spot as before.  Thanks again for the reply and the help.

---

### Post by Nation5 on 2006-10-30
I just tried to install Edgy Eft on the 20GB HD in question.  I performed the Checksum.  Passed.  I rebooted and it stalled in the same exact spot as it did with the previous version.  When the Ubuntu logo starts and it has the progress bar moving from left to right and back.  It goes all the way right, then all the way left, then 2 notches back to the right and freezes.  About 5 seconds of activity.
Did i just ruin 2 HD's by trying to install this?  Or did they coincidentally go out while doing the same thing?  Or is there something cool that I don't even know about?

---

