---
title: "hplip and my HP mutlifunction printer"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by opexoc on 2006-09-06
Hi, I have bought a multifunction printer HP Photosmart C4180. For 3 days I still have been working on installing drivers to this device, however every method fail. Firstly, I noticed that I had 0.9.7 version hplip on my computer, and in this website [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4100](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4100) I found information that my printer is supported, but I should have installed newer version of hplip. So, on sourceforge.net I find 1.6.7 version of this driver and was trying to installing. I had some problems with dependencies, but this commend helped:

sudo apt-get install python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev

and I could execute: ./configure && make && checkinstall. After that I restart cups and hplip... but my printer did not work. So, I go to System->Administration->Printing and I wanted to add new printer... but I could choose only "Use another printer by specifying a port.", because no printer was detected. But, in this field I can chose beetwen only "LPT1 , Parallel Port(Canon), Parallel Port(EPSON) ". but my printer is plugged into usb port... Although, I tried to do so... with LPT1... and nextly with big databse I could choose C4100 Printer... It is not the same... but I think my printer fit into C4100 series. So... Printer was added but I could 
not still print. I change this port on Parallel(Canon) and nextly on Parallel(EPSON), but I could not still print. I tried to use CUPS. I went to [http://localhost:631](http://localhost:631) ... but there I really could not do anything good for me. 
Please help. Every help will be appreciated.
best,
opexoc

---

### Post by steve.horsley on 2006-09-06
I could be wrong, but I thought checkinstall created a .deb file rather than performing an install. With any luck, maybe all you need to do now is install the .deb you made?

---

### Post by Apple 101 on 2006-09-06
It would have been easier to uninstall the older version, and compile the more recent version, finishing with 'make install'.

---

### Post by opexoc on 2006-09-06
It seems that I should have used "make install". Now this was displayed:

opexoc@ubuntu:~/hplip-1.6.7$ sudo /etc/init.d/hplip restart
Stopping hpiod:                                            [  OK  ]
Stopping hpssd:                                            [  OK  ]
Starting hpiod:                                            [  OK  ]
Starting hpssd:                                            [  OK  ]

Furthermore... When I go to System->Administration->Printers then it looks that my printer was detected because I can choose HP Fax in "Use a detected printer" field. When I choose it then I can check HP C4100 ( My is C4180, but I assume that my printer is in set of C4100 series or something  ). I choose also Driver: hpijs ( recommended ) ( suggested ). When I want to click on INSTALL DRIVER button and want to load some PPD file which I downloaded, this program says that I have one so I can't load second. This is because I load this PPD file very earlier.

However, My printer still don't work. I really don't know why. Still please help. 

best,
opexoc

I can add that in Printers Window I see that under the Photosmart C4100 write "Ready".

---

### Post by steve.horsley on 2006-09-06
I can't help you with your non-printing problem, but I can confirm that you did the right thing in installing - select the recommended/suggested driver - the Install Driver button is for if you have a different driver you know works better (unlikely). You shoudl be able to see the pront quue status under printers/administration. And if the PC thinks there's stuff in the print queue, you should see a printer icon in the notification area on the taskbar.

---

### Post by sjhstorm on 2006-09-06
From a terminal type the following for automatic setup of your printer

sudo hp-setup -a

this should do the trick

---

### Post by opexoc on 2006-09-07
opexoc@ubuntu:~$ sudo hp-setup -a
Password:

HP Linux Imaging and Printing System (ver. 1.6.7)
Printer/Fax Setup Utility ver. 2.1

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.
error: Error occured during interactive mode. Exiting.

But this is really weird because when I go to System->Administration->Printing then this setup find soem HP device... so I really don't know what is going on.

Yes, when I want print some thing then some icon is displayed on task-bar, but it does not matter I think. 

What should I do in this terrible situation?
Maybe something is going wrong with CUPS? I am really beginner in ubuntu and linux generally.

---

### Post by useResa on 2006-09-07
I like to link my thread (Continuing HP Printer problems) to this thread. Maybe the two are related and hopefully this &quot;link&quot; will keep us both informed about solutions being provided.

The link to my thread is: [http://www.ubuntuforums.org/showthread.php?t=252287](http://www.ubuntuforums.org/showthread.php?t=252287)  

The main difference in the threads is - I think - the fact that my printer is shared through a Windows machine and in this case the printer is hooked up directly.

For the rest I think the problems seem similar. :-k Kind regards.

---

### Post by sjhstorm on 2006-09-07
One question, did you uninstall previous 0.9.7 version prior to installing latest version.

---

### Post by opexoc on 2006-09-07
yes.

---

### Post by useResa on 2006-09-08
I also had the previous version installed (came standard with the Ubuntu installation).  Kind regards

---

