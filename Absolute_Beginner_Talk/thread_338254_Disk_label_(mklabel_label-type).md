---
title: "Disk label (mklabel label-type)"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by falsedust on 2007-01-14
I don't know why I suddenly thought of this now but about a week ago I reinstalled Ubuntu 6.06 onto my sisters PC (her HD died/went crazy) so I installed another HD and zeroed it using one of those programs that completely removes everything, so this older drive is like brand new no data on it what so ever.

Anyway going through the process of installing Ubuntu I had to partition the drive etc using gparted. But at one of the prompts it asked me to set the disk label, it presented me with a list and I accepted the default which was MSDOS. I did notice other options but was unsure of what they do, so at the time I didn't pay to much attention to it.
But tonight for some reason I remembered this prompt and am now curious what are the other options used for?

After having a search around I came across this - [http://www.gnu.org/software/parted/manual/html_node/mklabel.html#mklabel]("http://www.gnu.org/software/parted/manual/html_node/mklabel.html#mklabel")

2.4.4 mklabel

— Command: mklabel label-type

    Creates a new disk label, of type label-type. The new disk label will have no partitions. This command (normally) won't technically destroy your data, but it will make it basically unusable, and you will need to use the rescue command (see Related information) to recover any partitions. Parted works on all partition tables. 1

    label-type must be one of these supported disk labels:

        * bsd
        * loop (raw disk access)
        * gpt
        * mac
        * msdos
        * pc98
        * sun 

    Example:

              (parted) mklabel msdos
         
    Create an MS-DOS disk label. This is still the most common disk label for PCs. 


So my question is what are these other disk labels and what happens if I use them?

---

### Post by wpshooter on 2007-01-14
I see someone else is thinking about this, other than just me.

It is my understanding that if you are using a regular off the shelf DOS compatible computer the MSDOS (default) is  the correct choice.

However, as far as the others are concerned I have posed the same question as you have and I have never really gotten a comprehensive answer.

But from the names in the list it would appear that these are for other architecture types and O/S types.  My **GUESS** is that you could probably use the gpt for Ubuntu but I am not sure about that and I have never given it a try.

If you decide to try one of the other listings other than DOS for your Ubuntu installation and it works, please report the results on here.  I would be interested in the results.

Thanks.

---

### Post by falsedust on 2007-01-14
Yeah my thinking was that each one was for a specific OS, some are obvious Mac, BSD, MSDOS. But I was also thinking why if I am using Linux do I have to have a MSDOS disk label?
Ok well I guess I am going to do it then I am going to use the GPT. Which works out well because next week I have to re-organise my HD's to finally get rid of XP and NTFS. 
But first I have to scan a whole heap of my negatives and polaroids.

---

### Post by wpshooter on 2007-01-14
Please post back your results, I will be monitoring for it.

Thanks.

---

### Post by falsedust on 2007-01-15
Ok so basically from my further research into the matter (I did come across your earlier posts :) )  it comes down to your BIOS and handling disk partitions. A MSDOS disk label can only handle 4 Primary partitions thats why you have to create an extended partition to deal with more than 4 primary partitions. 
Does the average user need more than 4 primary partitions?
There is lots of stuff about disk partitions and labels on Wikipedia, have a look.

I did come across this from a cool little Kiwi Linux user group that explains the GPT thing - 

[http://www.wlug.org.nz/GPT]("http://www.wlug.org.nz/GPT")

GPT was introduced for iA64 systems, to get around a fixed 32 bit issue (2 to the power of 32 is 4 billion times a 512 byte block equals 2 Terabytes) in the PC-BIOS Partition table. Partitions larger than 2 TB require using a GPT disklabel, which differs from the PC-BIOS Partition table in a number of ways:

    * Is easily extensible.
    * Can contain up to 128 primary partitions, as opposed to 4, so there's no need for extended partitions.
    * Allows Partitions larger than 2 TB.
    * Identifies Partitions with a GUID so you can reference that Partition even if disks are moved around.
    * Identifies Partition type with a GUID, thus avoiding the type conflicts that plague the PC-BIOS Partition table format.
    * Provides a 46(?) character UTF-16 partition label to identify Partitions.
    * Has a "fake" MBR for backwards compatibility.
    * Includes a CRC32 to detect corrupt Partition tables.
    * Stores a backup Partition table at the end of the disk.

Most partitioning tools under Linux will fail to do anything sensible with a > 2 TB Partition. As of this writing, parted(8) is the only one that understands them and will let you set the GPT label on the disk.

There is a lot of information stating that you cannot boot off a GPT enabled device. Most of the claims imply that the fault is with LILO or GRUB not understanding GPT devices. We've not tested this, but GPT and traditional MBRs will coexist.
---

So in the end if you are using GRUB or LILO you have to use a disk label that they can both boot and read from. I don't see the point of using anything other than the MSDOS disk label, unless you are using a Mac, BSD, Amiga or Sun OS.
I know this isn't comprehensive in detailing the disk label questions, but I think it is not something to be worried about because if it were then there would be more talk and discussion on the matter.

Oh I posted a similar question on the GParted forum - [http://gparted-forum.surf4.info/viewtopic.php?id=332]("http://gparted-forum.surf4.info/viewtopic.php?id=332")
So we will see what comes of that.
cheers

---

### Post by nibsa1242 on 2007-03-04
I attempted an edgy install with GPT as the disklabel to see what would happen. The install seems to run fine until it attempts to install GRUB at which point it says there is a GRUB error. So... I don't recommend using GPT on a boot drive unless you know how to get GRUB to work properly with the GPT bootlabel.

---

### Post by rubberdragon on 2008-06-11
Hi, Everyone. Not a Ubuntu user myself, but found this thread and registered to suggest this link [http://www.sysresccd.org/news/2008/01/26/gpt-disklabel-support-guid-partition-table/](http://www.sysresccd.org/news/2008/01/26/gpt-disklabel-support-guid-partition-table/)
Hope this helps:):)

---

