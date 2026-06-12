---
title: "hp printer"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-03-01
have an hp deskjet 712. I have it installed on another box but cannot install it on this one....the gnome printing app will not open when clicked on it........after a while get error message that it can't contact cups server........how can I get the printer installed?

---

### Post by stuporglue on 2006-03-01
What happens if you try to access [http://localhost:631](http://localhost:631) ? It's the web interface to CUPS

---

### Post by sailor2001 on 2006-03-01
it doesn't come in

---

### Post by %hMa@?b&lt;C on 2006-03-01
try ```
sudo ifconfig lo localhost
```

---

### Post by sailor2001 on 2006-03-01
that doesn't do anything after asking for password

---

### Post by %hMa@?b&lt;C on 2006-03-01
it just sets up the loopback interface on localhost. now try to see if it works

---

### Post by %hMa@?b&lt;C on 2006-03-01
if you need any more help, get on msn
mine:BigBigBook@hotmail.com

---

### Post by darth_vector on 2006-03-01
HP's tend to work a lot better when using the HP JetDirect than when using CUPS. give it a go and see.

---

### Post by Dylan103 on 2006-03-01
I have a solution.

Linux Operations
---------------------------------
System > Administration > Printing
Now click Add New Printer.
Select Netowork Printer.
Then Windows Printer(SMB)
See Windows Operations for required information and next steps.

Windows Operations
---------------------
Go Start > Run and type in CMD
Then type ipconfig in the dos window.
Find and write down your IP Adress.
Then, 
Start > Control Panel > Printers And Other Hardware > Printers And Faxes. Then Right click the current printer and click Sharing.
Click the checkbox beside Allow Sharing, and give it a name such as  Printer or something.

Linux Operation Part2
------------------------
In The Host area put the IP adress of the Windows Computer.
In the Printer area put the name of the printer in the sharing ( My example printer ). 
Now hit Forward, Then chose your Printer Manufacturer and Series.
Then hit Apply.

And thats it, it worked for me, hopefully you to.

---

### Post by sailor2001 on 2006-03-01
sorry  guys, none of the suggestions work.. I do  have pnm2ppa.ppd on the desktop now, however

---

### Post by sailor2001 on 2006-03-02
in going to pnm2pp it stated that gnome print manager  doesn't work very good but foomatic does...Now the question is.....foomatic askes for keyring password... How do I get that and set it so I can access foomatic?

---

### Post by Pragmatist on 2006-03-20
Try these instructions.  If they don't work for you, please tell us *exactly* what happend at each step.

[https://wiki.ubuntu.com/HpPrinterInstallationAndMaintenanceBreezy?highlight=%28printer%29](https://wiki.ubuntu.com/HpPrinterInstallationAndMaintenanceBreezy?highlight=%28printer%29)

---

### Post by Sef on 2006-03-20
Thanks Pragmatist.  The HP maintenance section there has been really helpful for me.

---

### Post by sailor2001 on 2006-03-21
when on wireless, cups will not come in... straight wire to router it does.....however the tutorial [https://wiki.ubuntu.com/HpPrinterIns...=%28printer%29](https://wiki.ubuntu.com/HpPrinterIns...=%28printer%29)
doesn't solve the problem
sudo gedit pnm2ppa.conf    gives me this:
tom@tom:~$ sudo gedit pnm2ppa.conf
Model not found, discarding config

(gedit:17602): GnomePrint-WARNING **: Could not create filter from description 'frgba': filter 'frgba' is unknown

** (gedit:17602): WARNING **: gpa_transport_selector_rebuild_combo, could not set value of Backend to lpr

(gedit:17602): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd character encoding: ISOLatin1, trying CSISOLatin1

** (gedit:17602): WARNING **: gpa_transport_selector_rebuild_combo, could not set value of Backend to lpr

(gedit:17602): GnomePrint-WARNING **: Problem while creating filter from 'frgba': filter 'frgba' is unknown

(gedit:17602): Gtk-WARNING **: Ignoring the separator setting
tom@tom:~$

---

### Post by Pragmatist on 2006-03-21
how did you install pnm2pp?

---

### Post by sailor2001 on 2006-03-22
downloaded in synaptics

---

### Post by Pragmatist on 2006-03-22
Ok, just to summarize what we know (for the benefit of the rest of the thread since you obviously knew some of this already :) )

1. The hp 712c can't be used with regular drivers. It requires pnm2ppa
[http://hpinkjet.sourceforge.net/faqs.php](http://hpinkjet.sourceforge.net/faqs.php)
[http://sourceforge.net/projects/pnm2ppa/](http://sourceforge.net/projects/pnm2ppa/)

Synaptic has several packages that look helpful.  These are the ones I would install:
[B]pnm2ppa
printconf
foomatic-gui[/B]

Two questions at this point:
1.) Have you installed **printconf** and **foomatic-gui** ?
If not, try using those.

2.) Have you installed **foo2zjs** If you did, **UNINSTALL IT**

3.) In your second-to-last post you said this:
[QUOTE][when on **wireless**, cups will not come in... **straight wire** to router it does...../QUOTE]
What are you talking about when you say wireless/straight wire??

---

### Post by sailor2001 on 2006-03-22
printconf:

Package printconf has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list    (quote from synaptic)

have foomatic installed, but cannot access it because of keyring (have no idea what the password would be....tried everything for that)

I was operating wireless with the router about 4' above me.......wired direct in from router to pc and able to get cups that way

checked synaptic and don't have that other foomatic program you mentioned

---

### Post by Pragmatist on 2006-03-22
I'm having some trouble understanding your responses.  Please try to be more specific (assume I know nothing).

> Package printconf has no available version, but exists in the database.This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list (quote from synaptic)

Where exactly did you read this?  In Synaptic?  Ok, from the time you open Synaptic please tell me every action you take and every reponse you get from Synaptic.  This way I can see when and how the response occurs.  When you get the response, where do you get it from? Is it a box with an ok/cancel, is it from the terminal?  Does your entry in synaptic, for the package printconf, have a solid green box next to it?

> have foomatic installed, but cannot access it because of keyring (have no idea what the password would be....tried everything for that) Try installing this package in synaptic: **gnome-keyring-manager**

> I was operating wireless with the router about 4' above me.......wired direct in from router to pc and able to get cups that way  I don't understand what your saying.  So a couple of questions:
1.) What does your router have anything to do with enabling your HP 712c ?  Are you printing over a network?

2.) >  with the router about 4' above me
Is the physical position of the router relevant in some way?

---

### Post by sailor2001 on 2006-03-22
from synaptic:
Automatically configures USB and parallel printers with CUPS
Foomatic is a printing system designed to make it easier to set up
common printers for use with Debian (and other operating systems).
It provides the "glue" between a print spooler (like CUPS) and
your actual printer, by telling your computer how to process files
sent to the printer.

This package detects printers attached to the parallel or USB ports
of your computer, and automatically establishes printer queues using
Foomatic for those printers.  These queues can be managed using the
CUPS web interface at [http://localhost:631/](http://localhost:631/) or by using the
Foomatic-GUI tool.

Some low-end inkjet and laser printers that use proprietary languages
(sometimes erroneously called "WinPrinters" or "GDI printers") will
require either the foo2zjs or pnm2ppa package to work.

Project Home: [http://savannah.nongnu.org/projects/foomatic-gui/](http://savannah.nongnu.org/projects/foomatic-gui/)

Development weblog: [http://blog.lordsutch.com/?topic=13](http://blog.lordsutch.com/?topic=13)

there is no foo2zys in synaptics.....no the box for printconf is not green.it will not install (see note from previous post..)
I'm on a protected telephone co. dsl..a terrible place to be...I think they pump too many ppl on the same broadband.......hooking up direct gives me a LITTLE extra broadband, but not much. Actually I think I can get faster connections on a dial-up.  Foomatic is and has been installed, but that asks for the keyring. I've put in a new password in that config, but that won't recognize it and open foomatic......I've had the printer since my first computer, not that many years ago...maybe it's about time to give up old faithful and get a new one..you've been helpful, alas

---

### Post by Pragmatist on 2006-03-22
Your last post
> Foomatic is and has been installed, but that asks for the keyring
My post previous to this one
```
 Try installing this package in synaptic: gnome-keyring-manager
```

Did you install gnome-keyring-manager? ](*,) 

> no the box for printconf is not green.it will not install (see note from previous post..)
You still haven't explained when where and how this response from synaptic happens.

> [I'm on a protected telephone co. dsl..a terrible place to be
You said previously:
>  I was operating wireless
What I want to know is:  What does wireless have to do with your problem?

> ..maybe it's about time to give up old faithful and get a new one..you've been helpful, alas
This, of course, is your choice.  However, it appears that you wanted to give this older printer a shot.  In order to do that, you need to communicate very clearly and specifically about what your experiencing, error messages you get, and so on.  Remember: We aren't sitting next to you.  You are our eyes.

---

### Post by sailor2001 on 2006-03-22
the keyring manager had been installed............sometime ago........when trying to install the cupsconf, the message comesup as quoted before. "probably obsolete" when trying to access the foomatic, it asks for keyring password...password I put in as a new keyring doesn't work.  I don't know what else to explain.. I do have 2 computers, is why I am wireless.....one is in another building is why I have the router mounted high (for reception purposes) I just checked and my link is only at 27mps when it has to be near 30 to be able to recieve. at 27 it keeps dropping off....Direct wired to router is a little better but still VERY slow.......that's why I can't access cups when I'm wireless. times out. Would complain to the isp but that's like spitting in the wind...No isp cometition here......

---

### Post by sailor2001 on 2006-03-22
the response from synaptic comes up when I try to apply download for cupsconf. It will not apply........

---

### Post by Pragmatist on 2006-03-22
What happens if you just use ONE computer and attach the HP 712c to that one computer?

Try this in a terminal:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
Just cut & paste everything that shows up in the terminal and give it to us here.

---

### Post by sailor2001 on 2006-03-22
I'm not networking the printer......used only in the inhouse box......
I do keep updates on a regular basis.....
tom@tom:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [43.9kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:7 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [13.4kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [29.3kB]
Get:14 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:15 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [4750B]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:17 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg [65B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [36.0kB]
Get:19 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Get:20 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:21 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:23 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [17.5kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:30 [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release [702B]
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Fetched 271kB in 1m36s (2791B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tom@tom:~$

---

### Post by BLTicklemonster on 2007-12-29
Hey look, a dead horse, let's kick it and see what happens.

I have a deskjet 720c that i can't get to print. I try to do a test page, and it will automatically say it's out of paper, then feed a page halfway. I press feed, it spits that page out, prints the very top of a test page (half the ubuntu logo) then stops.

I get this if I try to print a document from gedit

```
(gedit:17188): GnomePrint-WARNING **: Could not create filter from description 'frgba': filter 'frgba' is unknown

** (gedit:17188): WARNING **: Can't create printer "PDF" because the id "PDF" is already used

(gedit:17188): GnomePrintCupsPlugin-WARNING **: The CUPS printer PDF could not be created


(gedit:17188): GnomePrintCupsPlugin-WARNING **: The data for the CUPS printer PDF could not be loaded.

(gedit:17188): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterSelect': filter 'GnomePrintFilterSelect' is unknown

(gedit:17188): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:17188): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:17188): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterClip [ GnomePrintFilterMultipage ]': filter 'GnomePrintFilterClip' is unknown

(gedit:17188): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): libgnomeprintui-CRITICAL **: gnome_print_layout_selector_load_filter: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:17188): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

** (gedit:17188): WARNING **: could not set the value of Settings.Document.Filter, node not found

** (gedit:17188): WARNING **: could not set the value of Settings.Document.Filter, node not found

** (gedit:17188): WARNING **: Invalid borders specified for theme pixmap:
        /home/bill/.themes/MacOS-X/gtk-2.0/entry2.png,
borders don't fit within the image

(gedit:17188): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GnomePrintConfig'

** (gedit:17188): CRITICAL **: gpa_node_set_path_value: assertion `parent != NULL' failed

** (gedit:17188): CRITICAL **: gpa_node_set_path_value: assertion `parent != NULL' failed

** (gedit:17188): CRITICAL **: gtk_source_print_job_set_config: assertion `GNOME_IS_PRINT_CONFIG (config)' failed

(gedit:17188): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterSelect': filter 'GnomePrintFilterSelect' is unknown

(gedit:17188): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gedit:17188): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:17188): GnomePrint-WARNING **: Could not create filter from description 'GnomePrintFilterClip [ GnomePrintFilterMultipage ]': filter 'GnomePrintFilterClip' is unknown

(gedit:17188): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): libgnomeprintui-CRITICAL **: gnome_print_layout_selector_load_filter: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(gedit:17188): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:17188): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(gedit:17188): GnomePrint-CRITICAL **: gnome_print_config_unref: assertion `GNOME_IS_PRINT_CONFIG (config)' failed

```

---

### Post by BLTicklemonster on 2007-12-29
Huh. I set the printer location to printer connected to LPT1, and it's printing out the test page.

Figures.

---

