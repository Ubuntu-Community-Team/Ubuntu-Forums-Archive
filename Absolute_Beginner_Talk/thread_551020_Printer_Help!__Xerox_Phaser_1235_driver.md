---
title: "Printer Help!  Xerox Phaser 1235 driver"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by alecwh on 2007-09-14
NO idea how to do it... ubuntu detects the printer (Xerox Phaser 1235), but when I click "next" there is no driver for it...

Can someone help?

---

### Post by linuxwizard on 2007-09-14
I don't see that printer even listed.
[http://www.openprinting.org/printer_list.cgi?make=Xerox](http://www.openprinting.org/printer_list.cgi?make=Xerox)

Searched the forum could not come up with anything on Xerox Phaser 1235. Not sure what to tell you would not count on it working in Linux no drivers.

Linux Foundation Forum Xerox Printers don't see anything on Xerox Phaser 1235 
[http://forums.openprinting.org/list.php?32](http://forums.openprinting.org/list.php?32)

---

### Post by Daveth on 2007-09-14
Xerox have their own Unix drivers for this printer, which are here:

[http://www.support.xerox.com/go/results.asp?Xlang=en_US&XCntry=USA&prodID=1235&ripId=&Xtype=download](http://www.support.xerox.com/go/results.asp?Xlang=en_US&XCntry=USA&prodID=1235&ripId=&Xtype=download)

from which this CUPS PPD file seems most relevant to Ubuntu:

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=1235&Family=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=1235&Family=)
Phaser&ripId=&langs=English%20(US)&plats=UNIX&Xtype=download&uType=

What you will have to hunt down in the forum is how PPD files integrate into CUPS - is it just a question of loading this file and off you go? Anyone know??

---

### Post by Daveth on 2007-09-14
just found this, which points a way forward:

[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

---

### Post by alecwh on 2007-09-14
Hey!

Thanks so much for your responses. I'm completely new to linux, I'd really appreciate a walk-through on this. :)

I got those links, but have no idea what to do. can anyone help?

Thanks in advance!!!

---

### Post by Maestro23 on 2007-09-14
> **alecwh said:**
> Hey!

Thanks so much for your responses. I'm completely new to linux, I'd really appreciate a walk-through on this. :)

I got those links, but have no idea what to do. can anyone help?

Thanks in advance!!!

You're going to need to type those commands in from a terminal.  Also you will need to use "sudo" in front of some of them.  RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by alecwh on 2007-09-14
> **Maestro23 said:**
> You're going to need to type those commands in from a terminal.  Also you will need to use "sudo" in front of some of them.  RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

Hey. Thanks a lot, but I don't see any commands.

---

### Post by Daveth on 2007-09-14
this bit of that..

Save the PPD file in the directory /usr/share/cups/model/ (this may be a different location for you, but it will be called "something/cups/model/"). The PPD file does not need to be executable, but it should be world-readable and should have the file name extension ".ppd". 
3. 	Restart the CUPS daemon.

Log in as root and enter one of the following commands: 
killall -HUP cupsd
/etc/init.d/cups restart
/etc/software/init.d/cups restart

---

### Post by alecwh on 2007-09-14
Ok, where am I getting the PPD file? I'm not sure where that is... can you help me find it?

---

### Post by Maestro23 on 2007-09-14
> **alecwh said:**
> Ok, where am I getting the PPD file? I'm not sure where that is... can you help me find it?

From the link Daveth provided:[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

>  2. 	Install a PPD file.

CUPS requires a PPD file to define how it will use the printer and driver (if any). PPD files come from several sources, be sure you get yours from the right place:

If you have a PostScript printer
    Obtain the PPD file from your printer's vendor. Typically it will be carefully hidden somewhere in your vendor's "driver" for Windows. We also distribute some PPD files here. You do not need a driver (Step 1), just the PPD file. 
If you do not have a PostScript printer
    There are two sources for non-PostScript printer PPDs under CUPS: 

If your printer uses a CUPS Raster driver (Gimp-Print for CUPS, samsung's lpp kit, etc)
    Use the PPD file that came with the driver. Gimp-print, for example, will generate and install a set of PPD files at compile time. 
If you have any other style of driver
    Obtain a PPD file from this website for the driver you want to use. Look for "download PPD" links near the driver names on your printer's page. If a driver has no "download PPD" link, there is insufficient data to generate a PPD for the entry; in that case, see the text of the driver entry. 

Save the PPD file in the directory /usr/share/cups/model/ (this may be a different location for you, but it will be called "something/cups/model/"). The PPD file does not need to be executable, but it should be world-readable and should have the file name extension ".ppd". 

---

### Post by alecwh on 2007-09-14
Ok. I have the file, and I just restarted the deamon. Will it appear in the printer drivers list?

---

### Post by Daveth on 2007-09-14
that is from the link in my first post to you- on Xerox's own site. Select Unix as the operating system, hit go, and look for the ppd- the first option on that list. follow that link, and it takes you to a page with

PPD Files using CUPS Printing Services
Filename: CupsPrinterPkg2007_May_10.tar
Version: 2007_May_10 
Date: 7/18/2007
Size: 4.1MB

download this file and put it into the  /usr/share/cups/model/  folder.
OK?

---

### Post by alecwh on 2007-09-14
Ok, done!

I did the terminal thing, got this:

> 
alecwh@aleclaptop:~$ killall -HUP cupsd
cupsd(12384): Operation not permitted
cupsd: no process killed
alecwh@aleclaptop:~$ /etc/init.d/cups restart
bash: /etc/init.d/cups: No such file or directory
alecwh@aleclaptop:~$ /etc/software/init.d/cups restart
bash: /etc/software/init.d/cups: No such file or directory
alecwh@aleclaptop:~$ 



---

### Post by Daveth on 2007-09-14
looks like you tried to kill it as "alec" rather than as "root", so you need to become a superuser and use "sudo" in front, as Maestro23 noted a few posts back.
Nearly there!

---

### Post by Maestro23 on 2007-09-14
> **Daveth said:**
> looks like you tried to kill it as "alec" rather than as "root", so you need to become a superuser and use "sudo" in front, as Maestro23 noted a few posts back.
Nearly there!

Baby steps.. Baby steps.. :smile:

---

### Post by Daveth on 2007-09-14
just noticed it has got to midnight here, so I'll have to hand you over the folk in better time zones! Good luck and good night.

---

### Post by alecwh on 2007-09-14
nearly there. :)

I did sudo, but only one of the commands worked...

> 
alecwh@aleclaptop:~$ sudo killall -HUP cupsd
Password:
alecwh@aleclaptop:~$ /etc/init.d/cups restart
bash: /etc/init.d/cups: No such file or directory
alecwh@aleclaptop:~$ sudo /etc/init.d/cups restart
sudo: /etc/init.d/cups: command not found
alecwh@aleclaptop:~$ sudo /etc/init.d/cups restart
sudo: /etc/init.d/cups: command not found
alecwh@aleclaptop:~$ sudo /etc/software/init.d/cups restart
sudo: /etc/software/init.d/cups: command not found
alecwh@aleclaptop:~$ sudo /etc/init.d/cups restart


---

### Post by Maestro23 on 2007-09-14
> **alecwh said:**
> nearly there. :)

I did sudo, but only one of the commands worked...

Like the docs said, it depends on the linux distro you're using.  For Ubuntu I believe it will be:

> sudo /etc/init.d/cupsys restart

---

### Post by halitech on 2007-11-21
Why not just download the PPD files from the xerox website ( [http://www.support.xerox.com/go/results.asp?Xlang=en_US&XCntry=USA&prodID=1235&ripId=&Xtype=download](http://www.support.xerox.com/go/results.asp?Xlang=en_US&XCntry=USA&prodID=1235&ripId=&Xtype=download) ) and use the add printer to add it and point it at the PPD when it asks to select the model of printer?

edit: just save the file to your desktop, extract it and then do the add printer thing :)

---

