---
title: "HPlaserjet setup but wont print"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Hope on 2007-05-01
Hi guys. I've searched thru these forums but without success to get this printer going.
Its a HP Laserjet 1000  running on Feisty. It tells me its printing but nothing happens.
It seems to recognise the printer but thats as far as it goes. I'm sure it just needs a nudge but where?
The recommended driver is installed. I've plugged into different usb connections, turned it off/on etc.:confused: 
any help welcome

---

### Post by Sef on 2007-05-01
Check out [LinuxPrinting]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000").

---

### Post by Hope on 2007-05-01
Hi Sef, thanks for your reply.
I checked that link but it all seems to be way out of date. The Feisty setup does all that stuff automatically (doesn't it?) and the files they refer to /etc/hotplug and so on aren't part of the current setup.
The current status of my printer is; > Printing: No %%BoundingBox: comment in header! whatever the heck that means but its obviously a problem.
I've already switched printers from Epson to HP because I thought that HP worked well with Linux.
Is there a more recent howto?
:(

---

### Post by deadgobby on 2007-05-01
MMMM It should be going. Lets take a look at this perspective. Is the printer on, is it full of paper, and toner good to go? If the printer is off. It will say that the printer is ready even though it is off.   Of all yes, then lets go this step.  Go back to System>Printing and right click on the printer icon. Scroll down to properties. It takes about a minute for the properties window to appear.  When that window pops up, Check all teh tabs and see if every thing looks good. Here is a sample of my printer properties.
Gobby

---

### Post by Hope on 2007-05-01
Hi DeadGobby, Thanks for your reply.
I've checked your screenshots and the only real differences I can see are in the connection tab and the general tab. In the screenshots I've attached it shows the printer is detected but in the general tab it shows the status error > no %%bounding box: comment in header it also fails to show any resolution?
The recommended driver is 'foo2zjs' which is installed by default.

---

### Post by deadgobby on 2007-05-03
Remove the location "Barrys Office". Or remove the printer and add it back and do not put Barrys Office as the location. Make sure the printer is on.

---

### Post by carrie.peary on 2007-05-04
I'm also having the same issues with a HP LaserJet 1020...it just won't print to it but will have items in queue. I followed what was above, but to no avail.

---

### Post by Hope on 2007-05-06
Hi DeadGobby, sorry to take so long to answer, I've been away. Now, I tried what you said and managed to delete the printer, (I think) but I can't add another. The app just hangs. I wait and wait but nothing happens. This is thru the system>admin>printing menu.
I do have another app called Print Job (CUPS) in the applications menu but there are no printers or jobs on it.
Should I uninstall and reinstall cups in synaptic? would that help or make it worse?:confused: 
Oh, yes, the printer is definitely on.
thanks.
not quite hopeless.
OK just found out that shutting down OpenOffice lets the printing app work. So now it shows (in add printer) that in 'local or detected' printers there are 'none detected'
Even I can see this is a large part of the problem.
How can I get it seen? Its not a network printer. Its connected thru USB, don't know the port number, sorry.

---

### Post by deadgobby on 2007-05-06
I think it is the USB port and the printer connection. So here is a link to see if this will work. Some very simple Terminal commands

[https://wiki.ubuntu.com/DebuggingPrintingProblems?highlight=%28printing%29](https://wiki.ubuntu.com/DebuggingPrintingProblems?highlight=%28printing%29)

---

### Post by drs305 on 2007-05-07
I'm having the same problem with the same printer as the original poster. The printer is recognized by Feisty and worked fine with Edgy. I've tried installing it as a network printer and as a standalone but can't get it to print anything. The job just sits in the queue. 

I wouldn't think it was a usb issue as the computer knows the HP 1000 is there. And 'lsusb' returns the device.

Clean install of Feisty w/ pre-established home directory, trying to install the printer via CUPS.

The cupsd.conf debug error_log has numerous entries: "cupsdAuthorize: Local authentication certificate not found!"

---

### Post by drs305 on 2007-05-07
Solved my problem, and maybe yours. If you have a Laserjet of approximately the same vintage just change the 1000 to whatever number your printer happens to be.

When I typed my "me too" entry, I began to think about how I set up my HP Laserjet 1000 in Edgy. I figured things would have been resolved with Feisty, but apparently not. Here are my notes from my Edgy installation, which I applied again in Feisty. I don't know if all the steps are necessary, but my printer is now working after doing them all.

```

		sudo aptitude install build-essential
		wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
		tar zxf foo2zjs.tar.gz 

```
I then moved the foo2zjs to my home directory and continued.

```
	
cd foo2zjs 
make 
./getweb 1000 
sudo make install 
sudo make install-hotplug 
sudo make cups

```

I then edited the following file:

```

gksudo gedit /etc/hotplug/usb/hplj1000

```

Commenting out the Set $DEV lines so they look like this:

		# Set $DEV to, e.g. /dev/usb/lp0, to force the device you want 
		# Else, leave it null to automatically detect the device 
		# DEV=/dev/usb/lp0 #DEV= ""

Next I created my HP Laserjet printer profile. You can do this via the menu or via the command line:

```
	
sudo gnome-cups-manager

```   

Finally, I selected Local printer, use detected printer, then turned the printer off and back on.

I would like to give credit to the author of a post I mostly found this solution on but don't recall where I found it.

Good luck.

---

### Post by deadgobby on 2007-05-07
Try installing through synaptic 
hpijs
hplip
hplip-data
 And reboot just for fun and try again.

---

### Post by Hope on 2007-05-10
Hi DeadGobby, thanks for you help.
Sorry to take so long but I don't get a lot of time in my office lately.
I tried the howto and got the stuff as you'll see in the attached.
Basically it seems foo2zjs is lacking the file sihp1000.dl in the firmware folder, ie /usr/share/foo2zjs/firmware.
Any idea where I can get this particular file so I can stick it in!
I did google it but it seemed everyone else was talking about the problem without really mentioning a solution.

hopeful

---

### Post by deadgobby on 2007-05-10
[https://wiki.ubuntu.com/MainInclusionReportfoo2zjs?highlight=%28foo2zjs%29](https://wiki.ubuntu.com/MainInclusionReportfoo2zjs?highlight=%28foo2zjs%29)

---

### Post by barkhat on 2007-05-10
> **drs305 said:**
> Solved my problem, and maybe yours. If you have a Laserjet of approximately the same vintage just change the 1000 to whatever number your printer happens to be.

When I typed my "me too" entry, I began to think about how I set up my HP Laserjet 1000 in Edgy. I figured things would have been resolved with Feisty, but apparently not. Here are my notes from my Edgy installation, which I applied again in Feisty. I don't know if all the steps are necessary, but my printer is now working after doing them all.

```

		sudo aptitude install build-essential
		wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
		tar zxf foo2zjs.tar.gz 

```
I then moved the foo2zjs to my home directory and continued.

```
	
cd foo2zjs 
make 
./getweb 1000 
sudo make install 
sudo make install-hotplug 
sudo make cups

```

I then edited the following file:

```

gksudo gedit /etc/hotplug/usb/hplj1000

```

Commenting out the Set $DEV lines so they look like this:

		# Set $DEV to, e.g. /dev/usb/lp0, to force the device you want 
		# Else, leave it null to automatically detect the device 
		# DEV=/dev/usb/lp0 #DEV= ""

Next I created my HP Laserjet printer profile. You can do this via the menu or via the command line:

```
	
sudo gnome-cups-manager

```   

Finally, I selected Local printer, use detected printer, then turned the printer off and back on.

I would like to give credit to the author of a post I mostly found this solution on but don't recall where I found it.

Good luck.

Thank you so much for sharing this!  I had the same problem as Hope with a HP LJ1000.  It worked!  I'm so happy!  Thank you, thank you!

---

### Post by Manthis on 2007-05-11
Thanks a lot Drs305 it worked for me too :)  I'm so glad

---

### Post by Hope on 2007-05-12
I'd like to say it worked for me but I get this error;
> sirbarry@main:~/foomatic/foo2zjs$ sudo ./getweb 1000

--13:37:36--  [ftp://ftp.hp.com/pub/softlib/software1/lj1488/lj-1145-2/lj1488en.exe](ftp://ftp.hp.com/pub/softlib/software1/lj1488/lj-1145-2/lj1488en.exe)

           => `lj1488en.exe'

Resolving ftp.hp.com... 161.114.22.105, 15.200.30.22

Connecting to ftp.hp.com|161.114.22.105|:21... connected.

Logging in as anonymous ... Logged in!

==> SYST ... done.    ==> PWD ... done.

==> TYPE I ... done.  ==> CWD /pub/softlib/software1/lj1488/lj-1145-2 ... done.

==> PASV ... done.    ==> RETR lj1488en.exe ... done.

Length: 12,621,056 (12M) (unauthoritative)



100%[====================================>] 12,621,056    41.90K/s    ETA 00:00



13:41:53 (49.18 KB/s) - `lj1488en.exe' saved [12621056]



Archive:  lj1488en.exe

  End-of-central-directory signature not found.  Either this file is not

  a zipfile, or it constitutes one disk of a multi-part archive.  In the

  latter case the central directory and zipfile comment will be found on

  the last disk(s) of this archive.

unzip:  cannot find zipfile directory in one of lj1488en.exe or

        lj1488en.exe.zip, and cannot find lj1488en.exe.ZIP, period.

I've tried all the other steps and I just end up with the same error when I try to print, ie "printing error" no other details.:confused: 
Thanks for your help, this is getting really frustrating

---

