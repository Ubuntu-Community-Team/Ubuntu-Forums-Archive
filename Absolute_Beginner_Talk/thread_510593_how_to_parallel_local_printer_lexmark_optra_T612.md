---
title: "how to parallel local printer lexmark optra T612?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by ronny_d on 2007-07-26
I have on a Dell usb 1.1 computer Ubuntu Feisty Fawn 7.04 desktopversion. I am an absolute beginner on hardware. Before i had RedHat on other hardware: i plugged this Lexmark Optra T612 in and that was it, set my system on LPRNG instead of CUPS (somehow i did not like CUPS), but without any real effort the printer worked and this simply was no issue. But now... with Ubuntu Feisty Fawn 7.04 on the simple desktopcomputer i am using... i am at a loss. Of course: i started out positive, plugged in my printer and its iights were on, its own testpage working, then i so chose in 'system' the configuration / administration tool and chose 'printers' and got this automatic 'gnome-cups-add' or what and step 1: LPT#1, my printer has parallel connection, anyway step 2 my printer not detected, what do i have to fill out for description and location, i at firs did /dev/lp0 for location, but.... it did not work, anyway step 3 or whatever step it was i had to choose the driver and yes: Optra T612 on the list so i chose that one and then the connection of this printer..., i guess it is a problem,  it is unclear to me. After i had anyway configured all, no testpage came... ever, it said 'parport busy' and 'will retry in 30 seconds' and '%%no boundingsbox in header comment!', i do not understand this, then even each time when i had tried the configuration again i had checked back the properties, and each time my local printer was automatically set to networkprinter and ipp cups... and none of the times giving testpage via the software. On parport #1 both Epson and Canon are preconfigured by this cupstool. 

Is there another way to configure my laserprinter Lexmark Optra T612? Is the driver for Lexmark Optra T612 not working despite it being on the list in this Ubuntu Feisty Fawn 7.04? I also tried the bios in this Dell, but all i see is 'parallel port' and enter, when it but says: 'mode' which option has or 'ECP' or 'EPP' or 'AT' or 'PS/2' and only one option is allowed or mode 'OFF'; serial ports are on 'auto'; then there is DMA1 and DMA3, then there is I/O Address 378h but only when mode is 'ECP' and when mode is 'ECP' then too it says 'DMA channel.... off'; i do not know what this all means, it is from bios, and concerns the parallel port which i believe i need for my 'local' printer. 

Does anyone know how to configure this 'local' printer succesfully so it will print the testpages and so it would work or is my printer obsolete although its driver is still on the list? How can i set it in my system to the parallel port as a local printer, not a networkprinter?

---

### Post by ronny_d on 2007-07-26
P.S.: so when i configure my lexmark optra T612 succesfully as a 'local printer' and LPT#1 (because Epson and Canon are preset at parport#1 both and each with their own parport#1)  and it says "ready" in the printtool, this all goes very fast, i try a testpage from that printtool and it but does not print; i close the printtool and open it again and check the properties: my "local" printer is set to 'networkprinter' under IPP CUPS whatever it is and my description and path /dev/lp0 is not found, or parport busy, or %%noboundingsbox comment in header! or 'will retry in 30 seconds' or whatever it says to "excuse" it cannot print. Somebody help. This is way too complicated for me. There seems to be a conflict on "who" is using the parallel port and in the bios i do not know what to change there, i do not see i can add for example another parallel port or even whipe out the preset Canon and Epson on parport#1. I do not see them in the bios.

---

### Post by ramjet_1953 on 2007-07-26
This link may help you:

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_T612](http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_T612)

Regards,
Roger :cool:

---

### Post by ronny_d on 2007-07-27
Thanks. I checked out 
[http://openprinting.org/show_printer...ark-Optra_T612](http://openprinting.org/show_printer...ark-Optra_T612)
but the language in my printer is already set to 'ps emulation 2' or something, postscript level 2 anyway, and no pcl or such (although i can choose it, but i know such gives problems), so this does not seem to be the cause the CUPStool does not print... Also about the paper: i have no A4, but folio and i suppose then the paper has to be chosen as option '11x17', this is anyway an option in the print configuration tool and i also chose this option. It so seems to be solely some conflict at the parallel port and which device is using this, as in the CUPS printtool parport#1 is both for Epson and Canon preset, both their own parport#1, then there is an option as LPT#1 which i then choose for this Lexmark, then lateron i chose 'local printer or detected printer' and i so do not choose 'networkprinter', but when i check after failing to print out a testpage with the CUPS configuration tool, i see the properties have altered without me doing anything and put my printer on 'networkprinter' and also the parallel port cannot be found. For 'location' i typed the path /dev/lp0, but maybe that is not true? Though when i look with 'ls' in /dev, i see it has 'lp0'... 

I know this Optra T612 should work..., but what is wrong with my configuration that the CUPS tool does not print a testpage and cannot find the parallel port or cannot find the host or says parport is busy or sets anyway, in all cases, my 'local or detected printer' to "networkprinter"  (but i only notice this when i check again the properties of the printer configuration...)? 

Anyway: the language in my printer is set to 'ps emulation 2'; is there some in the CUPS tool that i have to alter? But this parallel port, LPT#1, i do not understand why it is switched and why my printer is set to 'networkprinter' by CUPS and then also has set 'on' the option "use another printer" or something and 'serial port'...., i do not understand this, and i wonder whether maybe the path /dev/lp0 is "wrong", though when i check in /dev i see there is located lp0. 

I so still do not understand why my Lexmark Optra-T612 cannot be configured. I however remember in RedHat when i chose this particular Lexmark in the list of drivers, RedHat automatically set it to another driver, some specific one i do not remember, but it all worked; not (yet?) now in Ubuntu Feisty Fawn 7.04 desktop... on a Dell usb 1.1 bios A04 ("A zero 4"); the printer itself seems to work, that is: when i print out a testpage from this printer itself, it prints it correctly.... 

So the printer language (ps emulation 2) is not the cause; the printer is set to it. The papersize is foliio and i so choose option '11x17' instead of A4. Maybe it is something with mode option 'ECP'  or mode option EPP in the bios of this Dell-computer? Still all this is going beyond my scope and i am absolute beginner in this hardware/software level. Somehow the computer does not communicate with the printer, except for that the printer's light is on 'green' and it is 'ready'...

---

### Post by ronny_d on 2007-07-27
P.S.: maybe it is the 'driver' somehow...; that is: that CUPS is different that 'lpr', that CUPS somehow maybe does not have the same "driver" as 'lpr' and therefore conflict and no testpage from via cupstool... I remember in RedHat with this Lexmark Optra T612 i set my printersystem to LPRNG because somehow CUPS gave problems and anyway somehow by then too CUPS did not let my Lexmark print, but LPRNG did without problem. But i do not see a LPRNG-possibility in Ubuntu Feisty Fawn 7.04... 

Anyway: when CUPS, do i need to set the path /dev/lp0 as location for my printer to some path in CUPS? 

Theoretically it is said that my Lexmark Optra T612 cannot work on LPRNG when it cannot work on CUPS and that it should work on CUPS..., but practically until now it has never worked on CUPS... 

But so maybe some is different in drivers via LPRNG or CUPS? Or so maybe i have to change the location of my printer in the CUPS config tool in Ubuntu Feisty Fawn 7.04?

---

### Post by ronny_d on 2007-07-27
I mean: all this driver level "CUPS" and "LPRNG" is complicated for me... How it all exactly works... it confuses me what to type in this Ubuntu Feisty Fawn 7.04 desktop CUPS-printerconfigurationtool... (as i typed for location /dev/lp0) and all i got was this obstacle with the parallel port... and all confusion anyway. I know my printer SHOULD work..., it is a postscript printer..., on a Linux system, but so then maybe there is a difference in CUPS-related driver for my printer and lpr-related driver for my very same printer.... (that the path /dev/lp0 is for lpr-related driver maybe??) So what if in CUPS... would be the path of my printer to type in for location maybe? So the apparant conflict of parallel port or anyway its location cannot be missed out by... CUPS...? Maybe my printer is so not located in some path that relates to CUPS? This is deeplevel configuration for me and is confusing, i am absolute beginner in this "machine level".  What could be an alternative 'path' for location?

---

### Post by ronny_d on 2007-07-27
> **ronny_d said:**
> I mean: all this driver level "CUPS" and "LPRNG" is complicated for me... How it all exactly works... it confuses me what to type in this Ubuntu Feisty Fawn 7.04 desktop CUPS-printerconfigurationtool... (as i typed for location /dev/lp0) and all i got was this obstacle with the parallel port... and all confusion anyway. I know my printer SHOULD work..., it is a postscript printer..., on a Linux system, but so then maybe there is a difference in CUPS-related driver for my printer and lpr-related driver for my very same printer.... (that the path /dev/lp0 is for lpr-related driver maybe??) So what if in CUPS... would be the path of my printer to type in for location maybe? So the apparant conflict of parallel port or anyway its location cannot be missed out by... CUPS...? Maybe my printer is so not located in some path that relates to CUPS? This is deeplevel configuration for me and is confusing, i am absolute beginner in this "machine level".  What could be an alternative 'path' for location?



I guess, for now, that the cause of trouble configuring my lexmark is... that the parallel port broke, somehow broke, by  don't know what causes..

---

### Post by ronny_d on 2007-08-05
Oops: i guess 11x17 for folio is wrong... , would be 8.5 x 13..., though i am not sure of this either. But defect is that CUPS simply neglected folio option for papersize, i suppose. (So stupid...) I cannot remember CUPS ever had folio paper print option, though LPRNG did... (well: if i remember well; anyway LPRNG never gave problem in printing folio, CUPS does... as far as i can see).

---

### Post by ronny_d on 2007-08-05
... Or it is "name confusion"..., different 'size' names... and measurement, different degrees... (like celsius and fahrenheit, centimeters and inches..., even "comma" and "dot" in numbers... aren't standard either (here the comma means a dot where there the dot means what is comma here in numbers), and so on, and so on, and so on...). Anyway: 'Legal Size' (legal?)  would be 8. x 14, 'letter size' would be 8.5 x 11 inch..., though... folio (FOLIO..., folio...) is 8.5 x 13... (aha!), just an inch of difference only, hey! (I do not like stupid and unnessary problems like these, that is: problems that would not have to be 'there' anyway... if "the people" would be more global minded, broadminded..., openminded...  so little room, if any at all, would be left for the neglectful and stupid mind who but can come up with omissions).

---

