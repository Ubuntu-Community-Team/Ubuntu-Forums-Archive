---
title: "white screen during installation"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by irvintang on 2007-03-11
White screen on mac powerpc G4! please help! 

--------------------------------------------------------------------------------

Hello, I've been trying to install ubuntu on my macintosh powerpc G4. but i keep getting a white screen after i hit enter, key in "live" or "live video=ofonly".

specs are single G4 powerpc processor with 866MHZ. 1.5GB ram with two hdds, a 60GB on with OSX loaded and a second one which i partitioned for ubuntu.

so i've got two harddisks on my mac and partitioned my second hardisk with 34.05GB of free space. i then inserted the ubuntu live cd (which i downloaded and burned) and restarted the com.

holding "c" i got into the ubuntu boot page which listed some instructions in plain white text on the top left corner of my screen. the first time i just hit enter. it said loading kernal or smth like that. then ramdisks. then my screen went blank.

i tried again but this time i typed "live" and hit enter. it did exactly the same thing. 

i then tried again with "live video=ofonly" but the same white screen appeared after it said "loading ramdisks".

Please help me! i really wanna get ubuntu working

---

### Post by grazie on 2007-03-11
First you need to establish whether you've created a bootable disk. Did the md5sum verify? At what speed did you burn the image? Can you read the CD from a boot OS? What do you see on the disk?

---

### Post by CountChocula on 2007-03-11
I am also having the exact same problem.  On my G4 733Mz.  I burned the disk at the lowest possible speed on my computer.  When I get to the yaboot prompt to load ubuntu. I type install and then the " video=ofonly "  and then it boots to a white screen. I also tried hitting tab to view a list of the other kernels to load and I tried viewing the help info.  I could not really understand how to boot one of the other kernels. ie. The powerpc kernel. does anybody know how to load the other kernels....

---

### Post by woopie49 on 2007-03-12
Hi irvintang and CountChocula

My experience with loading from the Live CD is that it takes maybe 3-4 minutes to load and you may have a blank screen for that time.

Just boot from the Live CD, when the initial screen comes up, hit enter and let it do its thing (assuming the CD is alright).

Ubuntu has to check what your hardware is and then configure itself to suit your Mac.

Once loaded, when you start exploring Ubuntu from Live CD, your experience using it may be slow because it is reading from the CD anything that it has not loaded.

However, once installed to HD, it has quite reasonable performance.  It is more windows like than Mac.  I'm still getting use to the GUI.

Ron

---

### Post by irvintang on 2007-03-12
I opened the disk in my osx and everything was just like one the disk image i downloaded. folders and files were there, but when i tried to verify it disk utility said it needs to be repaired but i can't click the repair option.

what do you mean by checking the md5sum? i created a partition thats free space, should i have made it ms-dos or mac extended?

i left the white screen there for about 10 mins but nothing happened. the drive didnt sound or feel like it was spinning either.

---

### Post by grazie on 2007-03-12
Before trying to install, there are a number of essential things that need to be checked and they're well explained [here]("https://help.ubuntu.com/community/BurningIsoHowto"). Verifying the md5sum ensures that what you've download is good and is explained in the notes. When the cd has been burnt successfully you can  boot with it and enter check at the boot: prompt. If you used OS X Disk Utility or Toast and also selected verify burn this step isn't really necessary. CD-R and CD-RW disks can't be repaired by the Disk Utility. Throw away bad CD-Rs, while CD-RWs need to be fully erased (not quick erase) then start again. Burning at the slowest possible speed is always recommended.

Leaving the unused disk space as free is exactly what is required. You can then begin your Ubuntu installation with confidence.

---

