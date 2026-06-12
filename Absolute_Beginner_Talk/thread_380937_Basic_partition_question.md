---
title: "Basic partition question"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by STUMPOFWAR on 2007-03-10
A few beginner questions. I've read the guides but I still have a few concerns...

I have an older desktop.....P4 1.8 ghz......it has two hardrives (60 and a 250)......and I've upgraded the machine quite a bit (new video card, sound card etc etc)...so its worth squeezing some mroe time out of it......about a year ago I turned it into a media center. I have the machine running through my high def TV and sound system so that it is a gloried jukebox with pictures.....that I occasionally use for internet access (for Sirius radio or podcasts)

The 60 gb hard drive is the orginal  drive with Windows XP installed. My 250 gb hard drive is for my pics and MP3s......which together are about 80 gbs......

I want to dual boot with Ubuntu (one of my students got me in to it) .......Any time I that I have partioned a drive before, it destroyed all the data on the target drive......and I lost my original HP system CDs years ago....thus my worries.....

Is there a way to alter the partition on the 60 gb drive to install Ubuntu without detroying the Windows install? 

<OR if that's not possible>

Is there a way to transfer the windows install to the 250 gb drive to leave the 60gb unfettered for the Ubuntu installer to work with? And to do so which drive should I switch to master and whcih to slave?

I am much more concerned with losing the MP3s then anything else as the pics are backed up on my iBook. I spent a full week one summer ripping my hundreds of CDs and I would not like to do that again. 

thanx.....

---

### Post by andreas64 on 2007-03-10
Hi,

you can shrink your 60GB-partition with tools like PartitionMagic if there is enough free space on it

Andreas

---

### Post by chewearn on 2007-03-10
> **STUMPOFWAR said:**
> A few beginner questions. I've read the guides but I still have a few concerns...

I have an older desktop.....P4 1.8 ghz......it has two hardrives (60 and a 250)......and I've upgraded the machine quite a bit (new video card, sound card etc etc)...so its worth squeezing some mroe time out of it......about a year ago I turned it into a media center. I have the machine running through my high def TV and sound system so that it is a gloried jukebox with pictures.....that I occasionally use for internet access (for Sirius radio or podcasts)

The 60 gb hard drive is the orginal  drive with Windows XP installed. My 250 gb hard drive is for my pics and MP3s......which together are about 80 gbs......

I want to dual boot with Ubuntu (one of my students got me in to it) .......Any time I that I have partioned a drive before, it destroyed all the data on the target drive......and I lost my original HP system CDs years ago....thus my worries.....

Is there a way to alter the partition on the 60 gb drive to install Ubuntu without detroying the Windows install? 

The ubuntu installation should be able to take care of repartitioning for you.  But first, make sure you run Windows Defrag a few times to get all your files to the beginning of the partition.
Courtesy of a forum staff: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Note: personally, I am always worried whenever a partitioning is required; because there is always a risk, however small.  I recommend you find a spare hard disk that you can use to back-up your entire Windows partition.

---

### Post by STUMPOFWAR on 2007-03-10
> **AstalaVista said:**
> The ubuntu installation should be able to take care of repartitioning for you.  But first, make sure you run Windows Defrag a few times to get all your files to the beginning of the partition.
Courtesy of a forum staff: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Note: personally, I am always worried whenever a partitioning is required; because there is always a risk, however small.  I recommend you find a spare hard disk that you can use to back-up your entire Windows partition.

Thats a good idea..... I have an iMac with a dead PAV in my school's server room that I will crack open and throw the 30 gb drive  into an enclosure just to be safe......

Is there a way to back up the windows install on to the 250 g drive just in case?

---

### Post by chewearn on 2007-03-10
> **STUMPOFWAR said:**
> Thats a good idea..... I have an iMac with a dead PAV in my school's server room that I will crack open and throw the 30 gb drive  into an enclosure just to be safe......

Is there a way to back up the windows install on to the 250 g drive just in case?

Well then, that only moves the backup problem one step back, because you will need to resize the partition on the 250g drive to make room for the Windows backup.  Which means you will need to backup the data on the 250g drive.

I don't know your specific situation; but here is how I would do it to make sure at no time will I loose anything:
0. First, remove the 250g drive, just in case
1. Prepare a DOS boot disk with fdisk, so I can restore the Windows MBR
2. Hook-up the spare drive
3. Install a free Windows software called DriveImageXML
4. Use Windows Disc Management tool to create the back-up partition on the spare drive (there is no need to format)
5. Use DriveImageXML to clone to 60g XP to the spare drive
6. Remove the 60g drive, put the cloned spare drive as primary
7. Use the DOS boot disk to fix the MBR on the spare disk
8. Check to see that I can now boot from the spare drive to Windows

If all goes well, you now have the Windows spare drive ready to go if things go wrong with the 60g drive.

I know these steps are quite convoluted, but better safe than sorry.

---

### Post by rusty4r on 2007-03-10
Good answer, and I've used driveimage before it is a good backup utility.

On step 6, Do you mean primary as in jumpers?

On step 7, Do you boot with the DOS boot disk and then type what? Is it just "fix mbr"?

---

### Post by chewearn on 2007-03-11
> **rusty4r said:**
> On step 6, Do you mean primary as in jumpers?
I mean as the primary boot device.  Probably, will work best as IDE0 primary (especially with old PC).

> On step 7, Do you boot with the DOS boot disk and then type what? Is it just "fix mbr"?
You should of course include the fdisk program in the DOS boot disk.  Then type:
```
fdisk /mbr
```

Alternatively, there is this:
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

