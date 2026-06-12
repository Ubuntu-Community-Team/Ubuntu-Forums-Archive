---
title: "Locking up at Ubuntu load screen"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Valcrus on 2007-02-07
Before I even start  my computer is:
Intel Pentium 4 3.00 GHz
1.00 GB of RAM
with 2 SATA Western Digital WD1600JS 160.00 GB HDs

I just got the urge to give Ubuntu a go.  So I took my computer with an extra hard drive in it and installed Ubuntu 6.10 Desktop on it.  The installation gave me a little trouble but I just chalked that up to the drive being NTFS.  So I reformatted it to fat32.  This time the install went all the way through with not problems.  Then I went back to following the dual boot direction I was using [http://www.ubuntuforums.org/showthread.php?t=179902]("http://www.ubuntuforums.org/showthread.php?t=179902")
  I tried to boot with just the SATA drive I installed to but at the screen with the loading bar the computer just locks.  I tried finding something on the boards but in all honesty everything I could find I just couldn't get to work (like I saw something about adding pci=nomsi but I'm unsure where to add that or if I even can in this case).  The only console screen I can get to is the GRUB screen that I get when I hit ESC just before the loading screen when I lock.  Could anyone give me idiot instructions that I might try.  I figure I've always used windows but I would really like to take a swing at Linux.  Any help would be greatly appreciated.

---

### Post by shareMenaPeace on 2007-02-08
If you manually partition than you need at least 1 ext3 and 1 linux-swap for the linux file system (NTFS FAT are windows).

---

### Post by Valcrus on 2007-02-08
> **shareMenaPeace said:**
> If you manually partition than you need at least 1 ext3 and 1 linux-swap for the linux file system (NTFS FAT are windows).


I think I may have confused myself.  I allowed the install to automatically format.  Like I said I am a complete noob to this.  I let the install go though on pretty much all the defaults.

---

