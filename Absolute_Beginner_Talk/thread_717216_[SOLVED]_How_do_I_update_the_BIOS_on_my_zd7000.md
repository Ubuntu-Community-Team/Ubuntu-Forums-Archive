---
title: "[SOLVED] How do I update the BIOS on my zd7000?"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2008-03-06
I recent did a little search to see if my bios is out of date (because, surprisingly, it does not support USB booting capability).  This newer versions notes don't say that it's an added feature, but there may have been a previous version that worked it in there.

I have an HP Pavilion zd7000 laptop, and the bios updating utility provided by HP is supposed to be run from windows.  Can this be run from within VMware safely?

[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=hb-24923-1&lc=en&cc=us&dlc=en&product=1148894&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=hb-24923-1&lc=en&cc=us&dlc=en&product=1148894&os=228&lang=en)

Is there another way to go about doing this?

---

### Post by rbc on 2008-03-06
I have not tried this personally, but check this how-to:
[http://ubuntuforums.org/archive/index.php/t-190615.html](http://ubuntuforums.org/archive/index.php/t-190615.html)

---

### Post by diablo75 on 2008-03-08
I managed to get my bios to upgrade, but it took me a day, and it didn't add any new boot features to my laptop (I wanted to be able to boot from a thumb drive).

Here's what I did:

1.  Downloaded the *.exe from the original hp.com link I posted above.
2.  Ran the exe using Wine, and while it was running, watched my wine /Program Files/ folder for changes.  The executable will create a folder in your fake program files folder (in this case, it was called sp28962, and inside of it is a file called WINPHLASHF34.exe.  Copy that winphlash34.exe to a thumb drive.
3.  Download BartPE and build an install disc, using the disc builder and a Windows XP CD.
4.  Boot into BartPE, insert the thumb drive with the above mentioned file on it, and then attempt to run it from within BartPE.  It should work.

The reason I had to watch the program files folder and grab that other exe is because for some reason, when trying to run the original sp28962.exe (or whatever it was) file, BartPE would produce a "not enough disk space to extract to %Program Files%" error.  Running the WINPHLASH34.exe file takes a step out of the number of things that have to be done on top of BartPE.

---

### Post by wolfchri on 2008-03-18
If you have a DOS based program for your PC / motherboard / notebook, you can also upgrade the BIOS without Windows, by using Freedos. 

Here is a very easy, very simple guide, which works from CD as well as from USB stick (in case of CD-less machines, such as servers):

[http://vale.homelinux.net/wordpress/?p=238](http://vale.homelinux.net/wordpress/?p=238)

:guitar:

---

