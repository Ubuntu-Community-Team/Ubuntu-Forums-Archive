---
title: "Xerox 8400 Printer Install?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by jmwendt on 2007-06-30
I installed Feistyu Fawn with minimal trouble (maybe too easy -- didn't learn much!)  Current problem is installing my Xerox 8400 network printer. Driver is not in the Install Printer list, however there is a driver package on the Xerox Web site. This expands to give several tar files and an executable named setup. Double-clicking from Gnome doesn't do anything. From bash, in the appropriate directory, the command sudo setup give the message

./setup: 1: Syntax error: word unexpected (expecting ")")

The readme doesn't say anything about ")". Can anybody help?

Thanks,

John

---

### Post by Akuma Shiro on 2007-06-30
I had trouble getting my printer to work. 
Try going to System/preferences/Removable drives and Media-clicking on the "printers and scanners" tab, and checking the box that says "Automatically run a program when printer is connected".
Do this with the printer connected, but TURNED OFF.

turn your printer on, and hopefully, the CUPS printer set up will come on and show your printer is detected. Once you get your printer set up, uncheck the box you checked as above.

I think this only works if your printer is supported by CUPS. And it seems that almost every printer is supported.

I wish you luck. Let me know if it worked.

---

### Post by jmwendt on 2007-06-30
Thanks, Akuma. Neglected to mention that my printer is already detected, with the correct network address and information. Next panel is driver selection: Xerox is mentioned, but not the 8400. Tried a few drivers for other Xerox printers, but none of them would change the paper size from the default A4, even though I selected US Letter from the dialog. Printer wants the correct size, or no joy.

---

### Post by Akuma Shiro on 2007-06-30
Sorry I can't be any more help. Perhaps you could try contacting Xerox directly. With Epson, I know that some of the drivers are able to make other printers work. Maybe they could tell you if a different model printer driver would work just the same.

---

### Post by halitech on 2007-12-20
Hi John

Have you been able to get your printer working yet? If not, you may need to download the PPD files from the xerox website. Try calling support if you need more help, I'm sure there is a few people there that can help you out even if they don't officially support linux.

---

### Post by bryang317 on 2008-01-31
jmwendt...Did you ever resolve this?

I have the same issue, and I think it's just my noobness.

In case anyone can help.  Here's the readme from xerox.
[INDENT]
To install the package expand the tar file and execute setup.
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
              all of the Xerox software.[/INDENT]

Running sudo ./setup from the directory I unpacked the tar to produces the following error:  *'./setup: 1: Syntax error: "(" unexpected*

TIA.

---

### Post by halitech on 2008-02-13
Hi

Try just simply extracting the files then go into Printing (System - Admin - Printing) and add a printer. Go with a networked printer and select TCP/Socket, HP Jet Direct and put in the IP address and leave it on port 9100. Then select install driver on the next screen and browse to where you have the files extracted to and that should do it.

---

### Post by prescottp on 2008-06-30
The difference is that, while CUPS works jjust fine, using a Xerox printer with its full feature set requires you to install the CentreWare software... I could also use some help on this if anyone knows how to "execute" setup.  I've tried every command I can think of at this point.

---

### Post by halitech on 2008-07-01
CWIS is not software you can install, its a web service that runs on the machine itself. open a browser and type the IP address in the address bar and you'll see Centerware.

---

