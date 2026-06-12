---
title: "Booting and hard drive problems"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by RKF on 2006-02-05
1. When booting  -> checking all file systems - quits with error message "fsck failed" Control D to continue.

When trying the "repair" entry, gives 'bad command"  then CTRL D to get in.

A little bit of digging around in the system trying to do other things reveals ????? that the LVM is configured for ext 3 file systems (Ummm Duh?) when it appears the thing is searching for ext 2 ( again Duh?) If this is the case what is going on in the grub programming??? don't rreally want to know.

AND Linux will not look into the other discs on the machine, knows they are there but won't look. Did mange to get the 'enabled thing to work, but still can't see inot them.   please note that the only way to get the thing to boot in the first place was from a FDISC(ed) hard drive, into the LVM partitioning. None of the others would work - the Grub would just spit the dummy. 
[B]
Please reply in plain English for Dummies.[/B]

Find the HD config below :

Disk /dev/hdc: 30.6 GB, 30606151680 bytes
255 heads, 63 sectors/track, 3720 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          31      248976   83  Linux
/dev/hdc2              32        3720    29631892+   5  Extended
/dev/hdc5              32        3720    29631861   8e  Linux LVM

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdg: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1        4865    39078081    c  W95 FAT32 (LBA)
rickfischer@ricklinux:~$

---

### Post by RKF on 2006-02-06
Appears no on wants to play :(

RKF

---

### Post by Pragmatist on 2006-02-06
Since nobody has responded, I'll throw in my 2 cents (just keep in mind that is what its worth :) )

How do you have the 3 hard disks setup?  Is /dev/sda a SCSI hard disk?  which IDE is /dev/hdc on?

I take it that /dev/hdc1 is a boot partition.  What does the /boot/grub/menu.lst  file look like?

Does Windows XP (guess?) boot OK?

My guess is that your /boot/grub directory isn't even being read and that Linux doesn't know where to find it.

Try and download a copy of Knoppix, which is a live cd ([www.knoppix.org](www.knoppix.org)) This is a good way to test hardware just to make sure nothing is wrong with the drives (which I doubt).

---

### Post by RKF on 2006-02-06
This computer has no MS OS on it at all.

Boot is on the IDE disc that contains hdc1  hdc2 and hdc5

dev/sda is a SATA 160g data drive formatted in NFTS and containing all of "my documents" (MSXP format) 

dev/hdg is IDE 40gig to be a data drive for linux and is formatted in FAT32.

All discs are in removeable draws.

Plan was to get all the discs visible then reformat the 160 SATA to FAT 32 to be visible to, and for use by, both OS and then perhaps sliding gradually over to this as the main OS. Fat chance at the moment :) 

Cheers 

RKF

---

### Post by Nord on 2006-02-06
Did you try to uplug your SATA drive and boot up your system without it?

---

### Post by RKF on 2006-02-06
SATA drive has been out of its drawer at boot - yes.

RKF

---

### Post by RKF on 2006-02-06
latest try results : 

rickfischer@ricklinux:~$ sudo mount /dev/hdg
Password:
mount: can't find /dev/hdg in /etc/fstab or /etc/mtab
rickfischer@ricklinux:~$ sudo mount /dev/hdc2
mount: can't find /dev/hdc2 in /etc/fstab or /etc/mtab
rickfischer@ricklinux:~$
rickfischer@ricklinux:~$ sudo mount /dev/sda
mount: can't find /dev/sda in /etc/fstab or /etc/mtab
rickfischer@ricklinux:~$

Need help. :confused:

---

### Post by RKF on 2006-02-06
more info :

borrowed and Tried a knoppix run from disc.   The boot failed: Error:

dprobe: FATAL: error inserting apm (/lib/modules/2.6.11/kernel/arch/i386/dev/hdc2/kernel/apm.ko) no such device

Got to be someone who had a handle on this?????  - in plain English.

Cheers 

RKF

---

### Post by RKF on 2006-02-06
reckon it might have a lot to do with the "fsck failed" every time the system boots??
Cheers

---

### Post by Pragmatist on 2006-02-07
Now that I took a second look at your partition table, this is what I would try if I were you:

Reinstall ubuntu!  Reason: First of all your missing a swap partition which is required.  Second, the LVM thing is an unnecessary complication at this stage.  You could always use 10 GB maximum to get linux up and running and leave 20 GB for your future LVM partition.  When installing this time I would make 4 partitions at a minimum:
1.) /boot  100 MB  is enough;  put on primary partition; format=ext3
2.) /         ~10GB; put primary partition; format=ext3
3.) swap  1-3X your RAM;  put on primary or extended/logical; format=swap
4.) /LVM or /mnt/LVM ~20GB; on primary or extended/logical; format=ext3

I think the fsck problems your having are based on the unusual filesystems you've picked for your partitions.  I think its not performing the filesystem check because it can't interpret your partition table.

If you don't want to do that, what does knoppix have in /mnt  also, what output do you get when you type: ```
mount
```  The reason for looking in /mnt is that knoppix should have created directories corresponding to the partitions available.  For instance, when I just ran Knoppix, it had directories /mnt/hda1 and /mnt/hda6  even though I hadn't mounted those partitions. The directories were empty until I mounted the partitions, but they were there.  Finally, when running knoppix I would just have the linux drive in.  Finally, are those removable drives connecting to an adapter or something else rather than directly to the motherboard?

That is the best I can do without further information.

---

### Post by RKF on 2006-02-07
Hear what you are saying but at the original install the only way the grub would boot was if I did a DOS FDISK then from the ubuntu install with the LVM partitions as presented by the installation disc.  The only selection I did was off of the 4 choices given on the disc????????

I had initially started out as everyone does. Stick the disc in and let it run, follow the defaults. After each deterorating iteration, about 5; in the end with only a basic computer with a CD drive, and one ide hd with no peripherals or add ons, I managed to get the thing through the boot sequence, but with the "fsck failed"

Then we have he thing about installing partitions manually. yagottabjokin!

I get into enough trouble when using something like "Partition magic" which is menu driven, never mind actually writing the code.

So where does that leave us?

Is installed and partitioned per the Installation CD but can't see itself and the grub can't/won't boot in any configuration other than the one that is.

However, just had a thought. If I use partion magic and format for linux - what you reckon?  If so How??

Cheers  


Cheers

---

### Post by RKF on 2006-02-07
removeable , but not interchangeable drawers

---

### Post by Pragmatist on 2006-02-07
I'm confused (it's contagious :)  Knoppix should run as long as one of your CD drives work.  It has nothing to do with the hard drives.

The Ubunutu installer should be formatting your hard drives and placing the filesystems on it.  What was on your hdc drive before??  (I'm assuming the hdc drive is the one you used when installing with only one hard drive).

---

### Post by RKF on 2006-02-07
Nothing on the drive - wiped . Formatted using FDISK in DOS

Well, the knoppix quit with the FATAL ERROR as described.

For the single hard drive - yep. It is exclusively for Linux/ubuntu.

Methinks might go into box and simply re-arrange the plugs, bibs and bobs, DVD/CD drives etc. and ensure that everything is "cable" select.

Then have another look at a re-load from a HD formatted for Linux using "partion magic"

---

### Post by RKF on 2006-02-13
Apologies: Got caught up in other things nothing to do with computers. 

In the meantime have ripped out the ribbon cables and replaced with big long round proper looms all into the motherboard. This has resulted in at least being able to see and enable the hard drives. Still cannot see the or access the floppy.

So can see and access, 

. the main linux file drive,

. a 40Gig IDE hard drive. 


Think I can see and have enabled a 160 Gig SATA formatted in NTFS but cannot see the folders.  I was under the understanding that I should at least be able to see the NTFS Folders if not inside them ?????  Que?

Still cannot see or access the floppy disc drive.

Still have the Fsck error at boot

RKF

---

### Post by Pragmatist on 2006-02-13
So can you boot into linux with ANY drive?  Can you get to a prompt???

---

### Post by Pragmatist on 2006-02-13
Perhaps I'm not being clear.

1.) Can you boot any combination of your hardware and get to a login screen?
2.) Have you been able to boot this equipment (motherboard etc...) with another OS (i.e. Windows)??

3.) When you say that the computer can "SEE" a drive or not see a drive, what do you mean?  How can you know if the computers sees it or not?  Do you mean that the BIOS recognizes the hardware?  Or, are you actually entering Linux at a login screen and using utilities to determine what hardware is or isn't working????

We need clear precise information if we are to help you.

---

### Post by RKF on 2006-02-13
Reply:

1) No. at each attempt, irrespective of configuration it always quits at the fsck and requires a CTRLD to pass on.

*Note: This has always been the case since I finally got the grub to run.*

2) Runs perfect in XP HD in the boot drawer. 

*Note: The HD for Linux drawer has been swapped out twice all HDs are known to be good.*

3a. Previously (before the cable changes) from the fully booted/loaded  "System" drop down menu "disc management", though the disc manager knew they were there and gave their part/serial nos it could not enable or access the discs. Couldn't see into :) 

3b. Last evening (post cable change) it allowed me to enable:

 i) the 40Gig FAT HD and see into the folders and open the files. 

ii) the 160Gig Sata NTFS HD  but apparently not see the Folders.

3c. It has only ever shown a floppy icon but nothing else, no info nothing. clicking on the Floppy icon result in only the properties of one of the HDs.


Is all this any more help??

Cheers 

RKF

---

### Post by Pragmatist on 2006-02-13
> [the **disc manager** knew they were there and gave their part/serial nos/QUOTE]
What **disc manager**??
[QUOTE]Last evening (post cable change) **it** allowed me to enable....**It** has only ever shown a floppy icon but nothing else
What is **It**??

As I'm sure you can tell by how often I'm responding to you, I'd like to help you.  However, I cannot see anything without your showing it to me.  I am not at your house :-D 

If you are using something other than Linux to test your hardware, let me know.  If you are able to get into Linux, let me know as then I can really help you alot.

You have three choices:

1.) Reinstall Ubuntu and repartition according to my previous instructions when prompted by the Ubuntu installer.  This was my recommendation.

2.) Change your partitions on your Linux HD using Partition Magic or a Linux tool like GnuParted.  Then try rebooting and if that doesn't work reinstall as in option #1

3.) Try and fix your machine the way it is (this seems to be your preference)  In this case you **must have a bootable system or a system that can be made bootable**  It sounds like you don't have a bootable system right now.  However, you keep saying things like "It sees or It doesn't see" various things so I'm not sure if you know that because your in Linux or using some other tool.

Since you said something like "yagottabkiddin" regarding using Partition Magic, my suggestion is to reinstall and follow my instructions for partitions.  See my previous post.

Good Luck!

---

### Post by RKF on 2006-02-14
Sorry, "it" is "Gnome" the computer/whatever seeing into itself (a la "device manager" and/or "my computer" in MS XP) .

Anyway will go back to "Go" see if I can find $200, but if not will start over, step through all of your current and previous instructions and hope I don't end up in gaol :) 

Thanks, and will get back to you in a day or too after I have done all of this. 

Cheers

RKF

---

### Post by RKF on 2006-02-20
OK - all is well. All installed OK.

Replaced all of the IDE ribbons with looms and then went and wiped the OS disc and reformatted for Linux using Partion Magic. All tickity boo, except that cannot see or mount the 1.4 floppy - Can't have everything.

Now that I have the Linux/ubuntu up and running, wonder what I am going ot do with it. Won't even import an address book from Windows never mind run/install any of my critical (path) programmes.  However, those will be subjects for different threads.

Thank you for your assistance 

Cheers 

RKF

---

