---
title: "1st try: running desktopCD on windows"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by cmk_78212 on 2006-05-29
I have downloaded and burned ubuntu 6.06 rc 2 on to CD.  Now, I don't know how to make it run.  selecting the icon on the CD causes windows to ask what program I want to use to open this.  At start up, I have tried running the cd drive as the boot drive at start up, but windows still started.

Any ideas?

---

### Post by user1397 on 2006-05-29
[quote=cmk_78212]I have downloaded and burned ubuntu 6.06 rc 2 on to CD.  Now, I don't know how to make it run.  selecting the icon on the CD causes windows to ask what program I want to use to open this.  At start up, I have tried running the cd drive as the boot drive at start up, but windows still started.

Any ideas?[/quote]
Keep on trying opening the system BIOS.  Usually you have to press Esc, F2, F12, F10 or something of the sort (sometimes it even tells you).  Remember, to enter the BIOS, you must be at the very first startup screen, where your computer's brand name appears.

Once you configure the BIOS correctly, just stick your cd in, restart, and voila!, you'll have the live-cd running!

---

### Post by mostwanted on 2006-05-29
When you insert the CD in Windows do you then see a bunch files or just the single data file (the iso)? If it has been burned correctly (as an iso/disk image) you should see lots of files.

If your CD has been burnt correctly (as a CD image) then the problem is probably that your PC isn't set to boot from CDs - you need to configure that in your BIOS.

---

### Post by zhoux on 2006-05-29
you have to use a iso burner to burn the image on to the cd, so perhaps you should reburn the cd...i would suggest deepburner (which is free).  It could also be some problem with the iso image itself.  

i've actually never used the live cd before, i found that the text-based installer is much easier and smoother. 

hopefully that would help

---

### Post by steve.horsley on 2006-05-29
To summarise, there are two possible problems here. 
1: The PC BIOS isn't configured to boot from CD
2: The CD isn't bootable because it was burned wrongly

Number 1 can be corrected by changing the "boot order" in your BIOS. How you do this depends on your computer, but you need to set it to try to boot from CD before it tries to boot from the hard disk.

Number 2 is tricky. As mostwanted said, the test of whether you burned it right is to open the CD in Windows and look at the contents. If you see a lot of files and directories then it is probably burned right. If you just see the *.ISO file on the CD, then it has been burned wrongly.

To burn an ISO file correctly, you neeed to burn it as an **image** file, not just write the data file to a CD. I remember that Nero has a menu option "Burn Image file", I guess other programs have a similar option.

---

### Post by cmk_78212 on 2006-05-29
when I open my CD, I see only one file and it is the one that I downloaded.  It is listed as an .iso file.

I attempetd to make it an image file using the program "sonic."  I then reburned the CD.  It asked me to select a boot file.   For no particular reason, I picked "bootfix.bin" from the "i386" folder.  On running the bios, I set it to boot from CD, but nothing happened.  

Any ideas?  

Also, If I run the full intall version (the server version, I think?) is a partition program included, or do I have to do that before hand.  If I do so before handd, am I able to remove the partitian if I want to remove ubuntu?

---

### Post by aysiu on 2006-05-29
To burn it as a disk image, use these steps:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by cmk_78212 on 2006-05-29
Got it working, thanks.

---

