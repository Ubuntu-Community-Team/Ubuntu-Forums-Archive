---
title: "Installing Printer Driver Help"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Michl on 2007-03-29
For some reason Feisty at work has trouble printing
on Xerox 4512 on the LPT1 port.  The test page takes
over 3 hours to print.  So I am thinking of trying to see
if Xerox's CentreWare drivers will help.  What I need to
know is where do I expand and install the packages
in Feisty.  Xerox gives the following directions:

> To install the package expand the tar file and execute setup.
NOTE: setup for the code package will expand and install the compressed tar
   file in the install directory; generate script files and other files
   that are needed at run time. You do not need to uninstall the package
   if you are upgrading or reinstalling.
The following syntaxes are supported:
1. setup
2. setup tmp_path
3. setup install install_path
4. setup install install_path tmp_path
install_path is the installation directory which will contain
              all of the Xerox software.
tmp_path      is a temporary work area. /tmp is the default work area.

What should "install-path" be?

Thank you!  (If you think that this is a waste of time because these drivers will
not solve my problem, I want to know.)

Thanks!
Michl

---

### Post by Cathead Fred on 2007-03-29
Hi Michl,

Sorry to hear about your problem. I checked the linuxprinting.org website and it says your printer should work.

The website mentions two printers:

(1). The Xerox DocuPrint N4512

[http://www.linuxprinting.org/show_printer.cgi?recnum=Xerox-DocuPrint_N4512](http://www.linuxprinting.org/show_printer.cgi?recnum=Xerox-DocuPrint_N4512)

And

(2). The Xerox DocuPrint N4512PS

[http://www.linuxprinting.org/show_printer.cgi?recnum=Xerox-DocuPrint_N4512PS](http://www.linuxprinting.org/show_printer.cgi?recnum=Xerox-DocuPrint_N4512PS)


I don't know which one you need, so I posted both links. Both links do suggest a different driver than the Xerox one you are trying to use. I would give them a go.

Good luck and post your progress

Cathead Fred

---

### Post by Michl on 2007-03-29
The driver I am using is the hpijs driver -- that's what
the ordinary route for Add Printer recommends, but I'm
still having those problems.  I placed this as a bug on
launchpad and it seems that this is an issue.

---

### Post by Michl on 2007-03-30
Any advice?  Where should expand and install these
packages?   In other words, what should "install_path"
be?  (See quote in the first message.)

Thank you!
Michael

---

### Post by prescottp on 2008-06-30
I am also having this problem.  It says to execute setup but I have no idea how to do this.  And I also don't know what directory to use.  We're trying to install a Xerox Phaser 8860MFP and switch the entire office to use Ubuntu Linux.  This is proving to be very challenging...  Anyways, I've tried sudo setup, sudo make setup, sudo install setup, sudo exec setup.  Nothing works... Perhaps it's a very simple command that I'm not using??  I'm great with windows, I've administered servers using SSH, but I've never installed printer drivers on an actual Linux system right in front of me.  Your help is greatly appreciated as I learn this new environment.

---

### Post by halitech on 2008-07-03
download the CUPS Printer package from here

[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8860&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8860&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

and extract.

Then go to System - Administration - Printing and add a printer. For the connection, select AppSocket/HP JetDirect. Leave the port on 9100 and add the IP address of the printer. Then Select Provide PPD file and browse to where you extracted the files and select the model you have. Then select any additional options you have like extra ram, trays and a hard drive. Give it a name and finish. You should then be up and running.

---

