---
title: "Ubuntu CD always has errors"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by dESAI on 2008-04-09
Hi Good People :-)

I've had problems the last couple of weeks trying to install Ubuntu. I've downloaded 8.04 and 7.10 at least twice each. I've burnt maybe 5 bootable installation cd's. None of them worked. 

:confused:

After lots of troubleshooting, I finally check the CD's for errors (yeah I should have done it earlier ;-) NOOB!), and they all have problems.

:confused:

I've since redownloaded, and burn 2 new CD's each burn at the slowest speed my burner can burn. Still I have errors?

:confused:

This is really now urgent because, I installed Ubuntu on my fathers business computer about 6 months ago. Now the Word docs he exports to PDF are formatted incorrectly. So I need to connect to the Pc to see whats going on. I don't have a Linux Pc running at this moment. Is it possible for me to do a remote desktop connect from XP to Ubuntu 7.10? Or do I need to access it from Ubuntu only?

:guitar:

Any help is appreciated. Thanks everyone!

:popcorn:

---

### Post by PmDematagoda on 2008-04-09
When you say that you burnt the CDs at the slowest speed, could you please specify that slowest speed?

Also, did you check the MD5sum of the ISO that you downloaded with the proper one?

---

### Post by komputes on 2008-04-09
PmDematagoda is right, although most people just say it, it should be done every time you download a distro.  

1) Check the MD5  of the file to make sure that what you have is the same as whats on the server.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) When you place the CD in you will see "Check for defects", you may want to use that, as well as the memory test to check that the CD drive, the CD and the memory are all OK

3) if he turns on remote desktop you can connect via VNC, if it's across the internet/router port forwarding will need to be enabled on the router. If it's on a  local network it's easier.

---

### Post by dESAI on 2008-04-09
The slowest speed I can burn at is x4. I've never had problems burning ISO's before. This is the first time I've ever had to to try and burn something so slowly, it was worth a shot.

No i didn't try MD5sum... no idea what it is :confused:

---

### Post by russo.mic on 2008-04-09
Not to treat you like an amature or anything, but I don't know your level of experience.  Did you burn the ISO as a CD?  or did you just burn an ISO file to a data cd?  I only ask because I've seen people on the forums with this problem before.  

Russo

---

### Post by dESAI on 2008-04-09
HEHE no problem.

I'm a Linux Noob but I've been building computers for people for over 10 years.

I burnt the image to disc. 

The first CD didn't make it to the desktop view and showed a an error on the DOS-type screen (B&W)- dunno the technical name. 

The second made it to the login screen, but no futher. It just froze up.

The last one allowed me to start the installation process, but stopped because some installation files were damaged. That's when I did the "check cd for errors" and found the CD's themselves were the problem, not the download.

Thanks :)

---

### Post by ByteJuggler on 2008-04-09
An MD5 sum is a checksum, to verify that the ISO image as downloaded on your disk, is the same as the one on the server.  They publish MD5 checksums for each ISO, to enable you to verify the integrity of the file download before you burn it, and deal accordingly if the download corrupted the file contents somehow.  Go to the page previously mentioned by another poster and follow the instructions ( [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) )

---

### Post by dESAI on 2008-04-09
> **komputes said:**
> PmDematagoda is right, although most people just say it, it should be done every time you download a distro.  

1) Check the MD5  of the file to make sure that what you have is the same as whats on the server.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2) When you place the CD in you will see "Check for defects", you may want to use that, as well as the memory test to check that the CD drive, the CD and the memory are all OK

3) if he turns on remote desktop you can connect via VNC, if it's across the internet/router port forwarding will need to be enabled on the router. If it's on a  local network it's easier.

I only have a XP PC available atm. Is there an XP version of this?

I did the "Check for defects", that's how I discovered that the CD was the problem, when I thought it could have been the PC itself.

Thanks :)

---

### Post by Sef on 2008-04-09
> I only have a XP PC available atm. Is there an XP version of this?

Go back to the md5sum page.  There is a way to MD5SUM on Windows.

---

### Post by dESAI on 2008-04-09
> **ByteJuggler said:**
> An MD5 sum is a checksum, to verify that the ISO image as downloaded on your disk, is the same as the one on the server.  They publish MD5 checksums for each ISO, to enable you to verify the integrity of the file download before you burn it, and deal accordingly if the download corrupted the file contents somehow.  Go to the page previously mentioned by another poster and follow the instructions ( [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) )

OK I just installed MD5Summer for XP. But it will not allow me to select ISO to check. :confused:

Thanks :)

---

### Post by dESAI on 2008-04-09
> **Sef said:**
> Go back to the md5sum page.  There is a way to MD5SUM on Windows.

OK I installed MD5Summer for XP, but it won't let me check an ISO...

---

### Post by MarkRobert on 2008-04-09
The iso that you downloaded, was that through a torrent or a "save as"? Once I left a save as downloading, thought it was complete, burnt it, hung, scratched head, checked file size. Was way too small. Try redownloading it as a torrent (does it own error checking to make sure all parts there)

---

### Post by Sef on 2008-04-09
Read [How to burn an ISO]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm") and download [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

---

### Post by philinux on 2008-04-09
Just to save you making more coasters. I've been using cdrw's for ages now. Never had a problem.

4x speed is spot on.

---

### Post by dESAI on 2008-04-09
> **MarkRobert said:**
> The iso that you downloaded, was that through a torrent or a "save as"? Once I left a save as downloading, thought it was complete, burnt it, hung, scratched head, checked file size. Was way too small. Try redownloading it as a torrent (does it own error checking to make sure all parts there)

It was just the normal firefox file download. I have since installed and am now using Free Download Manager. Not sure if it's helping.

I have grabbit. How can I download to grabit?

Thanks :)

---

### Post by ByteJuggler on 2008-04-09
> **dESAI said:**
> OK I just installed MD5Summer for XP. But it will not allow me to select ISO to check. :confused:

Thanks :)

Umm, well, have you done what they show you to do, e.g.  Right click on the ISO file, click "Send to", click winMD5Sum, and a little window will pop up with the checksum for that file.  Using this method you can check *any* file.

---

### Post by ByteJuggler on 2008-04-09
> **dESAI said:**
> Free Download Manager. Not sure if it's helping.


FDM should help.  Do you see your download being redirected/done by the FDM download manager when you're downloading?

What's grabbit?  (Link please.)  Personally I tend to use "GetRight" as download manager on Windows.

---

### Post by dESAI on 2008-04-09
OK I re-downloaded it and checked it with MD5. The check said it's ok. 

But when I boot up and do a "check for defects" it still find one error.

I'm not even gonna try installing until I have an error free cd.

So what's next? I'm going to the store now to buy more cd's... better ones this time.


Thanks for you help :)

---

### Post by ByteJuggler on 2008-04-09
> **dESAI said:**
> 
I'm not even gonna try installing until I have an error free cd.

So what's next? I'm going to the store now to buy more cd's... better ones this time.

I suggest you buy some rewriteable (CDRW) discs, preferably brand name ones (Verbatim perhaps, or really any branded ones.)  If you still have problems after using better discs, I'd begin suspecting trouble with your CD writer, as crazy as it may sound.  Fortunately CD/DVD writers are dirt cheap these days, so you might then want to consider treating yourself to a writer upgrade.

---

### Post by dESAI on 2008-04-09
Doh...:(

I just got a pack of 10 sony cd-r... Gonna try again.

Can I do an installation from a usb? 

:guitar:

Thanks for the help! Very much appreciated :)

---

### Post by ByteJuggler on 2008-04-09
> **dESAI said:**
> Doh...:(

I just got a pack of 10 sony cd-r... Gonna try again.

Can I do an installation from a usb? 


cd-r is OK, it's just that you can re-use cd-rw's so you won't be creating so many coasters in the process.  :-)

You can install from a USB flash drive, but you'll have to put the installer etc on the USB stick first of course, which can be a bit fiddly depending on what you do.  Anyway, there's a howto somewhere for that, I think on the Ubuntu community documentation site.  (See if you can find it, if not I'll have a look and post back.)

---

### Post by komputes on 2008-04-10
> **dESAI said:**
> 
Can I do an installation from a usb? 


Instructions here:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

