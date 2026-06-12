---
title: "HELP Windows partition gone, accidentally deleted mbr!!!!!"
date: 2011-10-18
forum: Any Other OS
---

### Post by DisorderlyCitizen on 2011-10-18
ok so i tried uninstalling grub as i wanted to delete my linux partition from my desktop pc (i got a laptop which is better suited for linux)

anyway i used easybcd for removing grub and restoring the windows bootloader. however i accidentally deleted the list of operating systems in easybcd. so i made a new entry for windows 7 but i didn't change any options or anything, saved, and then restarted. i guess this is what caused my problem. basically i cant boot into windows, tried reinstallting grub with boot repair to no avail, it gave me this output though:

[http://paste.ubuntu.com/712414/](http://paste.ubuntu.com/712414/)

also, after reinstalling grub, my pc still boots into the windows bootloader with the message that no operating system could be found.
i also cant seem to access the files on my windows partition, i cant see the partition when using the ubuntu live cd or the prompt from
the windows 7 repair disc. 

i'm a little freaked out right now, i'm worried that i somehow trashed my windows partition and that now
all my files are gone:(:(:(

please tell me that there is still hope....

---

### Post by heshoots67 on 2011-10-18
Try too go to search fifes

---

### Post by oldfred on 2011-10-18
Script says it cannot mount sda2, but shows it as NTFS and still there in partition table. Often a chkdsk from a Windows repair console works. You have to rerun chkdsk until there are no errors.
Your Windows boot/recovery is in sda1 and with recovery there an f8 may get you into the recovery console to run chkdsk on your main install. Some say from grub it is difficult as it is quick and you have to try many times. You can also restore a windows boot loader to sda and that should get you to the recovery console.

With multiple drives why not have an operating system on every drive and its boot loader in that drive's MBR. Then you have multiple ways of booting.

Did you make a Windows repairCD will in Windows? You should have a repairCD or Linux liveCD for every system installed.

Moved to other OS.

---

### Post by lkraemer on 2011-10-18
DisorderlyCitizen,
If you just deleted the Windows MBR, why not use SuperGrub to replace
the MBR ?
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Or if you search the forum, or use google, you can also find how to replace
the MBR with a Windows Install CD.

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)
[http://tips4pc.com/articles/computer%20troubleshooting/how_to_repair_a_damaged_boot_sec.htm](http://tips4pc.com/articles/computer%20troubleshooting/how_to_repair_a_damaged_boot_sec.htm)


lk

---

### Post by DisorderlyCitizen on 2011-10-19
thanks i will try out the links later!
 
i'm pretty worried that somehow my partition got so corrupted it is beyond repair, i really dont want to do a fresh install!!! because when i reinstalled grub yesterday from the live session, i looked to find that linux didn't list my windows partition in the drive manager.
 
why could this be?

---

### Post by DisorderlyCitizen on 2011-10-19
ok so i tried the above options without success. problem is i cant see my windows partition when i go into the command line so i cant cd into it to chkdsk it. the os list which pops up when you boot into the recovery cd didnt list any os either

this is the same with a live session, i can see the windows partition when i use the disk utility, but it says unknown and just lists the size of the partition, but when i explore the drives through the places menu in ubuntu, i cant see the windows partition.

i'm slowly loosing hope of ever getting this to work

---

### Post by mips on 2011-10-19
If I understand this correctly you want to only boot windows on this machine?

If 'yes' then boot up the windows install media, selct repair or whatever it is called these days. It should drop you to a dos prompt from where you can run 'fixmbr' or 'fixboot' can't remember what it is called.

---

### Post by DisorderlyCitizen on 2011-10-19
thanks for your reply, unfortunately, as said before, i cant see or cd into my windows partition, that way i cant chkdsk or fixmbr it. 

i think i need to get the windows partition show up again first, then i can fix it's mbr with the above options. then again, i might be wrong

that and that only is my problem right now, hope it's clear now;)

---

### Post by satanselbow on 2011-10-19
> **DisorderlyCitizen said:**
> thanks for your reply, unfortunately, as said before, i cant see or cd into my windows partition, that way i cant chkdsk or fixmbr it. 


Are you booting from the Windows media (CD/DVD) and which version of windows are we talking about?

> **DisorderlyCitizen said:**
> 
i think i need to get the windows partition show up again first, then i can fix it's mbr with the above options. then again, i might be wrong


Partitions do not have an MBR - disks do.
Deleting Grub / MBR will not directly destroy any partitions - only your ability to see them listed in a nice neat list. 

> **DisorderlyCitizen said:**
> 
that and that only is my problem right now, hope it's clear now;)

Clear as mud... which of the numerous differing instructions listed above are you actually following?

---

### Post by oldfred on 2011-10-19
If windows cannot see it then it may be a problem with the PBR - partition boot sector. Partition table says partition is NTFS, but PBR has to also be NTFS with links to the Windows file to boot ntldr for XP or bootmgr for Vista/7.

Windows normally requires boot flag on any partition you want to repair.

Testdisk can show PBR and NTFS keeps a backup which if valid testdisk can restore. Testdisk can also create a generic PBR, but I think it usually needs chkdsk & fixboot from Windows even after fixing a totally damaged boot sector. 

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)


Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by DisorderlyCitizen on 2011-10-19
> **satanselbow said:**
> Are you booting from the Windows media (CD/DVD) and which version of windows are we talking about?

I tried booting from the installation disk as well as the recovery cd. the installation disk didn't work either, i just got the option of installing windows. btw the version is windows 7 64-bit

> **satanselbow said:**
> Clear as mud... How did you go about deleting your ubu partition / grub and which of the numerous differing instructions listed above are you actually following?

well i wanted to uninstall ubuntu from my desktop because i got a laptop on which i use it. the pc is just for gaming:D

due to me using grub at that time, i first wanted to restore the windows boot manager with easybcd. unfortunately i got a little exited and deleted the os list in easybcd. i added an entry for windows 7 again, but i didn't set any options. i think that i have missed something, like linking that entry to the corresponding os or something...

ok i tried sgd, when i chose to boot windows, it just looped me  back to the menu where i choose the distribution. when i choose to boot linux it says something about a file not being found, i think it has something to do with stage1

i'm still trying out testdisk, so far it's still analyzing my disk....

---

### Post by lkraemer on 2011-10-19
Would this be of any help?

[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

[http://pcsupport.about.com/od/toolsofthetrade/ss/windows-7-startup-repair.htm](http://pcsupport.about.com/od/toolsofthetrade/ss/windows-7-startup-repair.htm)

[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

lk

---

### Post by DisorderlyCitizen on 2011-10-20
ok guys i have given up and done a fresh install of windows 7. i will never put two operating systems on one disk again, this is like the 4th time that the mbr or grub got messed up because of a dual boot install on same disk. 

anyway thanks again for all the help!

cheers

---

### Post by oldfred on 2011-10-20
If you have more than one drive I do recommend separate drives.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by DisorderlyCitizen on 2011-10-20
i wanted to use my pc with windows only, i have linux running on my laptop and i haven't been using linux on my pc so i wanted to uninstall it, which has turned into a fresh windows install:p

i think i will still use linux on my pc in the future as i think that my laptop won't last very long anymore...but until then i will avoid using two OS on one system altogether

---

