---
title: "help with grub"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-11-02
boot loaders keep adding boot flags to the first partition.

im trying to use grub to boot xp vista and os x. os x is on an idei hd and on a SATA hd i have..

XP
XP
Vista
Ubuntu

ive been having trouble getting all the OS's to boot friendly for a while and its not working. i intalled grub to the linux partion because it originally installed to the os x partition causing os x not to boot but everything else would. but after installing grub to the linux partition which is (hd1,6) everytime i boot something besides ubuntu the boot loader of the other os puts a boot flag on the first partition of whatever drive its on which breaks the whole thing again.

how can i keep the other boot loaders from adding a boot flag? its really anoying.

---

### Post by Supergoo on 2007-11-02
:)Hi there ! 

You using the same harddrive for all the os's ? or are you using  different Harddrives,

Please post your information about your system, I assume its a Mac what version of OSX are you running ? did you use Bootcamp to install XP ? Anything else you can think of , will help us try to help you out.  :)

---

### Post by uknowho008 on 2007-11-02
its on a pc

os x is on its own hard drive and all other os's are on there own SATA drive.

what else do you need to know? i know what the problem is, i just dont know how to fix it. everytime i try to boot to say... windows xp the xp boot loader sets a flag on the first partition so the next time i restart the computer goes to the first partition to boot instead of linux partition where grub is.

i uninstalled the vista boot loader thinking it was only the vista that was causing the problem and now i cant boot vista. i edited the grub menu and it says there is not such something or other. but xp and os x's boot loaders cause the same problem.

---

### Post by Supergoo on 2007-11-02
Thats a intresting problem, sitting down and thinking about it.nothing is coming to mind right now on how to fix it, but let me ponder on it and if I get a idea I will post it, I am sure there are people here on the forums that can help you, I know alot of them are smarter then me :lolflag:
I do not know , but just a idea could OSX be making things go funky ? I assume its a hacked version if you are running it without a TPM chip that is installed on all Macs, I had a problem something like this, and I installed Grub on harddrive with just Linux and added the other OS's and it worked great, justa idea, I am sorry I can not help you more, I will keep thinking on it, good luck

---

### Post by uknowho008 on 2007-11-02
its not just os x thats causing the problem. i wish it were. i might be able to install grub to the first partition of my SATA drive which "should" solve the problem of xp and vista screwing it up when i boot into them. but even if i did that, since os x has to be on its own drive at the moment os x is still going to be cause the same problem. and if i put grub on os x's drive then it will screw up os x's mbr and i really wont know how to fix that. im using uphuck 1.4a for the os x install by the way.

---

### Post by deusxechelon on 2007-11-02
I had a very similar issue (Only after messing with the boot trying to fix it, it destroyed it), the only way I was able to resolve it was by doing what I did in this thread:

[If you had grief with your alternate CD partitioning]("http://ubuntuforums.org/showthread.php?t=593377")

> I used the guided partitioning on my first attempt at Dual Booting XP and Ubuntu which ended up in a miserable and most unrecoverable failure (Boot Failure when I tried to boot both operating systems, windows recoveries and testdisk could not fix it) requiring me to wipe the drive and start over. Fortunately it was a fresh install so it was just a loss of time and not data.

If this happened to you and you still want to successfully dual boot heres what I did:

I used a liveCD that I had on hand which I use for recovery known as Parted Magic to delete the partitions left over from the disaster and installed Windows again. After that I loaded Parted Magic again and premade the linux partition and the extended swap partition.

So far so good? Good, put in the Ubuntu Alternate CD and when you make it to the partitioner, go with MANUAL. All you have to do here is input the same thing you did with GPARTED from Parted Magic (Irritating in text, I had no choice.. the ubuntu livecd wouldnt work for me) into this here gparted. Before you tell it to perform the actions, make sure Windows has the boot records ( B ) and the partition you want linux to go in is designated with Root ( / ).

After that sit back and enjoy ubuntu. I hope this helped somebody.
__________________

---

### Post by uknowho008 on 2007-11-02
hmm.. i dont think we were having quite the same problem. i think i might try puting a small partition right in front of os x to install grub too. i didnt really want to put grub on that disk though because i hope to have os x installed on the SATA drive as soon as possible. but that may never happen. i just dont know how that will effect booting os x. i dont want to clobber os x's boot loader unless i can just use grub to boot straight to the os. ughh...

---

### Post by deusxechelon on 2007-11-02
hmm, well if you say so. When I first installed ubuntu into a dual boot, it gave me the same problem, would work fine untill I booted windows and then Grub stopped showing up there-after unless I manually reset it. Sounded similar to me. Good luck then :D

---

### Post by uknowho008 on 2007-11-02
oh.. i guess i just had a hard time understanding your post. ill see if i can figure it out agian.

---

### Post by uknowho008 on 2007-11-02
i got it working now. i ended up making a small partition on the os x hard drive and reinstalling os x to the second partition. then i reinstalled ubuntu and added os x to the grub list. im not sure if the partition in front of os x made the difference or not but i think it did.

---

