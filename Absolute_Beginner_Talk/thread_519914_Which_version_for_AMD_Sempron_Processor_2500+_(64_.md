---
title: "Which version for AMD Sempron Processor 2500+ (64 Bit supported)"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by ben22 on 2007-08-07
Hello,


I am a total newbie and have a problem with ubuntu not letting me enter.

Maybe I downloaded the wrong iso?

From [http://releases.ubuntu.com/7.04/]("http://releases.ubuntu.com/7.04/") I downloaded

PC (Intel x86) desktop CD, but maybe I should download 64-bit PC (AMD64) desktop CD ???

The computer has the following processor

AMD Sempron Processor 2500+ (64 Bit supported)
1,4 GHZ

Thank you so much, I really want to get ubuntu started and learn more about linux.

Ben

---

### Post by fatdaddy on 2007-08-07
either should work.  What happens or does not happen


Zack

---

### Post by logos34 on 2007-08-07
either will work fine.  You might want to read the stickies over in the x86_64 forum before you go 64-bit

---

### Post by Rocket2DMn on 2007-08-07
You downloaded the correct version (you could also use 64 bit but it has some problems).  After you download, you should check the md5sum to be sure it downloaded correctly, otherwise problems arise.
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then you should burn the .iso at a slow speed, like 4x, to help prevent write errors.  Use quality media if you can.
Not everybody is able to get the LiveCD to work, but if you are looking to install rather than just test it out, you can use the alternate cd which gives you a text based install.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom for the Alternate CD

If the problem is that it never even starts loading from the cd, you need to make sure your computer is actually booting from the CD.  This may require that you change the boot order in your BIOS so that the cd-rom drive is read before the hard drive.  Every computer is different when getting to the BIOS, but when you reboot your computer you will have a second or two to enter the BIOS (sometimes called Setup).  The screen should tell you - common keys to hit are F2, F8, F12, DEL, and ESC.  Once you set the boot order, you can save and exit the BIOS and restart the computer with the LiveCD or Alternate CD in the drive.

---

### Post by stchman on 2007-08-07
> **ben22 said:**
> Hello,


I am a total newbie and have a problem with ubuntu not letting me enter.

Maybe I downloaded the wrong iso?

From [http://releases.ubuntu.com/7.04/]("http://releases.ubuntu.com/7.04/") I downloaded

PC (Intel x86) desktop CD, but maybe I should download 64-bit PC (AMD64) desktop CD ???

The computer has the following processor

AMD Sempron Processor 2500+ (64 Bit supported)
1,4 GHZ

Thank you so much, I really want to get ubuntu started and learn more about linux.

Ben

Ok, here is a silly question.  The 32 bit version will work on both 32 and 64 bit processors.

Did you simply burn the .iso to a CD or did you burn an image?

---

### Post by Hospadar on 2007-08-07
you want to burn an image, if you did it right, you will see a bunch of files on the cd instead of just one .iso file.

---

### Post by st33med on 2007-08-07
An example of what won't work in the 64-bit version is Flash. There is currently no 64 bit Flash available.

---

### Post by ben22 on 2007-08-07
Hey thanks,

it seems the file in fact is corrupted (checked it with winMD5). How can I make sure it downloads the file properly???


adios,
 BEN



> **Rocket2DMn said:**
> You downloaded the correct version (you could also use 64 bit but it has some problems).  After you download, you should check the md5sum to be sure it downloaded correctly, otherwise problems arise.
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Then you should burn the .iso at a slow speed, like 4x, to help prevent write errors.  Use quality media if you can.
Not everybody is able to get the LiveCD to work, but if you are looking to install rather than just test it out, you can use the alternate cd which gives you a text based install.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and check the box at the bottom for the Alternate CD

If the problem is that it never even starts loading from the cd, you need to make sure your computer is actually booting from the CD.  This may require that you change the boot order in your BIOS so that the cd-rom drive is read before the hard drive.  Every computer is different when getting to the BIOS, but when you reboot your computer you will have a second or two to enter the BIOS (sometimes called Setup).  The screen should tell you - common keys to hit are F2, F8, F12, DEL, and ESC.  Once you set the boot order, you can save and exit the BIOS and restart the computer with the LiveCD or Alternate CD in the drive.

---

### Post by Rocket2DMn on 2007-08-07
I would just go to Ubuntu's website and try to download from there (again) - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
If you still can't get the md5sum to checkout, you may just want to put in a request to have a cd mailed to you.  Since mailing can take awhile, you may even want to wait to put in a request until Gutsy Gibbon is released in October, but here's the site anyway - [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) (within 10 weeks Gutsy should be out).
However, I would first try again, then try the alternate CD.  There are no guarantees when downloading files.

---

