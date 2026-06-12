---
title: "Can't get past window manager on cd boot?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-07-03
I can't get past the window manager load on the cd boot on ubuntu 6.06. It works fine on my laptop. 
The computer I am putting it on is about 4 years old. It had Windows ME on it and it started to act up, so i deleted the DOS partition and formatted the hard drive.
There is nothing on the computer now. I pop the Boot CD in and it loads all the way up to Window Manager and it isn't doing anythign. It has been like this for about 20 minutes now. The mouse takes a second to move but it does move. Any idea what is wrong?

---

### Post by sternael on 2006-07-03
Is the CD drive indicator light 'always' on and makes strange noice? If yes, then possibly the CD is corrupt. Choose (always on new burns no matter if it boots) the Check CD option on the boot menu and should checksums fail - burn a new CD with 1-4x speed or as low as your burner will permit.

The Live CD does not depend on the hard disk as long as it is empty. On some older computers with less than 128 MB of RAM the CD will freeze when booting the GUI as I have experienced myself.

---

### Post by tdrusk on 2006-07-03
It cd booted on the laptop, but not on the desktop. The desktop is pretty nice, so their should be no problems with that. 
I burned at 8X (lowest speed I could find) and it is doing the same thing.

---

### Post by tdrusk on 2006-07-03
What can I do if the computer doesn't have enough ram?

---

### Post by confused57 on 2006-07-03
[QUOTE=fuzzyhair]What can I do if the computer doesn't have enough ram?[/QUOTE]
If you have less than 128 mb of ram you could download the Dapper-6.06-alternate CD iso and do a server install:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

or Ubuntu Lite:
[http://www.ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntu+Lite](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=Ubuntu+Lite)

If you have 128 mb of ram, you could try the Xubuntu-6.06-alternate CD iso, I think you can also do a server install from the Xubuntu alternate CD.

---

