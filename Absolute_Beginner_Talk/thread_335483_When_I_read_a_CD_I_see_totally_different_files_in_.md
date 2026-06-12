---
title: "When I read a CD I see totally different files in ubuntu and windows."
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-10
When I read a CD I see totally differnt files in ubuntu and windows.

In windows I see the four zip files I backed up on the CD last week.  If I look at the CD in ubunto using Nautilus 2.16.1 file browser I see something totally different.

In ubunto I see a folder called files, openhtml.exe, and autorun.inf in what I think of as the root directory, although this may not be the correct term in linux.  If I open the files directory I see a bunch of .htm files, a loc.dat file, and an ahead.jpg file.

What is going on?

---

### Post by ComplexNumber on 2007-01-10
any screenshots?

---

### Post by thenetduck on 2007-01-10
I don't know how you burned the cd or how ever it was done, but one possible answer could be that the folders are on the cd but being hidden by windows. Windows does a lot of automatic stuff to try to prevent it's users from "breaking" their system. You will find that in linux, if you wanna break your computer it doesn't stop you. 
  Try enabling "hidden folders" in windows to see if this lets you view the folders one the cd. If all esle fails, just try doing it again. If that's not an option I would assume that windows added extra stuff onto the cd and hid the so it could read it correctly. I hope this helps, 

 The Net Duck

---

### Post by taurus on 2007-01-10
Maybe nautilus unzips and unpacks those files for you, showing you the content of those four zip files!

---

### Post by tc101 on 2007-01-10
I don't care about the extra stuff I see on the CD in Nautilis.  However, I need to get the .zip files off the CD and on my hard drive, and I don't see them anywhere on the CD.

---

### Post by tc101 on 2007-01-10
I did the same backup on two different CDs and I see the same thing on both of them in ubuntu/nautilis.

---

### Post by tc101 on 2007-01-10
I wrote data to a new CD from a new laptop running windows XP.  I thought maybe there was a problem with the format of the previous CD which was written on an old computer.  When I try to read the new CD that I just wrote on the new laptop I get a message that says:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

---

