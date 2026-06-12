---
title: "Help with Xubuntu and EPL-5900L printer"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by xiombarg on 2007-11-12
Hi,

I'm new to the forums, and pretty new to Xubuntu, and would really like some help installing my printer.

The printer is an Epson EPL-5900L laser printer. It requires a specialised driver (non postscript), for which I'm trying to use the [epsonepl]("http://sourceforge.net/projects/epsonepl/") project.

I have downloaded the source, and built it with:
```
sudo ./configure
sudo make
sudo make install

```
This all appears to build correctly.

I believe Xubuntu is using foomatic, so I looked in a foomatic subdirectory within the project directory. There is a script "install_debian", which I don't think I managed to successfully execute, though I did run the commands individually in a bash terminal. The script is as follows:
```
#!/bin/bash

#### Debian
# Theo & Geert say "Thanks" to the EpsonEPL people

# Add the xml files to the foomatic database.

cp ../foomatic/driver/*  /usr/share/foomatic/db/source/driver/
cp ../foomatic/opt/*     /usr/share/foomatic/db/source/opt/
cp ../foomatic/printer/* /usr/share/foomatic/db/source/printer/

##### Generate PPDs and install them

foomatic-datafile -t cups -d epl5700l -p 312297          >../foomatic_PPDs/Epson-EPL-5700L-epl5700l-cups.ppd
foomatic-datafile -t cups -d epl5800l -p Epson-EPL-5800L >../foomatic_PPDs/Epson-EPL-5800L-epl5800l-cups.ppd
foomatic-datafile -t cups -d epl5900l -p Epson-EPL-5900L >../foomatic_PPDs/Epson-EPL-5900L-epl5900l-cups.ppd
foomatic-datafile -t cups -d epl6100l -p Epson-EPL-6100L >../foomatic_PPDs/Epson-EPL-6100L-epl6100l-cups.ppd
foomatic-datafile -t cups -d epl6200l -p Epson-EPL-6200L >../foomatic_PPDs/Epson-EPL-6200L-epl6200l-cups.ppd

gzip -9f ../foomatic_PPDs/Epson-EPL-*-cups.ppd

cp -av ../foomatic_PPDs/Epson-EPL-*-cups.ppd.gz /usr/share/cups/model/foomatic-ppds/Epson/

# end of script
```

I didn't run the commands which directly reference printers other than the EPL-5900L. There were a couple of errors when I ran these commands:

When copying the XML files, there was an error warning for each 'cp' command, that a subdirectory 'CVS' was not copied. The original script didn't use a recursive ('-r' switch) copy, so I assumed this would not be a problem. Any ideas on this?

When running the last 'cp' command in the script, which places a foomatic PPD file in  /usr/share/cups/model/foomatic-ppds/Epson/ , I got an error, saying no such directory existed. I just created the directory tree, and then copied the files there again.

Then, when I turned on my printer, connected to the USB port, the printer was detected, and I got a message in the top right corner of my screen, saying it was ready to print. The message had a button to configure the printer, which I did. I confirmed that the EPL-5900L foomatic PPD was selected, and set it as the default printer, with flow control 'off' (flow control off is described as being simpler to set up, and is fine for printing small files).

I have been using 'system-config-printer.py' accessed by Applications>Settings>Printing to configure the printer. I have tried printing a test page, but the 'printer state:' field remains as 'idle', and I think the job doesn't get queued correctly (I think a job queue icon should become available in the top right of the screen, yes?). No lights flashed on the printer.

I have also tried using the following two commands, with the same result for each, posted following:

commands:
```
./ps2epl epl_test.ps usb://EPSON/EPL-5900L
./ps2epl epl_test.ps /dev/usb/lp0
```

results:
```
oli@orac:~/epsoneplijs/epsoneplijs-0.4.0$ ./ps2epl epl_test.ps usb://EPSON/EPL-5900L

-e ***** Printer: "EPL5900L" *****

-e ***** Paper Size: "a4" *****

-e ***** using parameters: "EplDpi=300,EplRitech=on,EplDensity=3,EplTonerSave=on,EplFlowControl=off" *****

GPL Ghostscript SVN PRE-RELEASE 8.61 (2007-08-02)
Copyright (C) 2007 Artifex Software, Inc.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
GPL Ghostscript SVN PRE-RELEASE 8.61: **** Could not open the file usb://EPSON/EPL-5900L .
**** Unable to open the initial device, quitting.

```

I had a look at the file /dev/usb/lp0, and the icon has an 'X' drawn on it. Does that mean it is not functioning?

I have a few ideas about what might be wrong, but I'm not sure how to move forward:
1)  Possibly the directories listed in the 'install_debian' script, are not appropriate for Xubuntu. Does Xubuntu place the CUPS/foomatic files in a location different from Debian?
2)  Possibly 'system-config-printer.py' is not correctly accessing a filter, which is needed to process a postscript file into a proprietary .epl file (ps2epl)
3)  Possibly something else related to Xubuntu accessing a USB port
4)  Possibly an incompatibility with the GPL Ghostscript, as there is mention about an afpl ghostscript hack for this printer. Could it be related to Ghostscript?

If anyone has any ideas, I would greatly appreciate the help. Thanks, and sorry for the rather long post.

xiombarg

---

### Post by xiombarg on 2007-11-14
bump- Should I be asking this in the Main Support Categories, rather than Absolute Beginner Talk?

Anyone here have any ideas that could help me?

Cheers, xiombarg

---

