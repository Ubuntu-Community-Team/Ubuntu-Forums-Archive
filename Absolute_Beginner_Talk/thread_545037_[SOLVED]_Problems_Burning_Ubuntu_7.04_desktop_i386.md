---
title: "[SOLVED] Problems Burning Ubuntu 7.04 desktop i386 disc"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by sporry on 2007-09-07
I downloaded Ubuntu 7.04 desktop i386 iso from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The size of the ISO image is 697MB. I have checksumed it with HashTab and it matched up correctly. I have looked at guides for burning the iso image to a CD for imgburn and InfraRecorder.

First of all I burnt the iso with Nero. It burnt fine, but when I placed the CD in my drive and it autoloaded it would load the splash image for Ubuntu, but not load this window [http://img405.imageshack.us/my.php?image=iso20he7.png](http://img405.imageshack.us/my.php?image=iso20he7.png)  with the windows programs on it. It would just produce an error for start2.exe and lock up.

So I decided to try burning the iso with imgburn. When I loaded the image to be burned in the program it showed the size to be 731,797,504 bytes, above the 700MB CD size limit. But I decided to burn it anyway. It progressed fine but problems started when verifying. At about 92% of verifying it produced an error for ClamwinSetUp.exe. I pressed try again but the same error came up. I ignored the error but then the same error started to appear for FirefoxSetup.exe. I aborted it and ran the disc as it was, again it produced the Ubuntu splash image, but didn't bring up the windows programs browser and it locked up.

I then decided to burn the iso using InfraRecorder at a speed of 8x. It showed it was under 700MB.  It seemed to burn fine but when burning ended and I went to load the disc it appeared the CD was empty. I  then fixated the disc which brang up the files but the same thing happens again: it produced the Ubuntu splash image, but didn't bring up the windows programs browser and it locked up.

To me it seems the disc isn't burning the windows programs properly. I haven't tried booting with any of the discs burnt because I'm not sure if it's even worth it if the discs are corrupted already.

Can anyone please help me burn this ISO properly. I'm getting desperate. Thankyou in advance for your time.

---

### Post by BrendanM on 2007-09-07
I'm not sure about the issues with the windows programs, but if you boot from the disc, before the system even starts up, there's an option to verify the integrity of the disc. So I'd say just do that before you start the OS from the disc.

Also, I've found that Linux installs are pretty resiliant to bad discs, especially the text installer. I've had it crap out halfway through the install and leave me with just a command prompt, but as long as the network connection and apt are working, you can just **apt-get install ubuntu-desktop** to get a working system.

---

### Post by Emeric Wood on 2007-09-07
When my friend was trying to burn his Iso, it also failed when he did it in Nero. When we did it in [http://infrarecorder.sourceforge.net/]("http://infrarecorder.sourceforge.net/") via [https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto") and it worked fine. I'd say try Infrarecorder.

---

### Post by domat00 on 2007-09-07
burn it at a rate under 4x, in infrarecorder, click these options and leave the others unmarked:  verify disc after writing; pad data tracks; buffer underrun protection; and in the advanved options, click:  the one labeled Yamaha Audio Master Q.R., and that's IT.  try that when you fully blank your disc (if it's a live CD, use a CD, not a DVD), and it should burn it correctly.  also, try a BRAND new disc, not one that you've used before.  sometimes you create coasters.  :lolflag:

---

### Post by sporry on 2007-09-07
Thanks for the replies. I'll give it a go domat00.

---

### Post by sporry on 2007-09-07
I burnt the iso again with domat00's settings, which burnt ok but still came up with errors when I loaded up the disc.

I booted up all four iso images I have burnt so far and chose the "check the CD for defects" option and all produced errors.

Think I'll go download it again :(

---

### Post by dptxp on 2007-09-07
Make sure that iso is correct by downloading using torrent. Open torrent (a file of about 25 kb, you will see on download page).Point (in torrent client) to existing iso and only parts that have errors shall be replaced, no need for full iso again.

Download and install bittorrent in Windows first to use torrent file.

Download and install Infrarecorder, Burn using ACTIONS>BURN UMAGE. (No BOOT CD or DATA CD).
Change no settings in InfraRecorder, let burn in auto speed mode (at about 18-20X).
No need to go down to 4X.
__________________

---

### Post by svalding on 2007-09-07
This is most definitely a case of a bad .iso image, even if the checksum turned out ok. Redownloading the ISO should most definitely solve your problems.

---

### Post by sporry on 2007-09-07
Well I downloaded the image again from another mirror and burnt the image using InfraRecorder. Still the same result :(:(:(:( There seems to be a problem with "start2.exe" in all 5 images I have burnt. Also it seems all the 2 images I have downloaded are over 700MB which is very bizarre.

Not sure what I'm doing different to everyone else. It is very frustrating and isn't giving me a very good first impression of Ubuntu unfortunately. Anyone have anymore suggestions?

Just want to add, the iso's I download say they are under 700MB when I download them but when I view their size in windows it shows they are over 700MB.

---

### Post by Terl on 2007-09-07
Is your computer set to boot from the cd?  If not, you need to enter your bios and set the pc to have boot from cd before boot from hard drive.  The image you showed in your first post is what comes up when the cd auto-plays in windows.

---

### Post by justinreeves16 on 2007-09-07
I had mad problems burnings iso also, it turned out in the end I just had to try differernt downloads until I got one with no flaws.

---

### Post by sporry on 2007-09-07
> **Terl said:**
> Is your computer set to boot from the cd?  If not, you need to enter your bios and set the pc to have boot from cd before boot from hard drive.  The image you showed in your first post is what comes up when the cd auto-plays in windows.

Yes, I have all of that set. That image in my first post fails to show up.

---

### Post by Terl on 2007-09-07
It won't load that image.  It will load an image that says Ubuntu and has a menu below it, the first choice being to start Ubuntu.  What exactly are you getting?  

[EDIT]  I rechecked the thread and see you do see the initial Ubuntu image but then get the error.  Could you post your system specs so we could evaluate those as well?

---

### Post by sporry on 2007-09-07
oh, well when I boot up my PC with the CD in, it produces the Ubuntu logo with options underneath it like you said. I go to the "check the CD for defects" option and it produces an I/O error and asks me to reboot. To me that shows the burn it corrupted. I don't want to install it if it's a damaged burn.

---

### Post by Terl on 2007-09-07
If you are using the regular Ubuntu cd and not the alternate cd, press start and let it load ubuntu.  That should take it all the way to the desktop and let you at least test it out.  The option to install if you like it is on the desktop.  It is worth a try as it may be just fine.

I never tested my Ubuntu disk I burned and it installs the same way the one I got from Ubuntu does - no problems.  I am not saying the failure is true or false.  I know once when I tried Fedora I checked the disks and they failed but Fedora installed and ran without issue.

---

### Post by sporry on 2007-09-07
I finally got a good burn. Apparently it was the discs I was using. I used different discs in Nero and it worked perfectly.

Thanks for everyone's help :)

---

