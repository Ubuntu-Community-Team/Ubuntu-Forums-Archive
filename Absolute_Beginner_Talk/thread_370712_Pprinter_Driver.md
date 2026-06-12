---
title: "Pprinter Driver"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by penndragonn on 2007-02-26
Hey guys,

Trying to get my Brother Printer working. Brother    main web page has link for Linux drivers... This is the file I downloaded: mfc210clpr-1.0.2-1.i386.deb
have no idea how to install it.can someone help?

Here's the     web page I went to to find out how, but nothing worked...
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
I'm very new  at Linux and installing new things seems almost alien to me...not like clicking on an EXE:confused:  or INSTALL, or SETUP file in Windows...not even close!!  

p.s. the mfc210c is my Brother Printer

---

### Post by Jussi01 on 2007-02-26
Oops, it seems a little more complicated than i first thought. Ill have a read and see if I can figure it out.

---

### Post by Jussi01 on 2007-02-26
OK, there are some clearer instructions here: [http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install.html)

try following them, one note however, instead of trying to log in with the "su"command like they say, prefix all of the terminal commands with "sudo"

Let us know how you go!!

---

### Post by penndragonn on 2007-02-26
Juss,

I'll give it a shot...thanks..


Just went to that site...What the heck is CUPS.....What do I download...where do I install it, using ARK I guess...then what...this is all quite confusing......Every time I use that unzipping program ARK I get error messages......HELP!!!!!!!!!!!!!!


I need step by step instructions.....that web page lists the type of Linux your running, I thin Kubuntu it Debian based correct?? After I download that, then the cups driver thing right? Then open the Terminal and use Sudo??

---

### Post by Jussi01 on 2007-03-01
Ok, here are some instructions:
Download this:

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)

and this:

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

copy  them both into one directory in your home folder - for the purpose of this exercise we will call it temp

then open terminal, type 
```

cd temp
```

Press enter after each line of code I give you

then type 
```

sudo dpkg -i --force-all mfc210clpr-1.0.0-1.i386.deb
```

it will ask for your password, enter your password (you wont see any letters on the screen) and press enter
```

sudo dpkg -i --force-all cupswrappermfc210c_1.0.0-1_i386.deb
```

then

go to firefox and put in this address

[http://localhost:631](http://localhost:631)

Click on “Manage Printers” and confirm that the printer name is listed there.
If the printer name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

The default port is USB. If you want to use a different port, click on “Modify Printer” and select the required printer port

Hope this helps

---

### Post by penndragonn on 2007-03-01
had to redo my whole pc........somehow the boot.ini file became invalid...AGAIN!!  Not sure what I'm doing wrong.....tried doing a fixmbr, and that failed.......  Windows is finally back on, and soon Linux on 2nd drive...I'll try what you suggested Juss....just wish you could just click on an Install File as in (Windows) Cough!!   Cough!!  Why does Linux have to be so complicated for new people...I'd imagine it scares many away...Definately not for the faint of heart as I've found out NUMEROUS times. I've Tried Fedora, Ubuntu, Kubuntu, X-Evian, DreamLinux, and PCLinuxOS...next on the list is Fedora Core 6....if that doesnt work, it's back to Kubuntu..........thanks again for all the help guys.

:)

---

### Post by Jussi01 on 2007-03-02
Hei, I understand your pain. However, you need to remember that it is that easy for many things, but many drivers for printers and other stuff are written by people who have those items, not by the manufacturer - manufacturers usually cater to windows and mac only. So that is one reason it can be hard.

---

