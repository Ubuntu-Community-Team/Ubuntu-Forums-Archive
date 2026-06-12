---
title: "Newbies! Install a Lexmark printer this way!"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-22
To all newbies: Every day for the last two weeks, I have seen people posting about their Lexmark printers. They have tried all the tips that have shown up on this board, and nothing has worked. They are ready to give up.

I was in that place until last night. I have a Lexmark Z517, which was deemed a paperweight. I had tried all the instructions posted here, and nothing had worked.

Then I found this page: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkMultifuncPrinters)

I followed it to the letter, and despite the fact that my printer is neither a multifunction printer nor listed as being supported in the instructions, it worked like a charm.

If you have any kind of Lexmark, take a break from scouring these forums for a second and try that howto.

---

### Post by gottatrieit on 2007-06-24
I can't seem to get my X5470 to work using this method.  I unhooked my 605 and re-hooked the usb line to the 5470.  My machine recognized it, but I can't print from it.
   When I try, I get the following message in the printer pop-up box:  
    paused: job-hold-until-specified

     Any ideas where I need to fix this?

                        Thanks.

---

### Post by samuraiCat on 2007-06-24
> **gottatrieit said:**
> I can't seem to get my X5470 to work using this method.  I unhooked my 605 and re-hooked the usb line to the 5470.  My machine recognized it, but I can't print from it.
   When I try, I get the following message in the printer pop-up box:  
    paused: job-hold-until-specified

     Any ideas where I need to fix this?

                        Thanks.

Yeah, I actually have a X5470 sitting next to the Z517, and I can't get that printer to do a darn thing. I have a feeling it may take some more research.

---

### Post by gottatrieit on 2007-06-25
[FONT="Comic Sans MS"]RATS![/FONT]Getting that X5470 to work with Ubuntu is the only thing holding my wife back from letting me install it on her XP machine!  She wants to be able to print and copy to her machine like she can now.

 OH WELL!  I can wait a little longer.

     Thanks for the input, samurai.

---

### Post by kevdog on 2007-06-25
I too have a Lexmark X5470 and gave up trying to make it work.  I dont think they make any drivers for this model.  Its a shame too.  Have to keep my Windows box up and running with Samba in order to use it.

---

### Post by samuraiCat on 2007-06-25
I'm going to try a different approach: I'm going to find a standalone image scanning application for windows, and I going to try to run it in WINE. That way, I might be able to at least scan with it.

Failing that, I'll just go buy a new multifunction box.

---

### Post by wolfen69 on 2007-06-25
install virtualbox, put xp on. then you can print without using a different machine.

---

### Post by samuraiCat on 2007-06-25
> **wolfen69 said:**
> install virtualbox, put xp on. then you can print without using a different machine. 

Well, I'm allready dual booting with XP, so if it comes down to that, I'll just do my scanning with XP booted. Thanks for the advice!

---

### Post by kevdog on 2007-06-25
Great suggestion about the virtualbox, -- never thought of that approach. Only problem for me is that my 5 year old laptop only has a 20gb drive, and no way can I squeeze on the total XP package.  Seems like overkill to me to install an entire OS (~ 4Gb) just for print drivers!

---

### Post by ricflomag on 2007-06-25
I have adapted the before mentioned how-to for it to install the Z55 driver. In my case, it is compatible with the multifunction printer X5150 (the scanner won't work though). Here it is:

```

sudo apt-get install alien
sudo apt-get install libstdc++5

cd Desktop
mkdir "lexmark z55 - remove me"
cd "lexmark z55 - remove me"
wget http://www.downloaddelivery.com/srfilecache/CJLZ55LE-CUPS-1.0-1.TAR.GZ

tar -xvzf CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
sudo alien -t z55llpddk-2.0-2.i386.rpm
sudo tar xvzf z55llpddk-2.0.tgz -C /
sudo tar xvzf lexmarkz55-CUPS-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
sudo /etc/rc2.d/S19cupsys restart

```

Then you'll have to go and install the driver: menu System -> Administration -> Printers, double-click on the "install printer" icon, select your printer, and at the second step, choose "install driver". Browse to "/usr/share/cups/model" and select the file "Lexmark-Z55-lxz55cj-cups.ppd". Now the Z55 printer should be available in the list of drivers inside the "Lexmark" section.

---

### Post by samuraiCat on 2007-06-25
> **ricflomag said:**
> I have adapted the before mentioned how-to for it to install the Z55 driver. In my case, it is compatible with the multifunction printer X5150 (the scanner won't work though). Here it is:

```

sudo apt-get install alien
sudo apt-get install libstdc++5

cd Desktop
mkdir "lexmark z55 - remove me"
cd "lexmark z55 - remove me"
wget http://www.downloaddelivery.com/srfilecache/CJLZ55LE-CUPS-1.0-1.TAR.GZ

tar -xvzf CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
sudo alien -t z55llpddk-2.0-2.i386.rpm
sudo tar xvzf z55llpddk-2.0.tgz -C /
sudo tar xvzf lexmarkz55-CUPS-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
sudo /etc/rc2.d/S19cupsys restart

```

Then you'll have to go and install the driver: menu System -> Administration -> Printers, double-click on the "install printer" icon, select your printer, and at the second step, choose "install driver". Browse to "/usr/share/cups/model" and select the file "Lexmark-Z55-lxz55cj-cups.ppd". Now the Z55 printer should be available in the list of drivers inside the "Lexmark" section.

Great! Man, I really wish I could get that scanner going. I'll find a way somehow!

---

### Post by claudio4j on 2008-03-25
Thanks ricflomag, those instructions works !

My system:
Kubuntu 7.10
CUPS server access lexmark x5150 at windows share
Lexmark X5150 connected at windows box (usb cable)

When using kcontrol to add the printer, don't expect the "Scan" to find your printer, just put the correct values (IP, printer name, workgroup).


[QUOTE=ricflomag;2910572]I have adapted the before mentioned how-to for it to install the Z55 driver. In my case, it is compatible with the multifunction printer X5150 (the scanner won't work though). Here it is:

```

sudo apt-get install alien
sudo apt-get install libstdc++5

cd Desktop
mkdir "lexmark z55 - remove me"
cd "lexmark z55 - remove me"
wget http://www.downloaddelivery.com/srfilecache/CJLZ55LE-CUPS-1.0-1.TAR.GZ

tar -xvzf CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
sudo alien -t z55llpddk-2.0-2.i386.rpm
sudo tar xvzf z55llpddk-2.0.tgz -C /
sudo tar xvzf lexmarkz55-CUPS-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
sudo /etc/rc2.d/S19cupsys restart

```

---

### Post by chewit on 2008-03-25
Seems like Lexmark printers are becoming usable. I posted a simlar thread to be able to get Z600 printers work. I even have provided the deb file drivers, for easy installing.

[http://ubuntuforums.org/showthread.php?t=679505]("http://ubuntuforums.org/showthread.php?t=679505")

---

### Post by heartburnkid on 2008-03-25
Wow, I've never been so glad to have an HP. :)

---

### Post by ashvee on 2008-03-26
please linux gurus develop a driver for x5470 so we all can ditch microsoft for ever 

is there any way to work the x5470 printer

---

### Post by Qiaozhi on 2008-04-27
> **claudio4j said:**
> Thanks ricflomag, those instructions works !

My system:
Kubuntu 7.10
CUPS server access lexmark x5150 at windows share
Lexmark X5150 connected at windows box (usb cable)

When using kcontrol to add the printer, don't expect the "Scan" to find your printer, just put the correct values (IP, printer name, workgroup).


[QUOTE=ricflomag;2910572]I have adapted the before mentioned how-to for it to install the Z55 driver. In my case, it is compatible with the multifunction printer X5150 (the scanner won't work though). Here it is:

```

sudo apt-get install alien
sudo apt-get install libstdc++5

cd Desktop
mkdir "lexmark z55 - remove me"
cd "lexmark z55 - remove me"
wget http://www.downloaddelivery.com/srfilecache/CJLZ55LE-CUPS-1.0-1.TAR.GZ

tar -xvzf CJLZ55LE-CUPS-1.0-1.TAR.GZ
tail -n +143 lexmarkz55-CUPS-1.0-1.gz.sh > install.tar.gz
tar -xvzf install.tar.gz
sudo alien -t lexmarkz55-CUPS-1.0-1.i386.rpm
sudo alien -t z55llpddk-2.0-2.i386.rpm
sudo tar xvzf z55llpddk-2.0.tgz -C /
sudo tar xvzf lexmarkz55-CUPS-1.0.tgz -C /
sudo ldconfig
cd /usr/share/cups/model
sudo gunzip Lexmark-Z55-lxz55cj-cups.ppd.gz
sudo /etc/rc2.d/S19cupsys restart

```
Brilliant! :biggrin:
I have a Lexmark Z55, and now it's working across the network to a Windoze machine.

---

### Post by AnthonyParker on 2008-05-30
I am facing the same problem myself.
Lexmark seems to be ignoring us altogether..
The sulotion of running Windows on a virtual machine (e.g., VMWare) is out of the question for me.. It takes hige amount of disk space, and further more I am not licensed to Window.
I have to say I find it very peculiar that hardware vendors does not release  drivers for Linux.
My conclusion is one:
Don't Buy Lexmark!

---

