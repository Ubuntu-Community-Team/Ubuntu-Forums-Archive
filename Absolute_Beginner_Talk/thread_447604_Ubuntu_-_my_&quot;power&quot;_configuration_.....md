---
title: "Ubuntu - my &quot;power&quot; configuration ...."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-18
I successfully migrated to Ubuntu from Windows XP and below is my configuration.  I post this not to boast but to stimulate ideas and discussion on what various  "Power Configurations" of Ubuntu can be like.

So, how have you configured Ubuntu?  What software have you installed that you found particularly useful?

Carl




**[SIZE="4"][CENTER]My Configuration[/CENTER][/SIZE]**

Clone PC:  2.8Ghz P4, 2GB Ram, 160GB HD.  nVidia 6250 dual head video card.  Two Septer 20” wide aspect monitors.  Maxtor USB Hard drive for backup.

**_Brief Summary of usage:_**
Ubuntu Feisty Fawn is now my primary OS with WinXP there in case I need something off it.
I use FireFox for Browsing, Open Office for desktop publishing, Gimp for graphics, Banshee for Music playback, MonoDevelop for C# programming.  I use NXServer to remote desktop.  I now run Quicken and QuickBooks on Linux thanks to Cross Over  technology.  I use Evolution for Email.  Ubuntu works reliably, boots fast, shuts down fast, works fast – quite an improvement over Windows XP.
[B][U]
Linux:[/U][/B]
1.Ubuntu 7.04 Feisty Fawn with Open Office 2.2
2.updated the kernel			- updated and compiled my first Linux Kernel
3.Automatix				- install help

**_Video:_**
4.Beryl					- must have desktop eye candy
5.nvidia proprietary video drivers	
6.GIMP Image Editor			- better than Adobe Photshop
[B][U]
Music, Sound, CD/DVD:[/U][/B]
7.Amarok
8.Banshee Music Player
9.Brasero CDROM burning utility
10.GnomeBaker – CD/DVD Writer
11.Serpentine Audio CD Creator
12.Rythmbox Music Player
13.Movie Player
14.Mplayer
15.Sound Juicer CD Extractor
16.Streamtuner
17.XMMS

**_Miscellaneous:_**
18.GnomeSword2 Bible			- not quite as good as ESWORD
19.Spider Solitare			- game
20.Google Earth				- fantastic
21.GAIM Internet Messenger
22.GnuCash
23.Various Codex's and Plugins
[B][U]
Programming:[/U][/B]
24.Mono					- run .NET applications
25.Monodevelop				- C# IDE
26.gcc++					- command line C-compiler
[B][U]
System Tools:[/U][/B]
27.NTFS-3G				- R/W NTFS – i.e. access Windows XP disc
28.ssh					- secure shell in lieu of Telnet
29.NXServer				- Remote terminal session

**_Windows Legacy:_**
30.Wine					- Spider Solitaire game
31.CrossOver				- to run Quicken2005, Quick Books 2004, IE6

**_Printers:_**
32.install HP2420 printer
33.install Brother MFC-420CN
34.PDF Printer driver

**_Tweaks:_**
35.Static IP
36.dual montior configuration
37.sudo apt-get install alien		- convert RPM to DEB
38.sudo apt-get install gnochm		 -read *.CHM help files
39.sudo apt-get install msttcorefonts  	 - Fonts

---

### Post by david_kt on 2007-05-18
> **cwmoser said:**
> 
**_Miscellaneous:_**
18.GnomeSword2 Bible			- not quite as good as ESWORD

You could install Esword using [these]("http://ubuntuforums.org/showthread.php?t=403677&highlight=esword") how to.

DK

---

### Post by dondad on 2007-05-19
*bump*

---

### Post by rdmike on 2007-05-21
Hi,

How did you get the brother MFC 420 printer to work? Were you able to use it as a networked printer as well? Thanks for the help as I am just trying Linux for the first time and haven't figured out the details just yet. :-)

rdmike

---

### Post by cwmoser on 2007-05-22
I documented notes on various packages I installed.  Installing the MFC-420CN was challenging and took me some time to figure out.  I think one of the 'secrets' is taht you need to install C-Shell (csh).

Here are my notes for the Brother MFC-420CN.

Carl



Brother MFC-420CN


Download Printer Drivers from [www.Brother.com](www.Brother.com)

mfc420cnlpr-1.0.2-1.i386.deb
cupswrappermfc420cn_1.0.0-1_i386.deb


Install csh - this is required:
sudo aptitude install csh



Install LPR Driver:

TURN PRINTER OFF

sudo mkdir /var/spool/lpd
sudo mkdir  /var/spool/lpd/MFC420CN
sudo dpkg  -i  ./mfc420cnlpr-1.0.2-1.i386.deb


Install the CPUS Wrapper:
sudo  ln  -s  /etc/init.d/cupsys /etc/init.d/cups
sudo dpkg  -i  ./cupswrappermfc420cn_1.0.0-1_i386.deb

cp  /usr/share/cups/model/brmfc420cn_cups.ppd   /usr/share/ppd/
ln  -s  /u/share/cups/model/brmfc420cn_cups.ppd  /usr/share/ppd/brmfc210c_cups.ppd
chmod  g+w  /tmp
chmod  o+w  /tmp


TURN PRINTER ON

Final setup and Print Test Page:

System -> Administration -> Printing

Right-click the MFC210C and click "Properties"

    * Connection Tab: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C)
    * General Tab: Here I rename 'MFC210C' to 'Brother Printer'. Let's the whole family know the printer they're selecting.
    * Paper Tab: Ensure your local paper size is selected.
    * Advanced Tab: Review the choices and make appropriate adjustments.
    * From any tab: Click "Print a test page" to confirm all works well.






Other Notes:

1.
Install the LPD/LPRng printer driver and CUPS Wrapper printer driver from the following pages:

Note: 
It is important to install the LPD/LPRng driver before installing the CUPS Wrapper driver. 
(LPD/LPRng printer driver)
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
(CUPS Wrapper printer driver)
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

If you receive the error message "lpadmin : Unable to copy PPD file" , please ignore it.
Connect the printer to your Linux PC and turn the printer power on.
2.
Next, you have to check the DeviceURL.
If you are connecting the machine via USB, run the command:
" lpinfo -v".
All device URL's which are registered will be listed.

If you are connecting the machine via the network or parallel port, enter the 
temporary DeviceURL "usb:/dev/usb/lp0" in the lpadmin command below. 
3.
Next, check the PPD file name.
Run the command:
"ls /usr/share/cups/model" and check the PPD file name.

4.
Then you should run the following command:
lpadmin -p (printer name) -E -v (DeviceURL) -P /usr/share/cups/model/(PPD file name)
For example, the command should read like this:
lpadmin -p HL2070N -E -v usb:/dev/usb/lp0 -P /usr/share/cups/model/brhl2070n.ppd
Note: 
For "(DeviceURL)", please replace it with the DeviceURL you checked in Step2.
For "(PPD file name)", please replace it with the PPD file name you checked in the Step3.

5.
If you are connecting the machine via the network, open the CUPS Web Interface "http://localhost:631/printers" , and change the DeviceURL to "lpd://xx.xx.xx.xx/binary_p1" or" lpd://nodename/binary_p1 ".

---

### Post by lazyart on 2007-05-22
Wow.  I have a Brother 7820N (networked laser all in one).  I went to Printers, clicked on new and selected network.  It read the printer database (20 seconds?) then sprung up having recognized the printer's ip address with no interaction.  I confirmed it and it suggested the driver matching the printer.... so um, I clicked okay and it was done.  I did all of those above steps for Dapper but on my fresh install of Feisty it pretty much did itself.  Three click install?  Never in windows.

---

### Post by rdmike on 2007-05-22
Three step install? Gotta love it! Unfortunately my printer install looks to be a long process and much more arduous than I anticipated when switching to linux. Ah well, it will be a learning experience right? Now, I am wondering if the 64bit version of Fiesty that I downloaded will create more issues than might normally be the case in terms of installing this printer? The reason I ask is the more information I read the more I hear this mentioned. Thanks again for the quick reply!

---

### Post by cwmoser on 2007-05-23
A lot of it has to do with which model printer.  My HP 2420 installed without a hitch.  The Brother MFC-480 was a bear.

Carl

---

