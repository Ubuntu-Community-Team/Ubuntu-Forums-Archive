---
title: "Enabling Dell Photo Printer 720 on Ubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2008-01-26
Could someone please advise how I can enable my basic USB printer (Dell Photo Printer 720) on Ubuntu. Any help would be most appreciated.

---

### Post by jeffus_il on 2008-01-26
The driver may not be available on your system.
Download it from:
[INDENT][http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151)
[/INDENT]Follow the Unix Driver Guide below on the page to install the driver on your system.
Then:

[LIST]
[*]Open your internet browser
[*] Type the address "localhost:631"
[*] Choose the Administration tab
[*] Choose the "Find New Printer" button
[*] Choose your printer
[*] Follow the install instructions and use the [FONT=ms sans serif, helvetica]**Lexmark z600 driver**[/FONT][/LIST]

---

### Post by bwtranch on 2008-01-26
Well, I really don't know that much about your particular model, but I can talk about the basic steps involoved in getting a printer to work in Linux. If your OEM supports a driver, then you really have no problem (maybe). The first thing to do is to go to their web site and find out if something is available, if not, don't give up. Everything I tried on the internet didn't show any promise for my printer (Brother DCP-1000) and I wound up writing the how-to on getting this printer to work. I can tell you it wasn't easy, but, hopefully it won't be that bad for you.

You will probably have to use the cupswrapper system and thanks to Apple, we have that.

Your printer may have a cups driver installed already and all you need to do is enable it. Try going to [http://localhost:631](http://localhost:631) and see if your printer is listed.

You may have to install a driver first and then go there. I know this sounds complicated and it is. But, with a little googling and with what I have given you, maybe it will work out. 

I'm sure someone else will chime in with maybe some more. The thing is about the Brother, no one had ever figured this one out before. Said it couldn't be done!:) Ha

---

### Post by MeanStreak on 2008-01-26
> **jeffus_il said:**
> The driver may not be available on your system.
Download it from:
[INDENT][http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:390:0:0&emeaframe=&fileID=1151)
[/INDENT]Follow the Unix Driver Guide below on the page to install the driver on your system.
Then:

[LIST]
[*]Open your internet browser
[*] Type the address "localhost:631"
[*] Choose the Administration tab
[*] Choose the "Find New Printer" button
[*] Choose your printer
[*] Follow the install instructions and use the [FONT=ms sans serif, helvetica]**Lexmark z600 driver**[/FONT][/LIST]

Thanks very much for the reply. 

I downloaded the CJLZ600LE-CUPS-1.0-1.TAR.gz to /tmp then followed the install instructions for Red Hat in the Unix Driver Guide PDF:

Installing from the Internet
[LIST=1]
[*] Read Before installing.
[*] Download the Lexmark Print Drivers package from the Lexmark Web site at  [http://www.lexmark.com/drivers:](http://www.lexmark.com/drivers:) lexmark-print-drivers-linux-glibc2-x86.rpm.gz
[*] Save the downloaded package in the /tmp directory.
[*] Uncompress the package file # gunzip /tmp/lexmark-print-drivers-linux-glibc2-x86.rpm.gz
[*] Install the package file: # rpm -ivh /tmp/lexmark-print-drivers-linux-glibc2-x86.rpm
[*] Run the following setup script to complete the installation: # /usr/local/lexmark/setup.lexprint
[/LIST]

Then:

[LIST=1]
[*] I opened the the address "localhost:631"
[*] I selected the administration tab
[*] I selected 'Find New Printer'
[*] I selected my Dell Photo Printer 720
[*] On the Model/Driver for Dell_Photo_Printer_720 screen, I have the option of either selecting drivers for two printers not relevant, or selecting "Provide a PPD file", however I don't have a PPD file. 
[/LIST]
Please advise. Talk about non-trivial.

---

### Post by rlhanson on 2008-03-24
> **MeanStreak said:**
> Thanks very much for the reply. 

I downloaded the CJLZ600LE-CUPS-1.0-1.TAR.gz to /tmp then followed the install instructions for Red Hat in the Unix Driver Guide PDF:

Installing from the Internet
[LIST=1]
[*] Read Before installing.
[*] Download the Lexmark Print Drivers package from the Lexmark Web site at  [http://www.lexmark.com/drivers:](http://www.lexmark.com/drivers:) lexmark-print-drivers-linux-glibc2-x86.rpm.gz
[*] Save the downloaded package in the /tmp directory.
[*] Uncompress the package file # gunzip /tmp/lexmark-print-drivers-linux-glibc2-x86.rpm.gz
[*] Install the package file: # rpm -ivh /tmp/lexmark-print-drivers-linux-glibc2-x86.rpm
[*] Run the following setup script to complete the installation: # /usr/local/lexmark/setup.lexprint
[/LIST]

Then:

[LIST=1]
[*] I opened the the address "localhost:631"
[*] I selected the administration tab
[*] I selected 'Find New Printer'
[*] I selected my Dell Photo Printer 720
[*] On the Model/Driver for Dell_Photo_Printer_720 screen, I have the option of either selecting drivers for two printers not relevant, or selecting "Provide a PPD file", however I don't have a PPD file. 
[/LIST]
Please advise. Talk about non-trivial.
Has anyone been able to make this driver work with "Gutsy"? I have followed the instructions to the letter. If I try to print a test page, it is submitted as pagexx but the data is never sent to the printer. The printer is always in an idle state.
Can any one help me?

---

### Post by rlhanson on 2008-03-24
I may be wrong but it appears to me that these instructions are for a .rpm install.

My problem is that my Laptop will not send the 'print test page' to the printer. When I go to 'localhost:631' <Administration <find printers it tells me that 'No printers were found'. If I go to <Administration <printers. The printer shows up as the (Default Printer) with the following data.
     Description: Dell Photo Printer 720
     Location: ubuntu
     Printer Driver: LexmarkZ600 v1.0-1
     Printer State: idle, accepting jobs, not published
     Device: cups-pdf:/
When I try to 'print test page' nothing happens. Anyone have any ideas as to why this is happening or not happening.

---

