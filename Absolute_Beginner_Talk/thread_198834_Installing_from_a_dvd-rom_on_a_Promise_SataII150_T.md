---
title: "Installing from a dvd-rom on a Promise SataII150 TX2Plus ide/sata controller card"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by JohnMinadeo on 2006-06-17
Hi,

I have installed Ubuntu a few times in the past to see how it's coming along (love it folks, love it!) I am encountering a problem here though. My dvd-rom is on a Promise SataII150 TX2 Plus sata/ide combe controller as my mother board supplied ide channels are filled with various hdds.

The Ubuntu 6 boot cd starts right up, but as soon as I choose Install, it tries a few things then drops me to a "Very limited command prompt" whereupon I can reset my computer.

I assume I am to provide some sort of driver disk by the manufacturer of the card (which I have, however, it only has windows drivers. Of course) So I went to promises web site and they seem to have a Suse 9.2 package, and a RedHat rpm, and the source code (to build my own I presume).

So What I am really looking for is an image of such a driver for Ubuntu6. 

Is that the case? I'm sorry, thanks in advance for all your help, I've been reading thru these forums and it really looks like a helpful community. (You'll probably see me back here when it comes time for the ATI radeon drivers :D )

Thanks again!

--
John Minadeo
johnminadeo at hotmail dot com

---

### Post by catlett on 2006-06-17
Can you run the live cd? I say it because you can convert the rpm to a deb with the application alien. If you get a live session of ubuntu going. Download the rpm version of the driver. ```
sudo alien* driver*.rpm
``` That will create a deb package. Save it to disc for use when you install. Run```
 sudo deb -i *driver*.deb 
```To install the deb.
I never had to add drivers during install so I don't know the process involved with mounting the cd, Hopefully it is auto detected. I don't know anything about the shell the install puts you in. If you were in bash in a regular session you would cd to the location of  the deb and them sudo deb -i.
 Will you have to cd to the cd drive? I don't know. I don't even know what the installer labels the cd as. Hopefully it is just /dev/hdc and you can cd /dev/hdc and then sudo deb -i *driver*.deb.

It may not even be that. There have been a ton of posts about issues with installs and satas.

---

### Post by JohnMinadeo on 2006-06-18
I did find a number of mentions of folks trying to install TO a drive on the controller, it seems like the no brainer would be to throw the dvd-rom into an ide chain and correct it later. Which I suppose is ok, but I was hoping for a way to install it to the environment it will finally run on. Although I can live with that.

Ya know, now that I think about i may not have tried the live mode :-( 

Thanks for the links!

I'll go verify whether I actually can run the live. Thank you for the suggestion... I guess I just skipped right by it as I've already done a few install of it... d'oh! still, woulda been cooler if promise provided one for use in debian based installs ;-)

Thanks again!

--
John Minadeo
johnminadeo at hotmail dot com

---

### Post by JohnMinadeo on 2006-06-18
I checked the ability to run it in live mode, and I can not. If I choose Start or Install Ubuntu It pulls up the pretty Ubuntu splash screen, "Loads Essential Drivers" and the begins "Decompressing Kernel" which it never finishes. If I wait long enough the pretty screen is replcaed by the standard full screen console window with "Decompressing Kernel..." at the top and it doesn't go any further.

Would it be feasible to install Ubuntu to a VMWare virtual machine, and convert (or build) the driver on that then use it during the install?

Thanks!

--
John Minadeo
johnminadeo at hotmail dot com

---

