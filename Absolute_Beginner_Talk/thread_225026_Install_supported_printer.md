---
title: "Install supported printer?"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by goatflyer on 2006-07-28
I've never installed a printer before and after reading and re-reading docs and helpfiles I must be missing some basic concept.

According to linuxprinting.org, my printer Epson Stylus C68 is supported by gutenprint/gimp-print, and that the driver can be accessed there.

Checking with Synaptic, I see gimp-print is installed.

When I load gimp, and try to print, I can see my printer in the addprinter, but it asks for a .PPD file which I don't have, and which linuxprinting.org says that gimp-print already has the driver.  Clicking 'print' complains no destination.

Same story with CUPS.  I get into the web-interface, it detects that I have an epson printer, but it asks me to either choose some generic driver for it (a list of about 8-10 which one do I choose?) or else supply the .PPD file, which I don't have and can't find.

I posted this question in the newbie section because I'm feeling pretty clueless and I need very basic explicit instructions.

--edit--
its Xubuntu, does it matter?

---

### Post by OU812 on 2006-07-28
Try setting up the printer this way: Launch a web browser and enter this address:

[http://localhost:631/admin](http://localhost:631/admin)

This will take you through the steps of setting up your printer.

john

---

### Post by goatflyer on 2006-07-28
Yes, this is the CUPS web-interface I mentioned in my question.

When I click on Add printer / EPSON  It suggests a list of 34 generic drivers (I counted!) of different sorts (which one to pick? 10 are 'recommended'), or else I should point it to the location of a .PPD file, which I don't know where it is, but which is supposedly included in the gimp-print.

---

### Post by OU812 on 2006-07-29
I found this link. Sorry if you did too.

[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C68](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C68)

john

---

### Post by goatflyer on 2006-07-29
Yes, I'm sorry too.  This is the page that confuses me most.  It tells me that gutenprint already has all the .PPD files inside it, so thats why they don't let me download one.

It also devotes a good amount of screenspace to tell me 3 ways how I can "access" the driver, but it reads more like an advertisement telling me in vague ways what is POSSIBLE, instead of being instructions on what I should do or select.

All I want to set up my printer, that's what I want to know how to do.  And this is a page that is devoted to exactly my printer and nothing else, but it still doesn't say what I am supposed to do.

---

### Post by goatflyer on 2006-07-29
bump.

Still have no idea how to supply the .PPD file for my printer that is supposedly included in gimp-print (so why does it ask me for it?).

Has anyone successfully installed a supported printer on Xubuntu?

Please.

---

### Post by goatflyer on 2006-07-29
FOLLOW-UP POSTING:

Eventually I have succeeded in getting the printer to work.

I gave up trying to figure out the CUPs admin printer setup (with its 10 'recommended' drivers).

Instead I did what Xubuntu recommends not doing:  I went into Synaptic and installed gnome-cups-manager.  After it installed, I wasn't able to find it in any of the Application menus, so I opened a terminal, and typed:

gnome-cups-manager


I got a pretty GUI window with an New Printer icon.  Double-clicking that eventually leads to
      Step 1 of 3:Printer Connection.
On that screen I had to select
      printer port: Parallel #1 (EPSON)

Clicking 'Forward' brought me to Step 2 of 3, where it gave me a list of ALL the epson printers.  I chose Stylus C86 and (THIS IS WHERE GNOME-CUPS-MANAGER SHINES!!!!!) the suggested driver automagically switched to "High-quality Gutenprint" driver, which is the one driver that is suggested by linuxprinting.org, but which the CUPS manager never found, despite the fact that it comes installed with the system.

No need to click "Install driver" here, just click Forward and you come to Step 3 of 3, where all you have to do is fill in two comment fields labelled Description and Location.  Any text is good here.

Click 'Apply' and you're done.

3 days worth of reading through circularly unhelpful helpfiles (CUPS, Foomatic, linuxprinting, Xubuntu, Ubuntu,..) and finally gnome-cups-manager solves the whole problem in a grandma-friendly way.  Xubuntu NEEDS THIS.  That, or CUPS admin should detect and 'recommend' the installed gutenprint driver, instead of recommending 10 incorrect 'generic' drivers.

Thanks anyway, John, for your attempts at help.

---

### Post by OU812 on 2006-07-30
Sweet.

---

### Post by Coburn on 2006-11-19
> **OU812 said:**
> Try setting up the printer this way: Launch a web browser and enter this address:

[http://localhost:631/admin](http://localhost:631/admin)

This will take you through the steps of setting up your printer.

john

So far so good, but when I try to open the PPD file in /etc/cups/ppd that I installed with gutenprint...

It prompts me for my username and password, over and over again ](*,) 

Hope nobody else is having this problem.

Might be network related.  I'm client on a home network (NFS w/ Firestarter) that was set up by a gnubie--me.:-k


Update:

I successfully printed a test page on my Epson cx5000.  Before it was just page-feeding and not responding to job cancel.

Turns out I had installed the Gutenprint-en cx5100 driver, and cx4800 worked for me.

Correction:

Documentation reveals that you are not _supposed_ to be able to change administrative settings through the web tool.  Security.

You can edit a config file to allow that feature, but the documentation on how to do that is either wrong or not understandable by the average user.  AKA me.

---

