---
title: "Help with installing FreeDOS on second partition"
date: 2015-08-25
forum: Any Other OS
---

### Post by KayeNg on 2015-08-25
My apologies if this is not the right forum to ask this question.

Hi! 
 
First partition, drive C:, of hard disk is Windows 7.  Second partition (50MB), drive H: , is for FreeDos.   
 
I downloaded the FreeDos iso file "fdbasecd.iso", mount it on a virtual  drive, installed it in the second partition ( drive H: ).  The files are  in H:\FDOS, not in the root directory H:\.  Is this ok? 
 
Downloaded EasyBCD 2.3 Beta build (because 2.2 does not have FreeDOS OS as an option to include in the boot menu). 
 
Managed to add FreeDOS in the boot menu, but when I try to boot FreeDOS,  I get what seems like the GRUB boot manager saying something which I  forgot.   
 
I cannot boot FreeDOS. 
 
Any ideas? 
 
Thank you for your time.

---

### Post by ajgreeny on 2015-08-25
I can not help with your specific problem but I think you will need to give us much more detail of what you actually did and also what you want to end up with, as I am a bit confused about your goals in this whole installation.

I have also moved the thread to the "Any other OS" section as it has nothing to do with Ubuntu.

---

### Post by KayeNg on 2015-08-26
Hello there, I thought my original post was already clear enough.

This is the way my computer is set up:

First partition = Windows 7
Second partition (50 MB only) = Supposed to be for FreeDOS
Third partition = currently storing data (documents, spreadsheets, pictures, music, videos)
Fourth partition = Lubuntu
Fifth partition = Linux swap

I guess my first question would be:  Is it possible to install FreeDOS on the second partition?  If the answer is yes, then this is what I did:

I downloaded the FreeDos iso file "fdbasecd.iso", mount it on a virtual   drive, installed it in the second partition ( drive H: ).  The files  are  in H:\FDOS, not in the root directory H:\.  Is this ok? 
 
Downloaded EasyBCD 2.3 Beta build (because 2.2 does not have FreeDOS OS as an option to include in the boot menu). 
 
Managed to add FreeDOS in the boot menu, but when I try to boot FreeDOS,   I get what seems like the GRUB boot manager saying something which I   forgot.   
 
I cannot boot FreeDOS. 
 
Any ideas? 
 
Thank you for your time.

---

### Post by oldfred on 2015-08-26
I think in the old days DOS only booted from first partition, but normally DOS & Windows use the boot flag to know which partition is bootable. Normal boot is BIOS -> MBR -> PBR where PBR is partition boot sector with more boot code. And MBR really just finds partition with boot flag.

If you move boot flag to DOS partition does it boot? If using a Windows type boot loader.
Windows has to have boot flag to directly boot, for repairs to the NTFS partition or to reinstall.
But grub does not use boot flag, and just looks for Windows boot files, so grub can boot a Windows that has boot files, but not boot flag.

I have seen this entry, do not know if freedos would be identical or not:
```
 menuentry "Msdos 7 (on /dev/sda2)" {
set root='(hd0,msdos2)'
chainloader +1
}


```

Chainloader entry then is like MBR -> PBR and expects more boot code in PBR. But does not require boot flag.

Shows Vista, but all BIOS boot
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

---

### Post by KayeNg on 2015-09-01
Hey oldfred, I'll just copy-paste my question from another forum.  My main problem is number three (3), but if you could answer 1 and 2, that would be great.
--------------------------------------------------------------------------------------------------------------------------------------------------

I sort of took some tips here:
[http://marc.herbert...._removable.html]("http://marc.herbert.free.fr/linux/freedos_no_removable.html")
but I also had to use the beta version of EasyBCD (which is EasyBCD 2.3)  as it has FreeDOS among its list of Windows operating systems.

Now to my FreeDOS problems. 

1.  When I boot into FreeDOS, it almost always asks me to enter the date and time.  Is this normal?

2.  I can run an old Clipper program but the program has to be in the  same drive/partition as FreeDOS; I cannot access other drive/partition  when I'm in FreeDOS.  Is this normal?  

 3.  When I'm using the Clipper program, I can print just fine.  But  I cannot enter data.  I get the "DOS ERROR 4", something like that.  When  running the Clipper program in command prompt in Windows 7 and I get  the "DOS ERROR 4", all I have to do is edit the autoexec.nt and config.nt  in windows\system32.
 

 By the way, I installed FreeDOS on the second partition in which I  assigned the letter D: .  I used the TEXTINST.EXE which is in  FREEDOS\SETUP\INSTALL (of the freedos iso file) to install.
 

 Upon running TEXTINST.EXE , I typed \FREEDOS\PACKAGES as the  source, and D:\FDOS as the target or destination.  Is this the right way  to do it?
 
 Thank you so much for your time.

---

### Post by oldfred on 2015-09-01
I have not used FreeDOS, just trying to remember years ago with old DOS.
I know back then I could mount d: drives. But you may need other FAT partitions.

---

### Post by sudodus on 2015-09-02
If you want to play old DOS games, dosbox might be a good alternative :-)

[www.dosbox.com](www.dosbox.com)

---

### Post by KayeNg on 2015-09-02
Hello, not really into games at the moment.  I need to run FreeDOS as a separate, complete OS, nothing to do with Windows or virtual machines, because:

1.  I don't like Windows.  Just recently my desktop computer was rendered unusable because of the win/sality virus.

2.  I don't have time yet to create or update our business software. Currently the program can only run in Windows command prompt, or FreeDOS (if I can figure out the config and autoexec problems as stated in my previous post).

If anyone knows how to solve my config and autoexec problems, please help!

Thank you for your time.

---

### Post by oldfred on 2015-09-02
I did not remember clipper. 
[https://en.wikipedia.org/wiki/Clipper_%28programming_language%29](https://en.wikipedia.org/wiki/Clipper_%28programming_language%29)

But reading that brought back memories. I originally used dBase II to create budgets since the spreadsheet program in DOS (SuperCalc?) could not then merge sheets. Updated to dBase III, then IV. But eventually migrated to MS Access. Partially since I wanted to learn more about SQL and possibly since Windows made it difficult for vendors to write software for its gui, and dBase V early versions did not seem too good.

But it really is time for you to consider updating your software.

---

