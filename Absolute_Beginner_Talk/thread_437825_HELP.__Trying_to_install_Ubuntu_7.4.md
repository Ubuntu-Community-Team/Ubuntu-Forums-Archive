---
title: "HELP.  Trying to install Ubuntu 7.4"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by MarineMa6 on 2007-05-09
I have a P4 3.4ghz, 2gig ram, 2 IDE HDD, 1 Sata HDD, 1 IDE CdRom, 2 6800gt cards in  sli mode.  downloaded the Ubuntu 7.4 CD and ran a check against the cd to make sure the cd was good to go.  I booted  to the cool looking Ubuntu Live Cd screen and ran the install.  after i rebooted i keep getting "error loading operating system" i loaded it on the sata drive and in my bios i have the sata drive as my first boot device.  i have LBA set to auto because its either auto or disabled for my bios.  any help would be greatly appreciated as i want to try linux for the first time.

Thanks

Jay

---

### Post by Sef on 2007-05-09
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

---

### Post by MarineMa6 on 2007-05-09
yes did the checksum and burned at 2x.  also forgot to mention during the install with the partitioner i did the full disk format not just a partition of the disk.  also if i boot with the live cd i can see the boot drive with folders and files.

---

### Post by slibuntu on 2007-05-09
Well if he checked the CD after he burned like i think he did, the speed won't have made a difference

---

### Post by Cypher on 2007-05-09
Did you make any changes on the GRUB installation screen??

---

### Post by MarineMa6 on 2007-05-09
sorry new to ubuntu and linux.  no clue what grub is.  sorry

---

### Post by umarvlie on 2007-05-09
> **MarineMa6 said:**
> I have a P4 3.4ghz, 2gig ram, 2 IDE HDD, 1 Sata HDD, ....

I noticed you have 2 IDE HDD and 1 SATA HDD, when you ran the install, was the original disk you boot from the first IDE drive?

Did you try to boot from HDD1 of the IDE drives i.e. change the first device to boot from the master on the IDE?

---

### Post by MarineMa6 on 2007-05-09
no i'm trying to install ubuntu on my sata drive not my ide drives.

---

### Post by umarvlie on 2007-05-09
> **MarineMa6 said:**
> no i'm trying to install ubuntu on my sata drive not my ide drives.

I understand but if you originally booted from the IDE drives your master boot record (i.e. where you should boot from) might still be there and GRUB (the small program that should start then you boot) might be on the IDE drive instead of the SATA disk.

---

### Post by MarineMa6 on 2007-05-09
oh. ok.  hmm.  tough one.  i know i rebooted my pc wich originally had xp on the sata drive as my boot device.  then loaded the live cd.  then did the install and chose the sata drive full partition to use ubuntu and rebooted and thats what happened.  hopefully this helps with what i did.

---

### Post by hyper_ch on 2007-05-09
IDE and SATA is a problem... it keeps acting weird for me also... in the BIOS I set SATA to be first boot devices (among the harddisks) and it did install grub there... however it set the boot record to hd(2,2) or something like that... this would be ok if I'd have IDE as first boot devices... so I needed to alter that to hd(0,2) and it works now...

You may have to do the same :)

---

### Post by MarineMa6 on 2007-05-09
thanks but could you tell me how to do that in lay men terms since i'm 1 day new to linux.  thanks  Edit:  i also have my sata drive as my first boot device in the bios

---

### Post by umarvlie on 2007-05-09
You can start from the live CD and correct this. Only problem is i dont know where the SATA drive will be mounted ( i am at work and on a windows PC so i cant guide you through that part).

Once you know the mount point of the SATA drive (it might be /media/disk or something) you have to do following: (assuming you have only one Linux partition and it takes all of the SATA disk):

gksu gedit /media/disk/boot/grub/menu.lst

then look for the part similar to this:

> ## ## End Default Options ##

title Ubuntu, kernel 2.6.15-28-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-28-386
savedefault
boot

where you see the root (hd 1,0) or something like that it should read (hd 0,0) if it is not you can change that and save the file, then reboot and see if it solves your problem.

---

### Post by MarineMa6 on 2007-05-09
umm next noob question from me is how do i type in command and where do i save the file once edited.

---

### Post by umarvlie on 2007-05-09
Well, noobs are people that never learn, guess you are a newb rather :) until proven otherwise.

In the menu (top left) you go to Applications > Accessoiries > Terminal and click on that, there you type the command:

> gksu gedit /media/disk/boot/grub/menu.lst

It opens an editor window and you can see a save button so that is quite easy and window like, just make sure you find the location of the disk (mount point) first, otherwise it wont open the file but just creates a new file or returns an error.

(unfortunately cant help you there @ work atm and cant double check things, maybe some1 else can give you some hints on how to find it)

---

### Post by Ozeuss on 2007-05-09
go to Applications>accesories>terminal
that open the command line.
you type the commands there. "sudo" or "gksu" mean that you're running a command that needs administrator privileges (as is the case when you want to edit GRUB).
gedit is the name of the text editing program. when you run the command you open up the config file  in the text editor. when you press save it saves into its place.

note about the previous post- the command should correlate to where you're linux filesystem is installed- /media/disk or /media/disk1

---

### Post by Ozeuss on 2007-05-09
to see where the live CD mounted your installed ubuntu, you can open the "filesystem" folder, and the media folder. there should be a folder over there that points to your installed ubuntu.

---

### Post by MarineMa6 on 2007-05-09
Thanks to all for this much needed help..  i will try everything when i get home tonight.  i think that ubuntu running off a cd is freaking awesome.  once again thanks to all that have helped.

---

### Post by hyper_ch on 2007-05-09
actually when you boot from your harddisk and you see the grub menu... you can press "e" I think to edit the entries... have a look and read what's on the screen :)

Select the first entry and change this "root (hdX,Y)" to "root (hd0,Y)"

Maybe you have to test until you find the correct stuff :) but I think it should be hd0

---

### Post by MarineMa6 on 2007-05-09
ok i'm home now.  tried what was said and this is what i got "The folder contents could not be displayed error accessing 'file:///media/disk/boot/grub': File not found"

HELP

---

### Post by hyper_ch on 2007-05-09
Well, did you also try to boot from your harddisk?

---

### Post by MarineMa6 on 2007-05-09
yes tried booting and still same error

---

### Post by hyper_ch on 2007-05-09
well, did you edit the grub entries when booting from the harddisk?

When the grub screen comes you have to press a key for editing... I haven't done so in a long time but it says on the screen written... then modify the whole thing...

---

### Post by MarineMa6 on 2007-05-09
i don't get the grub screen when i boot to disk.  it goes directly to the error.  HELP

---

### Post by umarvlie on 2007-05-10
> **MarineMa6 said:**
> i don't get the grub screen when i boot to disk.  it goes directly to the error.  HELP


Means that the Master Boot record is not correct or not on the Hard disk you boot from (the SATA disk).

I would suggest you to try and boot from the IDE disk and see what that brings up as the MBR might be on the IDE Master rather than the SATA for some reason.

---

### Post by MarineMa6 on 2007-05-10
ok fixed it.  i had to unplug my ide drives.  going to plug them back in when i get home from work

---

### Post by hyper_ch on 2007-05-10
then you have not set the SATA drive as first harddrive to boot from in the BIOS...

---

### Post by spider reaver on 2007-12-19
Hey there people, I could use some help please!!!!!!!

I have downloaded Ubuntu 7.4 which was around 400Mb and burnt it to disc.

I've installed it serveral time now and no matter which way i set it up i _CANNOT_ get it to boot, all it get is "error loading operating system".

I'm trying to install this OS onto my 160 SATA II driver which is a maxtor but it will NOT boot linux, it will install it fine using the CD (which is my _ONLY_ IDE device) but doesn't seem to want to actually load linux properly.

I did have windows XP PRO on the same drive but I wasn't bothered if it got wiped from the drive and replaced by linux (it isn't hard to change back really.) I dont think it was the copy of XP that was causing problems for me but it gone now as the drive has been formatted a few times nown but i'm still getting the same error message.

I have an AMD AM2 X2 64Bit 4200+ which is 2x2210MHz cores with 1GB of DDR2 667 and an ATI X300 PCI-E GFX Card so i dont think there is an issue with my hardware as it is a standard ASUS mobo as well.

I would love some feed back on this if anyone might be able to help me with this dilemma.

I would like to add that I am not new to linux but it has been a long time since i used it so i'm very rusty on remembering how to do things.

Please email me (pc-guru@hotmail.co.uk) or post!!

Thanks peeps!!

Jim

---

### Post by hyper_ch on 2007-12-19
there's no 7.4 version... there's 7.10 and 7.04.

And no ubuntu image is below 500 mb. Download it again and this time I recommend to use BitTorrent for download.

---

### Post by spider reaver on 2007-12-19
thanks for the speedy reply. will have a look now and will post with results!!

cheers again

Jim

---

