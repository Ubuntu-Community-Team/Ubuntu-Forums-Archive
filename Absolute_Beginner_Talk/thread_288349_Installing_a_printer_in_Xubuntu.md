---
title: "Installing a printer in Xubuntu"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by HenningS on 2006-10-29
I have Xubuntu running on an i386 PC and I have an Epson EPL-5900 connected to it. Now my question is, how do I get the thing to print? I don't have any Linux drivers for it, and I don't get what the Printer setup and Printer dialog thing is for. Can anyone help me?

---

### Post by ReaderRat on 2006-10-29
You might go to the link below - Hardware Compatilibility List - and check out your printer.

---

### Post by HenningS on 2006-10-29
> **ReaderRat said:**
> You might go to the link below - Hardware Compatilibility List - and check out your printer. Okay, I   looked for the printer, but I wasn't able to find out anything that I understood :???:  How do I *install* any printer?

---

### Post by ReaderRat on 2006-10-29
Sorry, I got a cuppa coffee....
Take a look at this link:
**[http://lists.freestandards.org/pipermail/printing-user-epson/1999/001732.html](http://lists.freestandards.org/pipermail/printing-user-epson/1999/001732.html)**


[color=BLUE] Nevermind, it's a dud...[/color]

---

### Post by ReaderRat on 2006-10-29
I found the right one:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5900](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5900)

Sorry, I don't have any personal knowledge of this printer...

---

### Post by HenningS on 2006-10-30
> **ReaderRat said:**
> I found the right one:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5900](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-5900)

Sorry, I don't have any personal knowledge of this printer...
Thanks. Downloaded epsonepl for the EPL 5900L printer, got an .RPM file. How do I use these?

---

### Post by pistcivet on 2006-10-30
Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups
Select the group shadow and click Properties.
Add the user cupsys to the group.
Restart CUPS with this command:
$sudo /etc/init.d/cupsys restart
Open a browser and type this in the address bar:
[http://localhost:631](http://localhost:631)

You should then be able to configure the printer.
You (most likely) will not need to download any driver.

---

### Post by HenningS on 2006-10-30
> **pistcivet said:**
> Launch Applications->System->Users and Groups, click on the tab Groups, and check Show all users and groups
Select the group shadow and click Properties.
Add the user cupsys to the group.
Restart CUPS with this command:
$sudo /etc/init.d/cupsys restart
Open a browser and type this in the address bar:
[http://localhost:631](http://localhost:631)

You should then be able to configure the printer.
You (most likely) will not need to download any driver.
Okay, I did all that, and I think I got *some* results. The 'error while printing' doesn't show up, instead a dialogue window that closes down so fast that I can't read what it says. The printer still doesn't print.
When I try to print a test page from the config, it says: 
"/usr/lib/cups/filter/foomatic-rip failed"
When I looked for that file, it wasn't there. Nor was any foomatic crap. Damn I'm getting frustrated.

---

### Post by ReaderRat on 2006-10-30
I believe you will have to use a program called alien. Here's how:
**[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)**

---

### Post by HenningS on 2006-10-31
> **ReaderRat said:**
> I believe you will have to use a program called alien. Here's how:
**[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)**
I did that. Installed the package and everything. Didn't change anything. I'll try it again and more thoroughly tomorrow, but right now, I'm just too tired.

---

### Post by Aurora on 2006-11-06
Hello,

I hope you see this, the thread is getting stale.  This is Xubuntu's best-kept secret.

The Xubuntu CD comes with a utility called gnome-cups-manager which makes it easy to install printers.  For some unfathomable reason, it does not install by default. Install this by your preferred method, either with Synaptic or the command line, and chances are when you click "add a printer", your printer will be automatically detected, and the driver will already be included.

--Paul in Seattle

[https://wiki.ubuntu.com/XubuntuPrinterConfigSpec?highlight=%28xubuntu%29%7C%28config%29%7C%28printer%29](https://wiki.ubuntu.com/XubuntuPrinterConfigSpec?highlight=%28xubuntu%29%7C%28config%29%7C%28printer%29)

---

### Post by HenningS on 2006-11-08
> **Aurora said:**
> Hello,

I hope you see this, the thread is getting stale.  This is Xubuntu's best-kept secret.

The Xubuntu CD comes with a utility called gnome-cups-manager which makes it easy to install printers.  For some unfathomable reason, it does not install by default. Install this by your preferred method, either with Synaptic or the command line, and chances are when you click "add a printer", your printer will be automatically detected, and the driver will already be included.

--Paul in Seattle

[https://wiki.ubuntu.com/XubuntuPrinterConfigSpec?highlight=%28xubuntu%29%7C%28config%29%7C%28printer%29](https://wiki.ubuntu.com/XubuntuPrinterConfigSpec?highlight=%28xubuntu%29%7C%28config%29%7C%28printer%29)
Thank you for helping, but I'm afraid my issue is solved. I snapped. The comp now runs Windows XP. I've just had too many problems with Xubuntu. I might try it again some time, but right now my mother desperately needs a computer that keeps the keyboard layout fixed, prints properly, doesn't hide the menubars at will, and provides a good office suite.
But thanks anyway for replying, I really do appreciate it. :???:

---

### Post by dbbolton on 2006-12-11
perhaps you can help me

i'm trying to install a Xerox Workcentre XK50CX on xubuntu 6.06 (i also installed the ubuntu-desktop package, gnome-cups-manager, and so on)

the computer detects the printer and gcm recommends the lex5700 driver (the xk50cx isn't on the list; it selects this driver for a xk35c)

however, linuxprinting.org states:

> **Section 3: Xerox WorkCenter XK50cx**

        
3.1 _How do I set it up?_ Setting it up as a Lexmark GDI inkprinter with Ghostscript "stp" driver. gs -DIVICE=stp -sMODEL=lexmark-z52 
       3.2 _How well are the options supported?_ All resolutions and quality parameter are available. It is important to use the Lexmark Z52 model. Other models aren't compatible to higher resolutions ober 600x600i added a new printer as a lexmark z52 with the gutenprint driver, and under "connection" i chose "use another printer by specifying port", which is usb #1.

neither of these worked. with the lex5700 driver, the printer makes noises like it's printing but ultimately shoots out a blank page. with the gutenprint driver, it just spits out a blank page.

what exactly is "gs -DIVICE=stp -sMODEL=lexmark-z52"? when i run it in a terminal as sudo or not, i get this error:

-dvar=name requires name=null, true, or false


so, i tried "gs -DIVICE=stp -sMODEL=lexmark-z52 -dvar=null" but got the same error. same with true or false.

this is my friend's computer, so it really doesn't matter to me. but i would certainly like to help him and we would both appreciate your help.

---

### Post by HenningS on 2007-05-11
> **Aurora said:**
> Hello,

I hope you see this, the thread is getting stale.  This is Xubuntu's best-kept secret.

The Xubuntu CD comes with a utility called gnome-cups-manager which makes it easy to install printers.  For some unfathomable reason, it does not install by default. Install this by your preferred method, either with Synaptic or the command line, and chances are when you click "add a printer", your printer will be automatically detected, and the driver will already be included.

--Paul in Seattle

[https://wiki.ubuntu.com/XubuntuPrinterConfigSpec?highlight=%28xubuntu%29%7C%28config%29%7C%28printer%29](https://wiki.ubuntu.com/XubuntuPrinterConfigSpec?highlight=%28xubuntu%29%7C%28config%29%7C%28printer%29)
I'm back again. The PC has Xubuntu again, same printer, USB connection. And once again, I'm desperate. I installed this gnome-cups-manager thingy, but how do I start it?
Any help is well appreciated, I'm in deep trouble here:(

---

### Post by the.phantom on 2007-05-21
i THINK you can use places and navigate to 
user
bin
gnome-cups-manager


and it is a executable so you can just click it and it will start 

hope this helps ?

(i just tried it and it worked for me to start it)

---

### Post by HenningS on 2007-05-22
Thanks man, that's exactly the folder I've been looking for. I converted from Mac OS X (temporarily), and I kinda missed knowing where all my apps are.
Also, the printer is installed now, and except for PDFs from certain apps (Adobe reader works fine, though), everything prints just fine.

---

