---
title: "please help with install"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by copterfixer on 2006-04-17
I have tried to install ubuntu breezy badger. I first tried in a SATA raid0 array. Neither of the provided boot loaders would load. The rest of the install was great. But if the boot loaders dont load then i cant boot. It comes with instructions on how to boot through dos manually. I am a complete dos retard. So i dont want to go that way. Then i reformated and tried to install on a signle SATA drive. everything worked wonderfully. Gave me the message take cd out and system will reboot. Great im almost there. Get back to the Bios flash screen. Detect drives. Moving on . then finally i get to a boot disk failure. insert system disk to continue. HELP
This is driving me crazy. 
I want to run this software.
Please 
thank you 
joe

---

### Post by Sef on 2006-04-17
Could be you have a bad install disk.  I would burn another copy.

If you downloaded:

1) Did you md5sum check or download with bittorrent, which checks automatically?

2) Did you burn at 4x? Faster can cause burn problems.

3) Even if you got the disk from Ubuntu, it still could be bad.

---

### Post by copterfixer on 2006-04-17
[QUOTE=Sef]Could be you have a bad install disk.  I would burn another copy.

If you downloaded:

1) Did you md5sum check or download with bittorrent, which checks automatically?

2) Did you burn at 4x? Faster can cause burn problems.

3) Even if you got the disk from Ubuntu, it still could be bad.[/QUOTE]


I got my disk from ubuntu
i tried 2 different disks and even did that disk integrity check that you can select from the install menu.

---

### Post by jorn on 2006-04-17
What disk boot failure did you get?
Why can't grub find the boot-partition? Did you a manual disk setup, and at the end, did you let grub install automatic?

Jorn

---

### Post by copterfixer on 2006-04-17
[QUOTE=jorn]What disk boot failure did you get?
Why can't grub find the boot-partition? Did you a manual disk setup, and at the end, did you let grub install automatic?

Jorn[/QUOTE]

well i dont know 
yes i let grub auto install.
no i did all automatic set up
and i dont remember what failure i got.
it just said boot disk failure insert system disk to continue or something like that

---

### Post by jorn on 2006-04-17
Oh, I see.
This has nothing to do with your Ubuntu install.
That's the pc's bios trying to find a boot-string.
Go into bios and set the boot priority to start at your harddisk and see what happens.
Jorn

---

### Post by copterfixer on 2006-04-17
[QUOTE=jorn]Oh, I see.
This has nothing to do with your Ubuntu install.
That's the pc's bios trying to find a boot-string.
Go into bios and set the boot priority to start at your harddisk and see what happens.
Jorn[/QUOTE]
i did that. I set the hard drive i installed ubuntu on to be the priority boot. Ive tried removing all the other drives. Ive tried everything that i can think of. But yes it fails in dos as it tries to load the OS

---

### Post by jorn on 2006-04-17
Ok. I see you are not that "nooby".
I am slowly running out of ideas. Does the bios recognize the sata on boot-up.
Eventuelly press the "Pause" botton. 
Jorn

---

### Post by copterfixer on 2006-04-18
Yes I am just a linux noob. Not a pc noob. Anyway yes my bois does detect my sata drives. I again tried to install again 3 times tonight. Using both 64bit disc and 32bit disc my pc is a 64 bit system. Also tried several different discs. I dont get it and its really frustrating. Every time i try linux i get fed up and go back to microhell i mean microsoft. grrrr
Thanks for the help
if you have anymore ideas please let me know

---

### Post by Sandlst on 2006-04-18
This problem is a cinch to fix, I've had to do it myself-the bad part is, it requires a complete new install.  In the installer, when you are partitianing drives, you have to create a ~500 mb partitian, formatted as ext3, with the mountpoint /boot.  After you create this part., then create the raid partitians as normal, it should work.  Post back if you have any problems

---

### Post by copterfixer on 2006-04-18
Wow thanks I will give that a shot. But i will post back later in the week. I give up for tonight time to go shoot some people on BF2 but later this week I will for sure attempt that and give a reply if that works or not. Thank you 
P.s. Last few install attempts were not running raid0 simply installing on 1 sata drive.

Signed 
Really frustrated
:D

---

### Post by Sandlst on 2006-04-18
[QUOTE=copterfixer]P.s. Last few install attempts were not running raid0 simply installing on 1 sata drive.[/QUOTE]

ehhhhh once again I fail at reading.....in that case my suggestion probobly won't work........are you also running a hardware raid, by any chance?  I have one installed, but grub doesnt like it and wont boot with it enabled......but then again I was able to get a grub error, which you have not AFAICT so it might be an unrelated issue....regardless good luck!

---

### Post by copterfixer on 2006-04-19
Well i have never done raid before so i dont know the difference between hardware and software raid. Please explain if you do not mind. 
i have 2 WD 74 gig rapters that i would love to run raid as my op drive. My eventual plan is to run windows inside linux i know it can be done. I want windows for gaming and linux for everything else.

---

### Post by jorn on 2006-04-19
As far as I know hardware-raid is managed by the motherboard.
Software-raid is run by an appplication in the os.
In my bios I can switch raid on and off. That's hardware raid.
I wonder if you could find the solution here.
Grub does't work well under raid but have you disabled the raid when you installed on the single sata?
Jorn

---

### Post by copterfixer on 2006-04-20
Yes when i tried to install on one drive i moved my drive from the Raid sata port to a regular sata port then tried to install on one partition *one hard drive* during the partition set up.

---

