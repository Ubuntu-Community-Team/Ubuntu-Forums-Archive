---
title: "Ubuntu"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Fallen2 on 2005-12-23
I need to uninstall Ubuntu.  May I please have the steps in doing that please?  Also how do I know if I still Windows XP on my computer.  I hope it's not gone.  Please help.  THanx in advance.

---

### Post by Swab on 2005-12-23
Do you remember what options you selected during install? If you asked for the entire disk to be used for Ubuntu then XP is gone... otherwise it should still be there.   As for uninstalling Ubuntu.. just delete the partition it uses... and format it as NTFS or FAT32 or whatever you want.

---

### Post by Fallen2 on 2005-12-23
Honestly I do not remeber.  Is there some way I can check?

---

### Post by Swab on 2005-12-23
[QUOTE=Fallen2]Honestly I do not remeber.  Is there some way I can check?[/QUOTE]

OK, open up a terminal thats: Application, accessories, terminal
and type "df" into the terminal window then press enter... let me know the results... 

Also do you have a windows XP cd?

---

### Post by DevilsAdvocate on 2005-12-23
When the bootloader comes on, do you have an option for XP?  If not, boot into Ubuntu and under System open up disks.  If you still have an NTFS partition on your disk, you most likely do have XP still.

---

### Post by Fallen2 on 2005-12-23
[QUOTE=Swab]OK, open up a terminal thats: Application, accessories, terminal
and type "df" into the terminal window then press enter... let me know the results... 

Also do you have a windows XP cd?[/QUOTE]

This is what I get after I pressed enter:
[B]
jose@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             75459076   2040972  69585000   3% /
tmpfs                   254392         0    254392   0% /dev/shm
tmpfs                   254392     12588    241804   5% /lib/modules/2.6.12-9-386/volatile
jose@ubuntu:~$[/B]

I don't think I have a Windows XP cd.

---

### Post by Swab on 2005-12-23
[QUOTE=Fallen2]This is what I get after I pressed enter:
[B]
jose@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             75459076   2040972  69585000   3% /
tmpfs                   254392         0    254392   0% /dev/shm
tmpfs                   254392     12588    241804   5% /lib/modules/2.6.12-9-386/volatile
jose@ubuntu:~$[/B]

I don't think I have a Windows XP cd.[/QUOTE]

Well OK, do what DevilsAdvocate suggests to see if you have an NTFS partition.. but from the output above it looks like you don't and XP is gone.

---

### Post by Fallen2 on 2005-12-23
HOw can I get it back then?  Oh and I don't see anything that says NTFS.

---

### Post by Swab on 2005-12-23
[QUOTE=Fallen2]HOw can I get it back then?  Oh and I don't see anything that says NTFS.[/QUOTE]

You will have to get an XP CD and reinstall... or take this opportunity to forget all about windows :)

---

### Post by Fallen2 on 2005-12-23
Do I have to buy the Windows XP CD or can I just odownload it from somewhere?

---

### Post by Swab on 2005-12-23
[QUOTE=Fallen2]Do I have to buy the Windows XP CD or can I just odownload it from somewhere?[/QUOTE]

Hmmm... not sure, do you have a Windows XP sticker on your computer with a serial number? If so then I suppose you could borrow someone elses CD, not really sure of the legality of this... you'll need to check.

---

### Post by cstudent on 2005-12-23
Did you get any kind of restore disks when you bought your computer? What brand of computer is it?

---

### Post by Fallen2 on 2005-12-23
Not but I made some.  If I run those will I lose my DSL internet connection because I just got DSL about 3 months ago and the CDs are from about a year ago.

---

### Post by Fallen2 on 2005-12-23
[QUOTE=Swab]Hmmm... not sure, do you have a Windows XP sticker on your computer with a serial number? If so then I suppose you could borrow someone elses CD, not really sure of the legality of this... you'll need to check.[/QUOTE]

Yes, I have a Windows sticker but there is no serial number on the sticker if that's what your asking.

---

### Post by cstudent on 2005-12-23
[QUOTE=Fallen2]Not but I made some.  If I run those will I lose my DSL internet connection because I just got DSL about 3 months ago and the CDs are from about a year ago.[/QUOTE]


If you are saying you copied some Windows files to CD those won't cut it. You need to have an install disk of some sort for Windows.

---

### Post by Fallen2 on 2005-12-23
[QUOTE=cstudent]If you are saying you copied some Windows files to CD those won't cut it. You need to have an install disk of some sort for Windows.[/QUOTE]

I have an HP computer and I came with a program called HP Recovery which made recovery dics.

---

### Post by cstudent on 2005-12-23
[QUOTE=Fallen2]Yes, I have a Windows sticker but there is no serial number on the sticker if that's what your asking.[/QUOTE]

The sticker has a product key for the version of Windows that came on your machine. If it was a retail version, you could borrow another retail disk and use that product key. If it is from Dell or Sony or some such maker, you'll almost have to have the CD's that came with the computer to reinstall XP. If it is one of those, you might be able to get a replacement disk from them, but it probably won't be free.

---

### Post by Fallen2 on 2005-12-23
In thast case I will just stay with Ubuntu.  So now can you help me install WINE?

---

### Post by cstudent on 2005-12-23
[QUOTE=Fallen2]In thast case I will just stay with Ubuntu.  So now can you help me install WINE?[/QUOTE]

I did a google for HP Recovery and this site came up first. Looks like some helpful info, but don't know if it will get your XP back or not. You can also try HP's website for more on your computer. [www.hp.com](www.hp.com)

[http://www.pctechbytes.com/hprecovery.htm](http://www.pctechbytes.com/hprecovery.htm)

I've never used wine, so I wouldn't be much help there. If that's what you want to do, then start another thread in an appropriate forum section and ask for help with it.

Good luck and Happy Holidays to you!

---

### Post by DevilsAdvocate on 2005-12-23
Did you check under Disks for an NTFS partition?  

If there isn't one, you can probably use the HP recovery disks but you'll need the serial number.  There's usually a "Made for Windows" sticker on the front of your computer.  But, look around the computer and in back for another sticker w/ a bunch of numbers on it from MS.  Can you find one?

---

### Post by Fallen2 on 2005-12-23
[QUOTE=Swab]Do you remember what options you selected during install? If you asked for the entire disk to be used for Ubuntu then XP is gone... otherwise it should still be there.   As for uninstalling Ubuntu.. just delete the partition it uses... and format it as NTFS or FAT32 or whatever you want.[/QUOTE]

I figured out how to get my windows Xp back, now how do I delete and format the parition?

---

### Post by Swab on 2005-12-23
[QUOTE=Fallen2]I figured out how to get my windows Xp back, now how do I delete and format the parition?[/QUOTE]

You can do that from Windows once you have it installed again... you will need to open up disk manager and you should be able to do it from there.

---

### Post by cstudent on 2005-12-23
[QUOTE=Swab]You can do that from Windows once you have it installed again... you will need to open up disk manager and you should be able to do it from there.[/QUOTE]

I think we determined (and partially assumed) that he installed Ubuntu over top of his XP. It might be better if Fallen2 could tell how he plans on restoring XP.

---

### Post by Swab on 2005-12-23
[QUOTE=cstudent]I think we determined (and partially assumed) that he installed Ubuntu over top of his XP. It might be better if Fallen2 could tell how he plans on restoring XP.[/QUOTE]

Ah, good point :)

---

### Post by Swab on 2005-12-23
I think he has gone ahead and executed his recovery plan...

---

### Post by Fallen2 on 2005-12-23
All I have to do is re-parition that one thing for more free space and then I can restore my XP.

---

### Post by jbmalone on 2005-12-23
In my experience it doesn't work that easily by just using "that thing." 

Instead, you will need to format the disc.  After the format make three partitions.  One in NTFS, where you will install XP, one in FAT32 to store your files, and the last for Ubuntu.  Then install Windows, and after Windows is running, then install Ubuntu.  This is as long as you want to dual boot.  If you don't then just format and install Windows.

---

### Post by bscbrit on 2005-12-24
Yes, but he is also trying to recover his damaged XP.   I wouldn't want him to reformat the drive completely otherwise he might have more problems than he has now!:D

---

### Post by jbmalone on 2005-12-24
I didn't necessarily read it that way.  It almost sounded like he was going to repartition the drive and then install XP in that new drive.  I don't think that would work.  And, we don't know the last time he defragged, so that could cause some real problems maybe with his XP and Ubuntu installations.

---

