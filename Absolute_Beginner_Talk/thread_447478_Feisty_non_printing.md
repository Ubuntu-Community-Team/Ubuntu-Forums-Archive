---
title: "Feisty non printing"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Hope on 2007-05-18
OK, I've been trying and trying to get my printers working.
Current status is; hp laserjet 1000 is now recognised and says its printing whatever is sent but then nothing happens. Printer properties show status as '> ready; usb printer is busy, will retry in 5 seconds'. but there are no other jobs, be they test prints or normal jobs.

I retried to set up the epson me1+(local chinese model) and actually got it to the stage where it sent the job and the paper started flowing thru..........but it won't stop. Have to turn off the machine to stop it! Managed to get it working by saying it was a 'new stylus'. But its only half working.
Don't want to buy another machine if this is not a printer problem!!

The laserjet works with XP

AAARRRGGGHHH, sob,sob,:confused:
Thanks to everyone for your help up to now and here's hoping there's something simple thats wrong and can be fixed as simply.
Hopeful.

---

### Post by victorbrca on 2007-05-18
Not sure how you got this far.... But two links that may help you are:

[**_Your local cups configuration_**]("http://localhost:631/")

[**_Driver Information_**]("http://openprinting.org/printer_list.cgi")


Vic.

---

### Post by dstew on 2007-05-18
I am not a printer expert, but [this page]("http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000") has some good advice for setting up an HP laserjet 1000 in Linux.

---

### Post by Hope on 2007-05-18
Sorry I wasn't clear about  what I had done previously, I've been thru the driver thing and I have it all,... and more.
Printer just won't print.
		this is what the online CUPS shows;

> LaserJet-1000
	
  Home      Administration      Classes      Documentation/Help      Jobs      Printers  
  	
LaserJet-1000 (Default Printer)
	Description: LaserJet-1000
Location:
Make and Model: Local Raw Printer
Printer State: processing, accepting jobs, published.
Device URI: usb://HP/LaserJet%201000

Print Test Page Stop Printer Reject Jobs Move All Jobs Cancel All Jobs Unpublish Printer Modify Printer Set Printer Options Delete Printer Set As Default Set Allowed Users
Jobs

Search in LaserJet-1000: Clear

Show Completed Jobs Show All Jobs

Showing 1 of 1 active job.
  	Sort Descending 	 
ID  	Name  	User  	Size  	Pages  	State  	Control 
LaserJet-1000-41  	Test Page  	sirbarry  	150k  	1  	processing since
Sat 19 May 2007 08:37:19 AM CST  	Reprint Job Cancel Job Move Job  
  	Sort Descending 	 
	 
	

The Common UNIX Printing System, CUPS, and the CUPS logo are the trademark property of Easy Software Products. CUPS is copyright 1997-2007 by Easy Software Products, All Rights Reserved.
	

Basically everything says the job is printing but nothing is happening. Printer light is on, has paper, toner etc.
I don't know what to do next.
Thanks

---

### Post by dstew on 2007-05-19
You don't have the correct driver installed. The Make and Model line shows just a generic print driver. You have to install the open-source HP driver. I was able to pick it from a list in the CUPS Administration tool when I installed. I have a LaserJet 1200, and my CUPS administration looks like this:
Description: HP Laserjet 1200
Location: Downstairs
Make and Model: HP LaserJet 1200 Postscript (recommended)
Printer State: idle, accepting jobs, published.
Device URI: smb://MARYS/Printer2

Of course, my device is a Samba shared printer, and yours is a USB printer, but the driver is the important thing. In CUPS administration, go to the Modify Printer dialog. Click continue until you get to the Make/Manufacturer page. On the pick list, go to the HP tab (**not** the Hewlitt-Packard tab). Select the HP LaserJet 1000 Foomatic/foo2zjs (recommended) line, click Modify Printer and you should be good to go. If you do not have the foo2zjs driver available, you can get it [here]("http://openprinting.org/show_driver.cgi?driver=foo2zjs"). You can also use Synaptic to install the foomatic HP drivers. The package name is foomatic-db-hpijs.

---

### Post by Hope on 2007-05-19
Hi Dstew, thanks for your help.
yesterday I tried to setup another printer on CUPS (actually the same printer)  	so now I get this;

Search in Printers: Clear

Showing 2 of 2 printers.
  	Sort Descending 	 
HP_LaserJet_1000_USB_ (Default Printer) "open device failed; will retry in 30 seconds..."
	Description: HP LaserJet 1000
Location: Local Printer
Make and Model: HP LaserJet 1000 Foomatic/foo2zjs (recommended)
Printer State: processing, accepting jobs, published.
Device URI: hp:/usb/hp_LaserJet_1000?serial=?

Print Test Page Stop Printer Reject Jobs Move All Jobs Cancel All Jobs Unpublish Printer Modify Printer Set Printer Options Delete Printer Set As Default Set Allowed Users
LaserJet-1000
	Description: LaserJet-1000
Location:
Make and Model: Local Raw Printer
Printer State: idle, accepting jobs, published.
Device URI: usb://HP/LaserJet%201000

Print Test Page Stop Printer Reject Jobs Move All Jobs Cancel All Jobs Unpublish Printer Modify Printer Set Printer Options Delete Printer Set As Default Set Allowed Users
  	Sort Descending 	 
	 
	

The Common UNIX Printing System, CUPS, and the CUPS logo are the trademark property of Easy Software Products. CUPS is copyright 1997-2007 by Easy Software Products, All Rights Reserved.

Also the attached screenshot shows synaptics record of what I have installed regarding this.
All the advice I've received so far I've followed, but this alleged printer beside me just will not print! My hair is greying daily.
I'm grateful for your help else I may have already fallen on my sword.

---

### Post by drs305 on 2007-05-19
In posts 4 and 6, how are you guys getting that data to display? 

I get to CUPS via System, Admin, Printing, but don't know how to gather the information you posted...

Thanks.

By the way, Hope, did you ever try my entry #11 in your earlier post about this? I only ask because today I reinstalled Feisty and after many failed attempts which mirror what you described above I followed my own advice and my printer started working again. I really didn't think it was necessary since I had an intact previous /home directory and foo2zjs was already installed, but when I ran through the steps my HP1000 started working. I don't know why, but it did.  The post I am referring to is: 
[http://ubuntuforums.org/showthread.php?t=429323](http://ubuntuforums.org/showthread.php?t=429323)

---

### Post by Hope on 2007-05-20
Hi drs305, thanks for your help, yes I did try it and I got this from ./getweb 1000;
> Archive:  lj1488en.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of lj1488en.exe or
        lj1488en.exe.zip, and cannot find lj1488en.exe.ZIP, period.
and then this;
> sirbarry@main:~/ComputerStuff/foomatic/foo2zjs$ sudo make install-hotplug
[ -d /etc/hotplug/usb ] || install -d -m 755 /etc/hotplug/usb/
install -c -m 755 hplj1000 /etc/hotplug/usb/
ln -sf /etc/hotplug/usb/hplj1000 /etc/hotplug/usb/hplj1005
/etc/hotplug/usb/hplj1000 install-usermap
/etc/hotplug/usb/hplj1005 install-usermap
sirbarry@main:~/ComputerStuff/foomatic/foo2zjs$ sudo make cups
make: *** No rule to make target `cups'.  Stop.
so it doesn't finish right and I can't edit the non-existent hotplug file.
I don't know how to remedy this missing bit. I did post this error before.

---

### Post by drs305 on 2007-05-20
I just duplicated the commands I posted and it still ran okay. Let me give you some specifics:

When I ran the following command the file was downloaded to the terminal directory I started in.
```
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
```
I get a 1.4MB file named foo2zjs.tar.gz 

I then run the following from the location where the file resides:
```
tar zxf foo2zjs.tar.gz
```
which results in a foo2zjs folder created in the same directory. The folder has 66 items and properties show 214 files and 5.4MB total.

I then run the following to move the folder foo2zjs to my home directory and then move the terminal  into the foo2zjs directory  ( in my case, /home/drs2/foo2zjs ):
```
mv foo2zjs /home/drs2
cd /home/drs/foo2zjs
```
I now have a folder foo2zjs located in my ~/ directory  (e.g. /home/drs2/foo2zjs  )

From the terminal prompt, when I type "dir" the first file I see is ' align.ps ' and the last file is ' zjs.h ' .
Ensure you are starting in the correct folder. Run the following commands:
```

make 
./getweb 1000 
sudo make install 
sudo make install-hotplug 
sudo make cups

```

I don't get any errors when I run ' ./getweb 1000  '. Assuming we both downloaded the same file and ran the same commands from the same directories, I don't know why you would get errors.  If you get this far, simply run the remainder of the commands from the earlier post.

By the way, I'd still like to know how you got the printer information to display.

If you are willing to try again, or even if you are not, good luck with your printer.

---

### Post by stripe4 on 2007-05-20
I had the same problem with USB connected HP LaserJet 1200. Solved the problem by changing the recommended "Postscript" driver with "hpijs".

---

### Post by drs305 on 2007-05-20
> **stripe4 said:**
> I had the same problem with USB connected HP LaserJet 1200. Solved the problem by changing the recommended "Postscript" driver with "hpijs".

That would certainly be easier. How do you do that? That wasn't through CUPS was it?

---

### Post by Hope on 2007-05-26
Hi DRS305, I've finally got back. I did try that command again and this time, yes, I followed it step for step. Last time I had a copy of the file from a USB flash disc.
Your command series finished without error this time.
However I can't try it out on the laserjet at the moment as I've got another printer to try, an Epson Stylus C41UX and it works sweet, maybe I can keep it!
thanks for all your help, btw, the access to CUPS is thru one of the links in this thread, I think you can get there thru the linux foundation site.
Barry.

---

