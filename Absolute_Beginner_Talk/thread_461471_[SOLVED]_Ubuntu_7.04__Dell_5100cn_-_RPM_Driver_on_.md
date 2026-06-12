---
title: "[SOLVED] Ubuntu 7.04 / Dell 5100cn - RPM Driver on CD"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by crjackson on 2007-06-01
I have a fresh install of 7.04 and a USB printer connection to my Dell 5100cn color laser printer.  The Dell site states Linux supported but I couldn't find a driver there.

Checking the CD I find a Linux directory and an RPM file for the driver.  Will this RPM driver version work or will it mess up my OS install?

Do I simply click on the RPM file to load the driver?  Someone clue me in on how one loads a driver or native program in Linux.  I would prefer a graphical interface if possible.

Thanks

---

### Post by HereInOz on 2007-06-01
The M5200 driver is already listed in the printer database - have you tried installing that?  It may or may not work, but it is worth a try.
System > Administration > Printers and follow your nose.

If you need to use the driver from dell, then the first thing you will need to do is to install a program called "alien" (in Synaptic) which will give you (command line I think - sorry!) the capability to turn the rpm into a deb.  

After that, you are on your own from my point of view as I have never actually installed a new printer driver in Ubuntu - they have always been there already, but this may get you started.

---

### Post by crjackson on 2007-06-01
Okay, thanks for the information.  I really had no idea where to start at all.  I've only booted the OS a total of 3 times now and don't know much about anything Linux at all.

Thanks for the response, that'll give me a starting point.

---

### Post by crjackson on 2007-06-02
Well I give up.  I can't get printer to work and I can't use Ubuntu without a printer.

I guess I'll reload windows now...

---

### Post by crjackson on 2007-06-04
> **HereInOz said:**
> The M5200 driver is already listed in the printer database - have you tried installing that?  It may or may not work, but it is worth a try.
System > Administration > Printers and follow your nose.

If you need to use the driver from dell, then the first thing you will need to do is to install a program called "alien" (in Synaptic) which will give you (command line I think - sorry!) the capability to turn the rpm into a deb.  

After that, you are on your own from my point of view as I have never actually installed a new printer driver in Ubuntu - they have always been there already, but this may get you started.

Thanks for your help.  I did manage to install Alien and convert the file to a DEB type file.  The resulting file didn't work however.  For the life of me and can't even figure out how to make Alien thing work all the time.  It never seems to be able to find the file and telle me something about ROOT.

I never did figure that out but after hours of trying I did something correct, because it converted the file for me.  I don't even know how to duplicate my accomplishment.

I guess it doesn't matter since I'm still stuck to windows since ubunto can print.

Thanks for trying.

---

### Post by crjackson on 2007-06-06
> **HereInOz said:**
> The M5200 driver is already listed in the printer database - have you tried installing that?  It may or may not work, but it is worth a try.
System > Administration > Printers and follow your nose.

If you need to use the driver from dell, then the first thing you will need to do is to install a program called "alien" (in Synaptic) which will give you (command line I think - sorry!) the capability to turn the rpm into a deb.  

After that, you are on your own from my point of view as I have never actually installed a new printer driver in Ubuntu - they have always been there already, but this may get you started.

Thanks for your help.  I finally got it working.  What a PITA...

---

