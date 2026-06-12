---
title: "uninstall ubuntu, stolen my bios????!!!!"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by gkabbott on 2007-07-15
No offence guys but Ubuntu is not for me. I have an acer 5100 that came with Vista. I hate it, and a  coworker gave me the Ubuntu cd to put on my d: drive in the partition with nothing on it. I don't like  Ubuntu, and to make matters worse Vista wouldn't load anymore. I tried to do a factory reinstall from the recovery partition in the harddrive but it won't get past update 12/13, I killed Vista by taking out the partition and putting Ubuntu on the whole 160 gig harddrive. At this point all I want to do is put the Windows XP disk I have in at startup and format the harddrive then worry about driver problems later. I went into bios and changed the priority to dvd drive first then harddrive, but all it does now is gives the XP disk a look, then proceeds to grub. How do I kill this grub thing and do an uninstall. I tried a few harddrive wipe programs and nothing will boot from startup except an Ubuntu CD. Help me kill Ubuntu. I can't even figure out this whole wine program that makes .exe files work. Please help me kill it, I know you guys like it, but I don't

---

### Post by tgm4883 on 2007-07-15
> **gkabbott said:**
> No offence guys but Ubuntu is not for me. I have an acer 5100 that came with Vista. I hate it, and a  coworker gave me the Ubuntu cd to put on my d: drive in the partition with nothing on it. I don't like  Ubuntu, and to make matters worse Vista wouldn't load anymore. I tried to do a factory reinstall from the recovery partition in the harddrive but it won't get past update 12/13, I killed Vista by taking out the partition and putting Ubuntu on the whole 160 gig harddrive. At this point all I want to do is put the Windows XP disk I have in at startup and format the harddrive then worry about driver problems later. I went into bios and changed the priority to dvd drive first then harddrive, but all it does now is gives the XP disk a look, then proceeds to grub. How do I kill this grub thing and do an uninstall. I tried a few harddrive wipe programs and nothing will boot from startup except an Ubuntu CD. Help me kill Ubuntu. I can't even figure out this whole wine program that makes .exe files work. Please help me kill it, I know you guys like it, but I don't

Hmm, is the Windows CD a pressed copy?  Many scratches?  I don't see any reason why you can only boot up the Ubuntu CD.  There is nothing on it that would make that possible.

---

### Post by gkabbott on 2007-07-15
boots to grub everytime, no matter what. xp, partition magic, and  even dban. even if someone could tell me how to get wine and how to use it maybe i could get dban to work. it's as if ubuntu has taken over bios. i would call acer , ubuntu or even microsoft but it is sunday and i am using this laptop in the canadian north in an oil camp with no disks or resources available. death to grub at startup, but HOW???

---

### Post by tuxcantfly on 2007-07-15
boot XP recovery disk, go into recovery mode (R), then type in: fixmbr

---

### Post by ReaderRat on 2007-07-15
Be sure the BIOS is set to boot from DVD/CD first. Then insert your XP disk and start it. WATCH what's on the screen. When it says "Press a key to boot CD", then press a key. Works for me every time.

---

### Post by gkabbott on 2007-07-15
i wish it was as simple as that  but it isn't. bios is already set to dvd first then hard drive. as for press esc, i wish. no F key, nor combo of F keys, or F keys with DEL or F keys with ESC works. It reads DVD drive for a moment then jumps right to GRUB no matter what bootable disk I use. How do I kill ubuntu and format the disks so grub is gone. getting ready to throw hard drive in a swamp and speak very badly of ubuntu as a bios virus if i don't figure out how to get my bootable abilities from startup back soon.  Let's try this from another angle. How do I get .exe files to work. I heard about wine and went to ubuntu links for it, every single url to wine failed. i went to limewire, got to 5/6 and stopped twice. It just isn't working out guys, please help me make a windows based .exe file work to re format and kill this. It's your baby, set me free, please. I guess I am a Bill follower, just can't stand Vista.

---

### Post by tgm4883 on 2007-07-15
Get the gparted live cd and wipe out ALL Partitions.  If that wont boot either, then boot up ubuntu live cd, install gparted with synaptic, and wipe all the partitions out with that.  

If you wipe out alll the partitions, then there is no way grub will be there anymore.

---

### Post by ReaderRat on 2007-07-15
> **tgm4883 said:**
> Get the gparted live cd and wipe out ALL Partitions.  If that wont boot either, then boot up ubuntu live cd, install gparted with synaptic, and wipe all the partitions out with that.  

If you wipe out alll the partitions, then there is no way grub will be there anymore.


Gparted site  =  [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by freebird54 on 2007-07-15
To get this straight - you can't boot ANY CD?  Or, you can't get the Win CD to boot?  Any chance you have a floppy drive in that thing?  If you do, get a Win startup floppy created off someone else's Win, and get the CD drive that way (to re-install Win).

Any install of Win will wipe out Grub for you.  That includes a temp install of Vista if necessary (!)

Wine, while it will run quite a few things, will probably not run enough of them easily enough to make you happy - so going back to XP is your best choice....

---

### Post by gkabbott on 2007-07-15
what is synaptic?  I am trying to get the cd now, only problem is that in my location i only have 1 dvd-r i can use, at least until i get home in a week

---

### Post by forestpixie on 2007-07-15
system> admin >synaptic - get to it once you've got the Ubuntu live cd running , and use that to get gparted

---

### Post by gkabbott on 2007-07-15
ok, i have the gparted.dat in a directory that i have no idea how to put on disk. I only have one dvd-r. what program do i use to get this program on a disk. please keep it simple, i have never used unix before.

---

### Post by gkabbott on 2007-07-15
please tell me how to get gparted to a cd, it's in iso format now. i really just want out of this now. i have no interest in reading how to use ubuntu. can someone give me the quick answer on what i do now with an unpackaged gparted fromsynaptic

---

### Post by tgm4883 on 2007-07-15
> **gkabbott said:**
> please tell me how to get gparted to a cd, it's in iso format now. i really just want out of this now. i have no interest in reading how to use ubuntu. can someone give me the quick answer on what i do now with an unpackaged gparted fromsynaptic

Did you download it from the website, or though synaptic.  My answer depends on your response.

---

### Post by reset3x on 2007-07-15
Try this.. [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12) If this doesn't work you can zero fill your drive with an installation disk for your hard drive... If you know who makes your drive go to their website and download an installation CD iso... Burn it and boot from the CD and zero fill the drive...

Good Luck!!

---

