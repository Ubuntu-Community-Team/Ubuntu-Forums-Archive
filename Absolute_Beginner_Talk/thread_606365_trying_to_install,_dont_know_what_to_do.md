---
title: "trying to install, dont know what to do"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by namo21 on 2007-11-07
So I mounted the .iso file on to a CD, booted to it, and it came up with DR DOS A:\ 

I honestly have no idea what I'm doing with Linux...  I read the install sticky but that's how to install it when you already have Linux running.

Sorry, but can someone help? :)

---

### Post by taurus on 2007-11-07
You need to burn the ISO onto a CD, not mounting it!

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by ARhere on 2007-11-07
I have no idea what you meant when you said you mounted the .iso on the CD.  I am going to assume you meant to say "burned the image" to a disk.  If so, and you are seeing an error message after POST and Ubuntu live does not start, then one of two things are wrong.

1. Instead of burning the image file, you just copied it to a CD.  In your CD/DVD software, you need to check the option that says something like, "burn image to disk" and not "copy data to disk".

2. If you did burn the image correctly, then the next step is to make sure your BIOS is set to boot from a CD/DVD.  When your PC first starts, a RAM test or HDD detection occurs, (*a bunch of white letters that you see before Windows starts to load*) you have the option to hit a key to enter the BIOS setup.   It is usually F2, F10, DEL, or CTRL+F.  If you look it should tell you briefly.  Once you enter your BIOS setup menu, one of the options should say something like "boot order" or something like that.  Make sure it says CD-ROM before HDD or DISK.  Every BIOS is different so you are going to just have to look.

Dr. DOS reminds me of some older PC's that were shipped with flash memory loaded with Dr. DOS which loads if OS was not found on the hard disk.

With the questions you are asking, I would suggest to get help from a friend.  Exploring is the way you learn, but is also the way you break things when you don't know what you are doing.  Please consider picking up a copy of "[the Official Ubuntu Book]("http://www.amazon.com/Official-Ubuntu-Book-2nd/dp/0132354136")" second edition.  It is very well done and cheap; perfect for beginners.

Hope this helps
-AR

---

