---
title: "Downloaded ubuntu-6.10-desktop-amd64.iso what next?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by stoopid on 2007-03-23
Okay so I download the file ubuntu-6.10-desktop-amd64.iso

I burned it to cd and tried to boot from CD.  This did not work. 

what do I do now?

Thanks.

---

### Post by Muzik83 on 2007-03-23
Sorry if this sounds like a dumb question, but when you burned the ISO, did you end up with many files on the burnt cd when you viewed it in Windows Explorer, or was there one single file (the iso) on the cd?

If there were many files on the cd (the "right" answer), can you give a bit more detail on what didn't work? Is your BIOS set to boot from the cdrom before the hard drive?  Did you see the Ubuntu logo and the 30 second count down?

-sean

---

### Post by dptxp on 2007-03-23
Burn Iso using InfraRecorder. Download it free, it works on Windows.
If you use Nero or similar use burning speed not more that 4X.

After you burn
Insert Cd.
Restart
Set bios to have CD as 1st boot.

When you get Ubuntu screen option, check CD Integrity first.
It takes time.
Next click on Live/Install.
CD shall run live.

You can Instal from the desktop you get.

---

### Post by stoopid on 2007-03-23
I just burned the single ISO file to disk.  Your reply leads me to understand that the ISO file is a disc image and must be burned with an application capable of burning a disc image.  I am going to use Nero and if that doesn't work ill use InfraRecorder. 
Thanks.

---

### Post by 3rdalbum on 2007-03-23
When you use Nero, it is called "Burn image to disc" in Nero Startsmart.

---

### Post by diskotek on 2007-03-23
extra note, you should burn the cd with slowest speed you can. 4x is good enough...

---

### Post by gautam on 2007-03-23
Are u sure that u r making a bootable CD out of the Image instead of copying the raw data onto the disc. Usually when u double click an ISO image ur default CD-Burner will start up and give u beautiful options and one of them will be "make a bootable disc". 

If it doesnt work that way open Nero (since u said you have it & Nero is a great aplicaiton to burn bootable CDs) and u should explore options to make bootable CD.

I dont have nero at the moment or I would have given clearer instructions. To test the CD after u have burnt it, open it in windows and it will give u options to install windows version of Firefox, adobe reader and other stuff. This is the best way to test if the CD is working.

---

### Post by stoopid on 2007-03-24
So I burned the image and it runs fine booting to the menu then the Ubuntu desktop.  Thing is that I have detailed instructions for creating the partitions and installing, I assume, an earlier version of Ubuntu.  I took the notes from this video:

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

Currently I have my hard drive partitioned in 2,  one for XP and the other unformatted for Ubuntu.  I need to create the a SWAP partition and a primary partition for Ubuntu.  When I attempt the Ubuntu install for the Ubuntu desktop I was not able to create the necessary partitions.  

I would like to do a manual install like outlined in the video and notes below.  Or if I can figure out how to create the necessary partitions from the desktop install that would be great. 

Please help. 

Here are the instructions I made: 
______________________________________________________
insert ubuntu CD

reset computer

create 2 partitions
1 as swap and
1 as primary partition where we install linux (ubuntu)

go to free space area
create new partition
create 512MB "swap" partition
enter

make it primary 
say yes put it at beginning of new partition
done

important
how to use the partition
we are going to use it as swap 
not bootable

make one more partition
create new
use rest of space
make it primary
use EXT3 journaling file system

pay attention
mount point
use / 
"root file system"
top selection

other thing is!:
bootable flag has to be set to "ON"

done here setting up 2 partition
"swap" and "main"
finish partition and write changes

create user account full name
create username for account
create password

Important!:
Install Grub boot loader to master boot record?
Answer: YES

Reboot/ Continue

Boot Menu:
Ubuntu: Top selecion to finish installation

Login
Username
Password

---

### Post by dptxp on 2007-03-25
why do you not run the live CD, click on install and do partitioning in step 5 that will come in your way. Use the extended partition, "delete" it there by selecting and right click, next use 8-12 GB for 'root' ('/'), 2 GB for SWAP, balance for data (EXT3 or FAT32).
Ensure that the Windows part is not checked for FORMAT.
The process is simple, you will get through easily.

See details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by stoopid on 2007-03-26
Thanks everyone.  I created the partitions and got Ubuntu installed.  

I created partitions for 

swap
/ 
/documents

I am not sure if the location /documents accesses the /documents partition though.

---

### Post by fakie_flip on 2007-03-26
Don't burn an iso file as a data cd or data dvd. Find an option to burn CD/DVD image.

---

### Post by stoopid on 2007-07-08
What is the link to start a new post?  It is not apparent to me.

---

### Post by splintercellguy on 2007-07-08
Make New Post in forum view?

---

