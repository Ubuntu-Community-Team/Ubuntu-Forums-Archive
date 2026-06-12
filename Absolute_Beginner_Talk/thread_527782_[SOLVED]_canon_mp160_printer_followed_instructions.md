---
title: "[SOLVED] canon mp160 printer: followed instructions but cannot print"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by ftp1234 on 2007-08-17
Hi

I am new to Ubuntu.
I tried to install the driver for Canon MP160 printer using the instructions posted at
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)
(I have pasted the instructions in the end for convenience)

(Sorry for the long post. I have tried to list everything I tried so far)

So after following steps 1 to 6, I powered on the printer.
I tried to print something from Firefox, but nothing happened.

So I went to System->Administration->Printing, 
I saw the Canon Printer there.
Right-clicked, saw Properties and there it showed me as a Network Printer.
I changed it local printer and the pending jobs from Firefox started printing.
But the printing was extremely slow.

In the properties section, the driver shown was something different; 'bcj????' or something
I tried to click on Install Driver and give the path to the ppd file.
On selecting the canon's ppd file in /usr/share/cups/model, 
I got the following error message

[B]The PPD
	/usr/share/ppd/custom/canonmp160.ppd
is already installed
[/B]
Why do I get this error message?
(My guesses. 1. I installed the driver with a wrong URI ?? What is this URI anyways? Is it same for everyone using Canon MP160?
2. I installed the driver before powering on the printer.
3. Something else)

Later, I removed the printer using the same menu.
Again did "Add Printer" and it shows me 2 options from the printers it detected.
1. Canon MP160 (Canon MP160 USB # 1)
2. Canon MP160 (USB Printer # 1 with status readback for Canon IJ)

I was not sure which one to select.
I tried both, and each time, got the same message when installing the .ppd file
If I choose the recommended driver (MP160 Ver. 2.70), I cannot print.
I also tried choosing MULTIPASS MP150, and printing was extremely slow.

Please advise how do I install the .ppd for my printer and hopefully get it working like others did using the instructions below.

Thanks,
Ftp1234

---------------------------------------------------------------------------------------
INSTRUCTIONS that I followed to install driver for Canon MP160 printer

Note: It is easier to use the "MULTIPASS MP150" driver that comes with Ubuntu 7.04 (and may come with other versions or distributions), especially if the printer is on your network rather than locally connected. This driver is confirmed to work, however you should only use this if Canon's official driver does not work for you.

Recommended driver: Canon open source drivers

The driver can be downloaded from Canon Asia ([http://www.canon-asia.com](http://www.canon-asia.com)). Printing and scanning are working.

It's not _that_ easy to install in Ubuntu, but it comes with an Installation Guide that works. For Ubuntu 6.06, 6.10 and 7.04, these are the instructions:

1. Install alien [sudo apt-get install alien].

2. Download the 4 RPMs (2 for printing, 2 for scanning).

3. Install with [sudo alien -i --scripts file1.rpm file2.rpm file3.rpm file4.rpm]).

3. Install libpng3 with [sudo apt-get install libpng3].

4. Install libtiff3 (or [sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3]) for scanning.

5. Restart Cups daemon with [sudo /etc/init.d/cupsys restart].

6. Install with [cd /usr/share/cups/model;sudo lpadmin -p MP160 -P canonmp160.ppd -v cnij_usb:/dev/usb/lp0 -E].

7. Install libxml1 with [sudo apt-get install libxml1] for some support programs to work, as printuimp160 (in /usr/local/bin/)

---

### Post by mikeyphi on 2007-08-17
When you right-click on the printer properties - select the Driver tab, 
Manufacturer should say: Canon
Model should be: Multipass MP160
Driver should be: High Quality Image (Gutenprint CUPS) (expert)

If these options are selectable - choose them, it should increase printer speed but the printer will still be slower than expected.

---

### Post by ftp1234 on 2007-08-17
I managed to get printouts using the following method
First install the driver using the following instructions
[http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP160)

Then I turned on the printer.
In a browser, pointed to [http://localhost:631/](http://localhost:631/) which is the CUPS web interface to configure
printers.

There were 2 choices offered by CUPS
1. CANON MP160 (USB # 1) printer
2. Canon MP160 (USB printer 1 with status readback for Canon IJ)


I added the CANON MP160 (USB # 1) printer (choice 1)

(NOTE: Adding choice 2 does not work)

When asked for selecting the driver, it showed me MP160 ver.2.70 in the list
(I suppose this option was listed because I had installed the linux driver for MP160 from canon website)

And then I can print pages just like I did from Windows.

Later in the CUPS web interface, I also tried to add the (choice 2) Canon MP160 (USB printer 1 with status readback for Canon IJ) printer with the same driver mentioned above.
But printing to this printer didn't work.

So I got the printing part working.

But there are a few questions I am curious about, which didn't get solved.
When I go to CUPS interface, I see the 2 printers I added as below.
 	
Canon_MP160_USB_1
Description: Canon MP160
Location: Local Printer
Make and Model: Canon MP160 Ver.2.70
Printer State: idle, accepting jobs, published.
Device URI: usb://Canon/MP160


USB_Printer_1_with_status_readback_for_Canon_IJ
Description: Canon MP160
Location: Local Printer
Make and Model: Canon MP160 Ver.2.70
Printer State: idle, accepting jobs, published.
Device URI: cnij_usb:/dev/usblp0

The interesting thing is when I followed step 6 in the driver installation instructions,
the last option to 'lpadmin' was '-v cnij_usb:/dev/usb/lp0'
Was that a typographical error? Should it have been /dev/usblp0, as shown for the 2nd printer above? What is a URI ? What is cnij_usb ?
Even if its as above, printing to the 2nd printer doesn't work anyways.

So was the last command (step 6) not necessary?
Just following steps 1 to 5, and using CUPS config web interface could probably suffice (although I haven't tried it)

Also, does anyone know how to scan using MP160? I believe I have installed that driver while installing the printer driver too.

Thanks,
Ftp1234


> **mikeyphi said:**
> When you right-click on the printer properties - select the Driver tab, 
Manufacturer should say: Canon
Model should be: Multipass MP160
Driver should be: High Quality Image (Gutenprint CUPS) (expert)

If these options are selectable - choose them, it should increase printer speed but the printer will still be slower than expected.

---

