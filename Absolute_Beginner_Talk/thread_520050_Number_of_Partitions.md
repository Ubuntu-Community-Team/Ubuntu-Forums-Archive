---
title: "Number of Partitions"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by MAHINDRA87 on 2007-08-07
I just purchased a used Dell D610 laptop (with an X300 ATI graphics card)on which I plan to run Windows XP and Ubuntu. This is the first time that I am running Ubuntu so I need some help. 

How many partitions and sub-partitions should I run? The laptop came with a small 65MB DellUtility partition and the rest of the drive was the XP partition. I erased the XP Partition and re-installed XP in smaller partition and left a small space 9-9.5 GB for Ubuntu. 

Is that sufficient for Fiesty Fawn? Are there any other partitions and or sub-partitions that I should create? 

Any other suggestions?

---

### Post by brent113 on 2007-08-07
That is adequate.

What I did on my computer is allowed merely enough for linux (around 15 gigs with the software I chose to install) and then mounted the windows partition where I can store my music and videos so Windows can access it too.

You'll just need the main ext3 partition along with a swap partition (usually around 1Gig)

Next time, for the record, you can resize a partition without erasing it using the Ubuntu Live CD's GParted, or a more powerful version in the GParted Live CD at [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by cobrn1 on 2007-08-07
As brent113 says, you can use the ubuntu partition editor to to the editing.

Just give 1gig to swap and put the rest as the root (/) to install in. *gigs will be fine for feisty. Note that you'll be able to read data (but not write) from your XP partition from within ubuntu, but you can't read ubuntu's data from XP (without using extra software). Just a thing to bear in mind.

---

### Post by 5-HT on 2007-08-07
I'd suggest creating your own /home parition in addition to / and swap that will store all of your data-- it makes a reinstall much easier and you don't loose anything.

If your drive is recognized as /dev/sda, I'd suggest:
```

/dev/sda1 - Dell Utility (Primary)
/dev/sda2 - XP (Primary)
/dev/sda3 - / (root Ubuntu parition for system data, Primary, 15 gigs should be more than enough. I think Ubuntu takes up around 2 gigs after installation, but you should leave some room for installing more. )
/dev/sda4- Logical Parition
                 /dev/sda5 - Swap (depends on your RAM, but if you want to hibernate--suspend-to-disk--it will need to be at least equal to your RAM)
                 /dev/sda6 - /home (for all your data)
```cheers

---

### Post by MAHINDRA87 on 2007-08-07
I know that a partition can be resized but I chose to delete, format and re-install XP because the laptop was purchased recently and came with much of the usual excess software. 

I am now downloading the Alternate CD because a Sticky in this forum advises the alternate version when installing Ubuntu on a computer with ATI X**** series cards and my laptop has a Mobility X300 Radeon. 

I'll resize the XP partition lower when I install Ubuntu (does Ubuntu come with GRUB or GParted?) About the partitions, so if someone could confirm this for me, if all goes according to plan I'll have the 65MB DellUtility FAT partition, the NTFS XP partition, a 1GB swap partition (To swap what? And in what file format should it be formatted?), and the ext3 Ubuntu partition (the Home partition called '/'? Very unconventional to a Windows user)?

5-HT (or anyone else) could you elaborate about the extra partitions? And please bear in mind that I'm a full Windows user. Define every term that does not apply to Windows.

---

### Post by cobrn1 on 2007-08-07
okay...

Look up and download the GParted CD. This tool will allow you to graphically mess with the partitions.You'll need to burn the .iso to a CD. The live CD has this tool, but you're using the text-based one, and that's a nightmare to work with, so this is better.

Now, when you've booted that cd up you'll want to set up the partitions something like this:

no1 - NTFS - XP (resize it if you want to make room, or leave it, it doesn't really matter...
no2 - FAT -  DellUtility
no3 - ext3 - / (this is the root partitons, where linux will be installed)
no4 - make this into an extended partition with 2 logical drives:
extended1 - ext3 - /home
extended2 - linux swap - swap (1 gig)

THe swap partition is formatted as linux swap - it is used like the page file in windows, to swap things out of the RAM. / is the root directory from which everything else spans. you can have /home in / (root's) partition, or on a seperate one. If it's seperate it allows you to reinstall much more easily as you won't loose your personal data.

/ is sort of like 'My Computer'. /mnt is where you'll be able to see all the devices/harddrives/partitions, hovever, note that partitions are refered to as /dev/sda*number* (or /dev/hda*number*.

EDIT: both CD's come with GRUB, at the end of the installation of ubuntu you'll be asked if you want to install it to the MBR - say yes.

---

### Post by MAHINDRA87 on 2007-08-07
I'm beginning to see the light.

I'll download GParted and use it before I install Ubuntu. The distribution will be something like this: 

1) Windows XP (NTFS) - 63-65 GB
2) DellUtility (FAT) - 65 MB
3) / (ext3) - 9 GB
4) Two part extended partition:
*** a) /home - 1 GB
       b) Swap - ?

Any more advice? How to deal with the notoriously nightmarish command line alternate CD perhaps?

---

### Post by cobrn1 on 2007-08-07
Not really - the text-based installer is actually really easy to use, and now that you've set up the partitions the really hard bits done. In the text installer you will still probably have to tell it where to mount the different partitions, but that should be easy enough, as you know which is which... Don't worry, it's much clearer than it sounds.

Also, if you get any problems mounting the windows partition to /windows (I think it tries to mount it there) just change that to /mnt/windows and it'll be fine...

Otherwise it'll be fine. Just read all the info carefully and it should be simple. We're always here (well - i'm prob going to head off to bed some time soon, but...) so if you have anymore probs just fire away...

Good luck! :D

---

