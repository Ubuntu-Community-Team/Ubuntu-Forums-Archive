---
title: "Help with install - problems with partitioning drive from LiveCD"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by VimesUK on 2007-03-04
Hello

I have installed the LiveCD and used the break=bottom command to edit the xorg.conf, so I can edit the device line from ATI to radeon. That way it will boot to the Gnome desktop using my ATI800 graphics card, all is well.

However I have stuffed up my 250GB hard drive (IDE) by editing the partitions as I didn't like how the auto partitioning was using most of the drive. I reckon that if I reserve around 60GB to use for ext3 drives and the rest as a one big FAT32 drive that would make me happy, I hope that Linux is happy too :)

But this is my problem I see from Gparted the following...

58.69 unallocated
86.00 unallocated
88.19 unallocated

I can't seem to figure out how to use Gparted to erase the entire disk so that first of all there aren't any defined partitions at all and then I can create my own as needed.

Can anyone please help with that, if it is possible.

Also as I would be manually doing this, I assume, could someone please suggest how that 60GB of EXT3 drive for Linux is best being 'split' to the correct proportions, like for swap etc....

Last point the then formatted (I hope) remainder of my drive as FAT32 how would I get Ubuntu to show that drive as last time I managed to install this (don't ask what happened) I found that I could not 'see' the remainder.

Then again I did try PC Linux and found that it was able to mount and let me read the three other NTFS formatted SATA drives that my system has and allow me to read the files from them.

Any help would be appreciated - many thanks :)

Please keep any advice really simple to understand :D

---

### Post by mac.ryan on 2007-03-04
Hi Vimes,

   I don't have all the answers to your questions, but here are the ones i can contribute to:

> **VimesUK said:**
> I can't seem to figure out how to use Gparted to erase the entire disk so that first of all there aren't any defined partitions at all and then I can create my own as needed.

The way it works for me, is to click on the bar displaying the HD partitions (the big one just under the icons "new", "delete", "resize/remove"). Then the clicked partition would become with a dotted border, and the button "delete" would become highlighted: click it and the partition is killed.

Please note that:[LIST=1]
[*]you can have "embedded" partitions (for example in the same extended partition you might have 2 or 3 logical drives). In that case click on the external border grouping the 3 drives...
[*]You have to click "apply" in order for changes to take effect.[/LIST]> Could someone please suggest how that 60GB of EXT3 drive for Linux is best being 'split' to the correct proportions, like for swap etc....Different people might come with different suggestions, and above all it depends from both your box and your needs. I would suggest however: 5 to 10 Gb for the installation + double the size of your ram as swap (unless you have a very big ram already) + the rest to be mounted as "/home". This way you will have your data in a safer place + it will be easier to reinstall linux without losing data if you will ever need this.

> Last point the then formatted (I hope) remainder of my drive as FAT32 how would I get Ubuntu to show that drive as last time I managed to install this (don't ask what happened) I found that I could not 'see' the remainder.Sorry, this is not 100% clear to me. Any partition in FAT or NTFS on the HD will be automatically seen and mounted when ubuntu boots up... but I am not sure this is what you wanted to know... :-/

Last points:[LIST]
[*]remember you can operate only on unmounted drives (right-click on the drive and click "unmount device" before starting gparted.
[*]I had once a problem with an external drive: it was pre-formatted in NTFS and no matter what I did, gparted was unable to buldoze it (ubuntu was keeping on seeing it as an active, healthy partition). I worked it around from WinXP.[/LIST]Hope this helped at least a bit. Best luck!

---

### Post by VimesUK on 2007-03-04
Your post is EXTREMELY helpful and thanks for taking the time to post and help me, most appreciated.

What I meant by 

> Sorry, this is not 100% clear to me. Any partition in FAT or NTFS on the HD will be automatically seen and mounted when ubuntu boots up... but I am not sure this is what you wanted to know... :-/

is that when I previously had Ubuntu installed I could not 'see' my other hard drives, unlike PC Linux where I could have those hard drives 'appear' on my desktop to easily access them.

Thank you again for you time and trouble in helping me.

EDIT: IIRC The 'rest' of my drive being formatted to FAT32 could not be mounted by Gpart, it had to be formatted in EXT3 and I wanted to keep it as FAT32 then I can access it via Windows as well as Linux.

---

### Post by mac.ryan on 2007-03-04
Hi Vimes, I am happy to know my post helped you. :)

I don't have the ubuntu Live CD with me, but one possibility could be that the FAT32 and NTFS drives are automounted only when you install ubuntu, and are not when you run it from the CD.

You could however try to manually mount the devices in ubuntu when running it from the CD. I am not an expert in commmand-line linux, but it **might** work like this:
[LIST=1]
[*]Open a terminal (on installed ubuntu this is under /Application/Accessories
[*]Type "mount /dev/sda1"
[*]Type "cd /media/sda1"
[*]Type "ls"[/LIST]Explanation:
[LIST=1]
[*]Open the terminal
[*]Mount the first partition on your standard HD with default/automatic parameters
[*]changes directory to the place where the sda1 is normally mounted
[*]show you the directory of that disk (so if you see your files, then it worked!!)[/LIST]Please note that if the above procedure doesn't work, this can depend from a number of issues (your first partition not being sda1, the CD user not having enough permissions to mount a device, etc...). But if it works... then you are sure you won't have problems.

Best luck with it! :)

---

