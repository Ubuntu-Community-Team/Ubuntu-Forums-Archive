---
title: "Booting From CD Fails"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by PeterE on 2006-08-13
For some time I have running XP and an old copy of Mandrake. I wanted to update Linux so have tried to look at the options (use Mandrake version of Grub and have my hdb partitioned). No problems booting/installing with CD's from Knoppix and Suse but CD from Ubunto, Gentoo and Linspire all fail to boot in the same way. They all apparently boot OK and loads the applications, then the PC seems to close down (screen goes black and the Linux applications seems to (from the lights on the CD) reload but the screen remains black and no input will be accepted.  Can anyone help??

---

### Post by Drakkor on 2006-08-13
Can you get to the 2nd option to "Check the CD for defects" ?

---

### Post by PeterE on 2006-08-13
I dont think so as after loading it just switches off and restarts with that blank screen

---

### Post by MaximB on 2006-08-13
you should check the sums
maybe you burned it wrong (you need to burn iso not copy it)
or it has some defects

---

### Post by taurus on 2006-08-13
If after booting and your monitor goes blank, then it means there is a problem with your graphic card!  Therefore, I recommand you download and use the alternate CD to install Dapper on your machine then.  It's a text base installer and it should have everything that the desktop has.  After installing it, you can reconfigure your X is you are still exxperiencing a problem with it.

---

### Post by Drakkor on 2006-08-13
I agree with both other posters,check that the md5 sums match your iso,and burn that as an image file. If that isn't it I suspected it might be your video card that needs configuring. Try the alternate text-based install.  Good Luck ! :)

---

### Post by PeterE on 2006-08-13
Thanks  - will do every thing suggested and will get back we done (not today).  The check CD option did not display anything but wound through the CD so it seems as though it might be the graphic card a Nvidia GEForce FX5200  Will first check the checksum under kernal in mandrake  Peter

---

### Post by Macrorip on 2006-08-14
Oh, man, same video card same problem. I don't think it's the install cd since I recieved an official copy in the mail. It's gotta be the display driver, which seems to be the consensus from what I've been reading. Does anyone know how to install the driver from the command line, as that is the only entry point I can get to? I can't even get to the graphical login screen.

---

### Post by PeterE on 2006-08-15
Downloaded the alternative and checked the checksum which was OK but when trying to instal it in the text mode fails after about one minute with just a quick red flash on blank screen saying " Not Supported" - no idea what is not supported.  When coming back to Windows the display had gone high and to the left by about two inches.  Reseting the resolution fixed that problem so I also now think it is something to do with the graphic driver. Can only assume that Knoppix and Mandrake incorporate the correct driver (as both of them work) but that Ubunto, Gentoo and  Linspire incorporate the wrong product.  Assume I cannot do a thing to rectify as it would need the working driver to be built into the iso file.  Has anyone else any ideas.    p.s. My machine is a 2,4 Celeron useing a Nvidia Geforce FX5200 Graphic card to drive modern (cant remember the initials) digital flat 19in screen.  Peterhttp://ubuntuforums.org/images/smilies/icon_confused.gif
:???:

---

### Post by PeterE on 2006-08-19
Have not had a solution so will now restate the update complete problem. For some time I have running XP and an old copy of Mandrake. I decided to update the Linux software so have tried to look at some of the options. No problems booting/installing with CD's from Knoppix and Suse but CD’s from Ubunto, Gentoo and Linspire all fail to boot in the same sort of way. They all apparently boot OK and load the Kernel but then the screen seems to close down ( goes black and the Linux applications seems to (from the lights on the CD) reload but the screen remains black and no input will be accepted.  Have downloaded the alternative and checked the checksum on both CD’s which are OK and tested them on a neighbours PC with no problems. With my machine when trying to install the alternative in the text mode it fails after about one minute with just a quick red flash on blank screen saying "Not Supported" - no idea what is not supported. When coming back to Windows I find that the display had gone high and to the left by about two inches. Reseting the resolution fixed that problem.
 I think the failure is either something to do with the graphic driver or the fact I have my second hard drive partitioned for Linux and boot (if no  CD’s present) into the Mandrake version of Grub i.e. HDB1/boot/grub. Can only assume that Knoppix and Mandrake incorporate the correct driver (as both of them work) but that Ubunto, Gentoo and Linspire incorporate the wrong product. Assume I cannot do a thing to rectify as I know of no way of getting the correct driver to be built into the iso file. Or is it that these failing builds  are getting confused as my Linux partitions are not on the first HD 

 My machine is standard (except for the second HD which used to be in my previous machine) about 18 months old running a 2,4 Celeron processor using a Nvidia Geforce FX5200 Graphic card to drive TFT flat 19in screen. The Nvidia Windows software is up to date.  Can anyone help??

---

### Post by mgmiller on 2006-09-20
From your description, I suspect the video card is outputting an out of range signal for your flat panel monitor.  They are very picky, especially about refresh rates and if an out of range signal is sent, the screen just goes black.  Try hooking up an old CRT monitor if you can get your hands on one and see if it doesn't work.

---

