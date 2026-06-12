---
title: "Epson Photo RX640"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by DaveSmart on 2006-09-14
Hi,
I'm brand new to Linux (fed up with windows!)I have installed Ubuntu 6.06lts and begun to set up my system. My old HP laserjet 4L setup a treat but my new Epson photo RX640 does not want to play, Add printer detects the printer and suggests a driver which I duely accept but the test page does not print, all I get is a load of blank pages until I switch off the printer. I know this is probably something simple but any help would be appreciated, step by step hand holding type instructions would be great!
Thanks.
Dave

---

### Post by Najand on 2006-09-14
Can this link help you?
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX640]("http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX640")

---

### Post by DaveSmart on 2006-09-14
Thanks for looking Najand, but the link you gave does not help. Any other ideas???
Cheers all
Dave

---

### Post by chrisccoulson on 2006-12-01
I was thinking of buying this printer. Does anyone have it working? The info on linuxprinting.org for this printer is misleading.

Cheers

---

### Post by cotcot on 2007-01-08
The info is indeed not correct. I have commented the page. The RX640 is still somewhat too new to have already full support.
The RX640 is according to the linux driver download page of Avasys not (yet ?) supported. There is some kind of a generic driver (pipslite) that I could install and use the printer with, but the quality is not so good. I think it is only a matter of time to get the RX640 supported by gutenprint.
The scanner part is working fine using iscan 2.4.

---

### Post by HavarN on 2007-04-29
I got the printer printing with this driver on feisty fawn:
[http://openprinting.org/show_driver.cgi?driver=st640ih.upp&fromprinter=Epson-Stylus_Photo_RX640](http://openprinting.org/show_driver.cgi?driver=st640ih.upp&fromprinter=Epson-Stylus_Photo_RX640)
Used System->Administration->Printing Installed the printer as RX600, right-clicked->properties->Driver tab, Install driver... the second st640ih.upp driver made the printer able to print a test-page.

Though the color-reproduction is not very good. Red is orange,  blue is purple, cyan is blue and black is grey.

But it's printing and that's progress :)

Update:
[SIZE="4"]Printing working with perfect photo quality[/SIZE]

I got the printer working with perfect photo-quality and great color reproduction using the official driver from Avasys.

The official link to the download site:
[http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html)

I downloaded the rpm, converted it to .deb and attached the .deb, the GPLed sources and the resulting .ppd to this post. Hope this helps someone.

If you download this .deb, install it by double-clicking on it using nautilus, open it with gdebi.
You may have to configure the driver after installing it. That can be done by opening a Applications->Accessories->Terminal:
$ sudo /usr/local/EPAva/LITE/scripts/setup-cups.sh
(choose /dev/usblp0 instead of the default /dev/usb/lp0 if you're using usb for the printer).
$ sudo /usr/local/EPAva/LITE/pipslite-install

Notes:
Now you should be able to install the printer using gnome-cups-manager. If not, you may have to browse for a custom driver (the .PPD file) in step 2 of the "New Printer"-wizard.

The official driver doesn't provide any options to choose quality settings. I'm guessing it always prints with perfect photo-quality which is not always good. To solve this you could create two printers the way I've explained in this post. Using the st640ih driver for drafts and the official driver for photos.

---

### Post by ShirishAg75 on 2007-04-30
Good job there HavarN, welcome to the community, I liked how you added the link to [https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersEpson) . Pretty nice. Carry on the good work. Cheers :)

---

### Post by cotcot on 2007-04-30
I also own a RX640. I got it working in Feisty with the epson avasys driver in 32 bit. I installed Feisty 32 bit on my amd64 box because of the unavailability of a 64bit version of the pipslite rpm. (and a couple of other apps in 32 bit)

---

### Post by Vprobe on 2007-07-02
Hi!

I did as told on this topic, installed cups succesfully and when I go to "add printer" it succesfully finds my printer. But there is no driver for this printer so I downloaded the .PPD -file and added it to the drivers. When I select the driver for RX640 everything seems to be ok, but the printer seems to be on "stopped" -state instead of "ready".
I can change the state but still printing doesnt work. I can see my current printing jobs which all are on a state of "job-stopped". Cant do anything about this, nothing, nothing goes through.
If I select a driver for RX630 or some other "nearby" -model, the printer just spools empty paper until the paper is finished or the printer shut down.

Can somebody tell me a solution for this problem? Help would be much appreciated!

yours,
Juho

---

### Post by dukemaru on 2007-08-19
Any way to get this to work on 64bit ubuntu?

---

### Post by cotcot on 2007-09-29
Compile gutenprint version 5.1.3. There is a driver in it for the RX640 or wait for Gutsy
After compilation run>  cups-genppd.5.1
Then configure the printer cups ([http://localhost:631/](http://localhost:631/)).

---

### Post by cotcot on 2007-09-29
Sorry for double post.

---

### Post by HavarN on 2008-04-29
Still working with gutenprint in Ubuntu Hardy 8.04.

It wouldn't print automagically when plugged in (as in Gutsy)...

I had to choose ink type:
system-config-printer -> Printer Options -> Printer Features Extra 3 -> Ink Type -> Six Color Photo

---

### Post by cotcot on 2008-05-05
The RX640 worked out of the box with a new 8.04 64 bit install. Colors and were not OK. I changed with ```
system-config-printer

``` the RX640 driver from the simplified one to the full driver and adjusted color balance (0.7 for cyan and yellow , brightness to 1.5 and saturation to 0.6.

---

