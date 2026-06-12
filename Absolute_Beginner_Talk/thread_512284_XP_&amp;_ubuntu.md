---
title: "XP &amp; ubuntu"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by Ginoxy on 2007-07-29
Hello, 

i have downloaded the last version from ubuntu, Well i was searching the web over the dual booting i found many but in my case i have a question about the partition part 

i have 3 drives which is C, D & E 

C has windows XP

D has 7 GBs for MP3s 

E has 75 GBs (nothing in that drive) 

now im planning to set the E drive for Linux Ubuntu so on the installation steps what shall i do ? 

i think step 4 or 5 or whatever it talks about partition , any idea? 

thanks.

---

### Post by cmp1988 on 2007-07-29
For partitioning that drive, you need to figure out exactly how much of the drive you want dedicated for the Linux install.  If you want the whole drive dedicated, then reformat the NTFS partition to EXT3, but leave some space for the Swap partition.  Swap must be at least the same size as your RAM.  You also want your main Linux partition to be set as root (/)

---

### Post by FleetAdmiral74 on 2007-07-29
If you just choose the automatic, take the whole E drive option, then it will (should...99% of the time) automatically pick up on the XP install, and on completion and a reboot, you can chose which OS to boot into.

If you want to do a manual install, but which offers greater flexibility in the future, do partitions manually. Make a an ext3 partition, mount point / about 10gigs. Then make the swap type partition however much you want, and then make another ext3 partition mount point /home

This way when you upgrade, you can wipe the OS and reinstall without touching your home dir where your data is.

---

### Post by FleetAdmiral74 on 2007-07-29
> **cmp1988 said:**
> For partitioning that drive, you need to figure out exactly how much of the drive you want dedicated for the Linux install.  If you want the whole drive dedicated, then reformat the NTFS partition to EXT3, but leave some space for the Swap partition.  Swap must be at least the same size as your RAM.  You also want your main Linux partition to be set as root (/)

Whoh....sounds like he wants to dual boot...that means not touching the NTFS partition...

---

### Post by Ginoxy on 2007-07-29
Well i need both Windows XP and Linux 

i dont know how to make those partitions !

---

### Post by livingtarget on 2007-07-29
Important steps to remember:
Linux notations for harddisks are /dev/hda1, /dev/hda2, /dev/hdb1/ or if you have sata most likely /dev/sda1/, /dev/sdb1/

"a" stands for harddisk nr. 1, "b" stands for harddisk nr.2 these are the physical harddisks. So you have for example 2 80Gig harddrives than the first one is called hda and the second one hdb.

The number behind the letter stands for the partition number. This is how windows usually (with emphasis on usually) assigns C, D, E etc. So /dev/hda1 is usually C.

When you launch the partition editor think carefully and don't do anything too soon, read what you are actually doing. It should be quite easy to find your E: as it is quite large 75gb and it's all free. Ubuntu often picks those partitions by default. It should have either fat32 or ntfs file systems.

---

### Post by FleetAdmiral74 on 2007-07-29
> **Ginoxy said:**
> Well i need both Windows XP and Linux 

i dont know how to make those partitions !

well...tell us exactly where you are stuck, we can work from there.

---

### Post by Ginoxy on 2007-07-29
Okay, 

Last night i was about to install it and everything went fine i tried graphs mode i got the screen and the install icon for that i pressed on it and when i reached the partitions i stopped coz i did not know what to do as i said before i have 3 drives 

D E and F 


i want the F drive for Linux , 

So any idea how to make it , and ofcourse i dont wanna lose windows XP 


Thanks.

---

### Post by ugm6hr on 2007-07-29
My suggestion (very easy, but perhaps not the most ideal):

This assumes your "Drive F" is a partition of a larger hard drive (how many physical drives do you have?)

Boot Ubuntu LiveCD.
Start GNOME Partition Editor (look in Menus for it)
Identify drive F - it will be called something else in Ubuntu - see livingtarget advice.
Delete Partition(s) in F
Create Extended Partition in all 75GB of F
Apply.

Then run Ubuntu installer.
Select "Guided - Use largest continuous free space"
Follow instructions.

---

### Post by Ginoxy on 2007-07-29
Nice, But my question is how to do that ? i dont have the menu ! i downloaded the CD from the net! 

Regards,

---

### Post by ugm6hr on 2007-07-29
> **Ginoxy said:**
> Nice, But my question is how to do that ? i dont have the menu ! i downloaded the CD from the net! 

Regards,

Oh - sorry.

Try this: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

That also has pretty good instructions on how to do everything else you want to do too.

---

### Post by Ginoxy on 2007-07-29
Thanks a lot :)

---

### Post by Ginoxy on 2007-07-29
Hi again, 

i downloaded Partition magic few mintues ago , is it safe to make the partition from there ?

and by the way when i opened parition magic it gaves me Disk 1 = C Drive , D Drive 

and Disk 2  as a dynamic disk 

THanks.

---

### Post by ugm6hr on 2007-07-29
> **Ginoxy said:**
> Hi again, 

i downloaded Partition magic few mintues ago , is it safe to make the partition from there ?

and by the way when i opened parition magic it gaves me Disk 1 = C Drive , D Drive 

and Disk 2  as a dynamic disk 

THanks.

As per previous advice - yes - Partition Magic will do this in Windows too.  

But Partition Magic cannot create the Logical Partition for Ubuntu.  So follow my instructions as previously - create an extended Partition only.

Don't quite understand what you mean by "dynamic disk".

If you don't understand about partitions / physical disks - post a screenshot of Partition Magic / GNOME Partition Manager here before going any further.

---

### Post by Ginoxy on 2007-07-30
Sorry for being late to answer. Well i was trying to put any image here but i could not. 
i did not get the idea about partitions @ all ;/

---

### Post by anewguy on 2007-07-30
Maybe we should back up a step or 2:

A disk partition is a logical way of looking at a section of a physical disk.

For example, you may have a single drive but with 2 (or more) partitions - maybe 1 for Windows and the other 2 for Linux.

You might also have multiple disks, with 1 or more partitions on each drive.

From what you have posted, it appears you have 1 drive with 2 partitions for sure - your C: and D: drives (what partition magic is showing as "Disk1 = C drive, D drive") and another drive of unknown content (what partition magic is showing as "Disk2 as a dynamic disk".  Unfortunately, we don't really know what that means.

Do us a favor:

(1) Boot from your Ubuntu LiveCD

(2) Click on "Applications" on the top bar, scroll down to "Accessories" and then over to terminal and click on it.

(2) Once the terminal window has opened, type in:

parted    and press enter

This should bring up the disk partitioner.   Now type:

print all    and press enter

Please copy the output of that command for posting back here.

Type:

quit    and press enter

When you are returned to the terminal window prompt, just type   exit    and press enter


Now you should be able to reboot to Windows and post back what the print all statement showed.  That will help us help you.:)

---

### Post by Ginoxy on 2007-07-30
Right now im at the office once i come back home i will post about it , thanks for your help 

Regards, 

:)

---

### Post by Ginoxy on 2007-07-30
Hi again, 

We i did exactly as what mentioned above and i got this : 

Warning : You are not supeuser. Watch out for permessions

Warning : unable to open /dev/scd1 read-write

GNU parted 1.7.1

Using /dec/scd1


Then i did print all i got :

Error: Unable to open dev/scd1 unresognised disk label 


but i clicked on the icon over the desktop what is called " examples"  and i got this

File system 
Floppy drive
Disk1 = which is my current C drive in windows and i saw all folders & files there   ! 
Disk2 = which is my 2nd drive and has some folders also
New Volume = Which is my 3rd drive and has nothing inside it 


Please let me know if anything wrong. 

Regards,

---

### Post by bren on 2007-07-30
preface the commands given to you previously by "sudo"

e.g. "sudo parted"

(this will ask you for password and then make you superuser temporarily)

bren

---

### Post by Ginoxy on 2007-07-30
this incase im running linux but im not ! right ?

---

### Post by 3rdalbum on 2007-07-30
You should be running Ubuntu when you type in that command.

---

### Post by Ginoxy on 2007-07-31
As they told me yesterday, i just inserted Ubuntu CD and printed out that lines ! 

Now the problem as i think with the "NEW DRIVE"
how to set this drive with linux ?

Regards,

---

### Post by Ginoxy on 2007-08-01
So, any idea? 

Thanks.

---

### Post by ugm6hr on 2007-08-01
I am wary about giving advice to someone who doesn't understand the basics of physical drives / partitioning, since any error can result in you wiping / over-writing the wrong drive, leaving you with no working computer.

If you cannot get a screenshot of a Partition Manager for us to look at, I am not certain it is sensible for me to advise you blindly.

This might get you started with finding stuff out:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

In the meantime, I would suggest you continue to use the Ubuntu LiveCD and read around these forums.

Sorry this sounds negative, but I didn't want you to think I was ignoring you.

---

### Post by Ginoxy on 2007-08-01
Okay, but how to upload any screen shot i take ?!
must be a link right ?

---

### Post by ugm6hr on 2007-08-01
> **Ginoxy said:**
> Okay, but how to upload any screen shot i take ?!
must be a link right ?

Yes. When you reply - click on paperclip icon above text entry.

---

### Post by anewguy on 2007-08-01
Sorry - I was away for a while.  Just so you know, if you boot the LiveCD you are actually running Ubuntu LInux, you just haven't installed it to your hard drive yet.

Could you post back what your status is on this?

Thanks!:)

---

### Post by Ginoxy on 2007-08-02
Okay, Right now i was having 2 things on my main drive which is Basic and Dynamic disks 

Disk 0 = 2 drives one of them is C for Windows XP 

Disk 1 = Was Dynamic and i just formatted it to Basic Drive and i did 2 partitions on that drive. 

i used Partition Magic to install linux as a new OS 

Later on Partition Magic asked for either EXT2 (Recommended) or EXT3 

is this right ?

Regards,

---

### Post by Ginoxy on 2007-08-02
Hi again, 

This is what i have now:

My computer - Manage - Disk Management 

[ATTACH]39618[/ATTACH]

on the other hand i have "Partition Magic" with this :

[ATTACH]39619[/ATTACH]

There is a drive called "L" and i want this drive to be my Linux OS 

Regards,

---

