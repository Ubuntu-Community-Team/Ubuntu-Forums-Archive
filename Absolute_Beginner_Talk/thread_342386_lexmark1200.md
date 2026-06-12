---
title: "lexmark1200"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by dave_2 on 2007-01-20
Im completely new to ubuntu but have manged to install it and set it up on the windows network at home . The main problem I am having is with a lexmark 1200 series printer . When I ask to install a new printer the system finds it on the correct port and suggest a driver . However when I print a test page the job is sent to the printer but then the the job is stopped with no printing . The printer is set up as a local printer and works fine under windows with the driver supplied . The other point is that although the printer driver is for a 1200 series and the system recognises it as a 1200 the actual machine is a 1271 scanner and printer . The scanner is not recognised by xsane . I have tried all the other lexmark drivers with no success . I currently have to export as pdf onto a network drive and print from the windows computer using remote desktop . I would appreciate any help that I can understand

---

### Post by Sef on 2007-01-20
Do you have a n optra 1200 or another 1200 model?

---

### Post by dave_2 on 2007-01-20
windows describes it as a lexmark 1200 series .and the same description is used in the manual . The actual machiine is described as a "1200 all in one" . Could the fact that the scanner is not recognised by xsane be realated?. I tried all the lemark printer drivers  some said printing and nothing happened and some said job stopped . I have installed it as a network printer and again it is recognised on the host windows conputer . When a tets page is requested the prineter jobs go from job printing then goes to job pending . Any asvice appreciated

---

### Post by evil_cat on 2007-10-23
I also have the same kind of printer lexmark 1200 all in one series and it is not optra model

PLEASE HELP:confused:

---

### Post by BruisedQuasar07 on 2007-10-23
The problems you describe are not limited to lexmark all-in-one
printers. I am new not to computing, problem
analysis, or research but to Linux (started July).

I have read several posts about problems like yours and a
problem with Epson & HP printers wto Linux (started July) but 
working well until the user reboots
Ubuntu, SuSe & other popular distros. You will have to solve this
problem yourselves. I will help you with documents (that for Linux are
scattered all over Internet and most prove useless, as they contain 
unrelated stolen from huge books like Linux Bible). The ones I offer you
here are written by real Linux experts.

You would not believe the goofy advice wannabe Linux Experts gave 
here for my problems. Most very arrogantly said its a hardware problem, 
which is almost never the case. The problem lies in Cups. I also found
a problem I had with my HP supported HP psc 1315 all-in-one is caused
by a incorrect line in CUPS that's been there for two years! Remove 
the line and the scanner problems vanish. 

Meanwhile learn the main parts of any Linux Distro and the specific 
parts for Unbuntu, i.e., Gnome desktop, Cups, Terminal, Bash, Grub
You can look them up one at a time via Google search. Scan the docs
fast for fluff of someone who doesn't know what he is talking about
or takes 10 pages to explain a one page topic. Wiki is a great place
to begin. 

[https://help.ubuntu.com/community/CategoryDocumentation](https://help.ubuntu.com/community/CategoryDocumentation)
Offcial Ubuntu Docs >look for "print" & CUPS docs 

[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)
For earlier version of Ubuntu but applies to 7.04, etc

You need to learn about Printers and Printing in Gnome desktop 
Linux distros in general. Search Google for CUPS (Common Unix 
Printing System) which is where your problem resides. Just search Google
for CUPS and select the WIKI article about CUPS, it was contributed
by an Ubuntu or some other Linux expert.

Also search Google for - Gnome-Cups-Manager

Read this material and I think you will figure your way around
your print problem

--Bruised

---

### Post by Feenix3k on 2007-12-03
So far I have only been able to get my lexmark 1200 to work in 6.06 Ubuntu. It uses the z600 driver.  So far I have been unable to get it to work in 6.10 or 7.4 and have not tried out 7.10 yet.


This is the direction that I have for 6.06. It will in stall in 6.10 and 7.4, but it does not show up in the drivers list when you install  the printer.

First Section
Make sure you have installed the following packages 

apt-get install libstdc++5 alien

You have to download the Lexmark driver from [http://gentoo-wiki.com/HOWTO_Lexmark_Printers](http://gentoo-wiki.com/HOWTO_Lexmark_Printers) 

mkdir lexmark

cd lexmark

wget [http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz](http://www.downloaddelivery.com/srfilecache/CJLZ600LE-CUPS-1.0-1.TAR.gz)

Then you have to extract the content 

tar xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz

You now have a lot of files in your current directory, the driver is buried inside a shell-script, and you have to dig it out: 

tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz
Unpack your new tar-archive: 

tar xvzf install.tar.gz

Unfortunately Lexmark has only given you .rpm-packages, and you have to extract the content of those: 

alien -t z600cups-1.0-1.i386.rpm
alien -t z600llpddk-2.0-1.i386.rpm

Now you have to extract the newly made tgz-files which contains the drivers, and copy them to their locations. !!! Important: do exactly as written, otherwise your system may become ruined !!! 

tar xvzf z600llpddk-2.0.tgz
tar xvzf z600cups-1.0.tgz
cd usr

sudo cp -a * /usr
sudo ldconfig # Reloading library-database

The drivers are now installed and copied to their locations. Test everything out with the following command: 

/usr/lib/cups/backend/z600

If the output is something similar to this: 

direct z600:/dev/usblp0 "Lexmark  Lexmark X1100 Series" "Lexmark Printer"

Then it is working. 
Reload Cups: 

/etc/init.d/cupssys restart

And add a new printer using System->Administration->Printing. Make sure you select the z600-driver.

---

