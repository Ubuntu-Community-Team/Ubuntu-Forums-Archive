---
title: "Can't resize NTFS partition!"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by miggols99 on 2007-03-30
When I try to resize my partition in qtparted it says:
> Filesystem check failed! Totally 123 cluster accounting mismatches.
What does that mean? I have defragmented the windows partition before.

---

### Post by freebird54 on 2007-03-30
Sounds like you need to run CHKDSK /F in Windows to fix allocation errors first...  I think there's a graphically accessible version too, but I can't get to the Win side while I'm typing! :)

It is a good idea to defrag more than once (I ran 3) before resizing... Win defrag is sometimes 'lazy', and gives better results on a rerun.

---

### Post by huygens on 2007-03-30
I don't know what it means, but it rings a kind of bell in my mind that would tell me to perform a scandisk under windows.
A cluster could be considered as the 'unit' (as in the smallest element) of your hard disk. A file is stored in one or more cluster. The cluster size may vary depending on your partition/disk size.

To take a well known comparison, you could think the hard drive as a bookshelf and a cluster as a compartment in the bookshelf. Each of this compartment can contain book 10 cm wide (for example) they can contain only one book. Books larger than 10 cm can be sliced into smaller parts each fitting in one compartment.
So, when you place a book 5 cm wide, it is occupying a whole compartment (and wasting 5 cm of space). If you place a book which is 22 cm wide, it will occupy 3 compartements (and waste 8 cm of space), etc.
For hard disk it is the same. A disk is divided in cluster of for example 4kB size. A file of 1kB will occupy a complete cluster, and so you have 3kB wasted. A file of 103kB will occupy 26 cluster and waste only 1kB.

I'm not sure what a cluster mismatch is, but I would guess that for example a file as been registered as using the next 4 continuous cluster, but is actually using only 3... Scandisk should be able to repair this kind of errors.

---

### Post by freebird54 on 2007-03-30
I knew there was a graphical equivalent - but I use WIndows so rarely now that it rarely f(&^*s up!

Scandisk is the one to run, then defrag a time or two - then retry the resize operations....

---

### Post by huygens on 2007-03-30
This is what I have found in the NTFSresize FAQ:
> [LIST]
[*][SIZE=+1]**What do "[B]Cluster** **accounting** failed",      "Filesystem check failed!" and "**cluster** **accounting** **mismatches**"       mean?[/B][/SIZE]      Ntfsresize makes a filesystem consistency check for extra safety before the real      resize operation and it refuses to make any modification to the filesystem      if it finds serious errors already present. This is done to protect you from      accident data loss due to the     imperfect state of your filesystem. In these cases you need to boot Windows and run      [chkdsk]("http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx")     with the **/f** (fix errors) command line option.     If chkdsk asks you if it should check the drive the next time you restart the      computer then answer 'y' (yes) then restart Windows **TWICE**. If you don't      specify the **/f** option or you don't reboot twice then chkdsk will not fix      the NTFS consistency problems. 
     You should also use at least ntfsresize version 1.13.0 and please note that      Windows occasionally won't repair the problems if you also have      [bad sectors]("http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html#badsectors"), hardware damages.[/LIST]Under Windows, you can right click on a hard disk and select properties. You then have a small window that is brought up and you got to the "Tools" tab. There you can run the scandisk/checkdisk thingy. It most probably will tell you that it will be run upon next Windows start. So just as the FAQ suggest it, restart Windows once and even a second time. ;-)

---

### Post by Gina on 2007-03-30
Yes, I found I had to defrag in Windows several times before the files were moved to the beginning of the disk (as well as dfragmented).  I also had to turn off the Windows swap file and Hibernate to remove immoveable files.

The errror certainly seems like lost clusters so yes, run a disk check prog to recover lost clusters and fix errors generally.  BTW Scandisk is not as thorough as CHKDSK run from DOS mode (command line at bootup) (or set to do it on restart) because Windows marks some files as untouchable and needs to run the check/repair before Windows itself is loaded.

---

### Post by miggols99 on 2007-03-30
Ok I managed to resize the partition. How do I install Kubuntu to the empty area?

---

### Post by deuchar1 on 2007-03-30
For the record - if you ever get a green block of unmovable data on your disk when trying to resize NTFS disable Windows' page file. It can cause problems.

---

### Post by huygens on 2007-03-30
> **miggols99 said:**
> How do I install Kubuntu to the empty area?

Launch the Live-CD (I mean you have to start your computer and boot on the CD). You will see Kubuntu loading directly from the CD (it is not touching your disk).
On the desktop, you will see an icon named "Install". Double-click it and follow the instruction. When it comes to partitioning, you should have the option to use the available free space.

---

### Post by miggols99 on 2007-03-30
Ok, it's all working now :) thanks.

---

### Post by c-breakdown on 2007-03-30
> **deuchar1 said:**
> For the record - if you ever get a green block of unmovable data on your disk when trying to resize NTFS disable Windows' page file. It can cause problems.

That sounds like my problem exactly.   Could you please elaborate on what you mean by disable Windows' page file?  I googled that and came up with crazy results since all the words are so common.  I would greatly appreciate your help.

> **Gina said:**
> Yes, I found I had to defrag in Windows several times before the files were moved to the beginning of the disk (as well as dfragmented).  I also had to turn off the Windows swap file and Hibernate to remove immoveable files....

I think the unmovable files are what is keeping me from installing ubuntu.  What do you mean by "turn off the Windows swap file and Hibernate to remove immovable files"?  I'd really like to try this too.

---

### Post by Bartender on 2007-03-30
I'm not sure deuchar meant to actually disable the page file.  Is that possible??  Anyway, the page file is Windows' equivalent of swap in Linux.  
If you've got a lot of RAM (at least 2GB) maybe you could do without a page file but most  dual-booters just run defrag several times and make do with whatever space the Windows install gives up.
No matter how many times I run defrag W2K shows a block of "unmovable" data out in the middle of the free space.  I don't know what that data is or if it's possible to shove it over towards the rest of the Windows data...
One way to get around that, but only if you're starting from scratch and using a genuine Windows CD, not a "Recovery CD", is to partition the drive from the Windows CD before installing  Windows.  I realize that doesn't help most people but thot I'd mention it...

---

### Post by huygens on 2007-03-30
> **c-breakdown said:**
> That sounds like my problem exactly.   Could you please elaborate on what you mean by disable Windows' page file?  I googled that and came up with crazy results since all the words are so common.  I would greatly appreciate your help.

I think the unmovable files are what is keeping me from installing ubuntu.  What do you mean by "turn off the Windows swap file and Hibernate to remove immovable files"?  I'd really like to try this too.

pagefile and swap are two terms for the same thing. You can deactivate them in Windows, however just perform the defrag and re-activate them after or you might not be able to use some of your application without it. And if you have less then 512MB, you might not be able to deactivate the swap completely!! But you could reduce it so if you sum up your memory and the swap you reach 512MB. That should be enough memory to perform the defragmentation.

So to deactivate it the page file, you need to right click on your "My Computer" icon and select properties. A window will appear. You should a "Performance" tab or something of the sort where you can select things like graphical effects, etc. There is one option there (you will have to look a bit around) for the page file. Deactivate it. Windows will try to warn you many times, but proceed anyway. You will have to reboot. After reboot completion, simply connect to your account and perform one or several defragmentation. After that, reboot to install Ubuntu. Once Ubuntu is installed. Do not forget to boot back to Windows and re-activate the swap.

As for the hibernating. I do not remember where it is set-up exactly, but I think that if you right click on your desktop and select properties, you will have a small window appearing. There should be a tab for the screensaver where you can modify also power saving parameters. Click to change them and somewhere in the new screen you shall be able to deactivate the hibernating I think. However, as I'm under Linux I cannot verify it...

---

### Post by c-breakdown on 2007-03-30
huygens you're my hero, thanks so much.  Once I turned page file off I was able to defrag those unmovable files the first time.  After that GPart Live CD made the new partition and I just had the ubuntu install put it there.  

Thanks everyone who helped me, it took me some time but thanks to the great support here I've got it going.  \\:D/

---

