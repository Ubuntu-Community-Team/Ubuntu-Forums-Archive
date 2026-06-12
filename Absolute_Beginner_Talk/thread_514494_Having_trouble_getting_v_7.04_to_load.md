---
title: "Having trouble getting v 7.04 to load"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Disker on 2007-07-31
Hi Everyone!

I just joined the Forums and have a question on my attempt to get Version 7.04 up and running.   I'm running a OptiPlex with 384Mb of RAM and a Pentium III processor with a 9G hard drive.  The machine currently has 2000 Pro running on it without errors.  

When I boot from the Live CD the Ubuntu logo appears and the initial Welcome Screen.  I choose Load/Install and things start moving with the Logo appearing and the orange progress bar.  This goes on for a while and then I start getting errors.  In the end the screen goes blank and I'm done for.  There is a continuous flow of errors but a few i could catch were;

hdc: error_code: 0x70 sense_key 0x03 asc and so on

Buffer I/O error on device hdc logical block 0 

Buffer I/O error on device hdc logical block 1

AS I mentioned, after this the screen goes blank and I have nothing.  I have used this CD in another machine and it loads and runs from CD fine so it's not the CD.  I want to load it on the OptiPlex though so I need to figure this out.  

Thanks for the help!

---

### Post by Rocket2DMn on 2007-07-31
The best option when the LiveCD doesn't work is to download and use the Alternate CD which gives you a text based install.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and select the Alternate CD checkbox at the bottom.
Don't forget to check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") against the correct [hash]("https://help.ubuntu.com/community/UbuntuHashes") and then to burn at a slow speed, like 4x, so as to reduce write errors.

---

### Post by ramjet_1953 on 2007-07-31
Before you try downloading the alternate CD, a few questions.

1. At what speed did you burn the iso image?
Any thing faster than 4 X for ANY iso is asking for trouble.

2. Did you use good quality media?
Budget CDR's don't cut it with iso's.

3. Did you check the integrity of the disk after burning?
There is a menu item to do this before booting into the live Desktop.

Regards,
Roger

---

