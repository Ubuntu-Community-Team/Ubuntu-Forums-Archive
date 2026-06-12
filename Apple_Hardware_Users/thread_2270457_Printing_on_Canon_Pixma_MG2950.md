---
title: "Printing on Canon Pixma MG2950"
date: 2015-03-23
forum: Apple Hardware Users
---

### Post by Martin_Srensen on 2015-03-23
Hello,

I have Lubuntu 14.04.2 running on an G4 iMac iLamp, I now would like to print...

I have got the printer above, and have at Canon found drivers for Intel. There is also source code available, but before I start learning command line build and install I would like to know if I am wasting my time? Virtual newbie in these arts.

The printer also has WiFi built in, but I have no more progress with that.

Thanks, Martin

PS. Where do I change the keyboard? I have a Spanish and the system seems to have forgotten

---

### Post by pdc on 2015-03-23
Hi Martin;

for the Canon MG2900 series, as you say, Canon provide linux drivers; they come in three formats: rpm and debian and source code; for each, they come in 32bit and 64bit formats;

............so you need the debian; and Canon provide an install script that should do all for you ............. you can ignore the source code variant!!

-____________

Background: to set up any printer; one seems to need to do 3 things:

1) establish a connection
2) install the drivers
3) register the printer on your system

_____________

1) connection: I don't know if you have set it up for wifi yet ?? Canon UK provide an excellent guide for a huge range of Canon inkjets on how to do this [http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/](http://www.canon.co.uk/support/consumer_products/pixma_printer_wireless_connection_setup/)

........sadly.....yours is very new ...not added yet; 

____________

2) and 3) go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html) for the debian package and click to download and SAVE what will be [COLOR="#008000"]cnijfilter2-5.00-1-deb.tar.gz[/COLOR] (Canon now seem to supply this package for all their new inkjets; so whichever printer you buy, this is the install)

if you open a terminal; please ask if you don't know how; and paste in these commands: again, please ask if you need guidance ....hit ENTER after each paste ........

```
cd Downloads
```

```
tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
```

```
cd cnijfilter2-5.00-1-deb
```

```
./install.sh
```

............that final command will start the install script running; it will ask you for your sudo password, so have it ready ...................

_________________

so by using the Canon install script it should both download and install the drivers; and also then register the printer for you

___________

for running the scanner side, Canon supply ScanGearMP from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html) and it comes down as [COLOR="#008000"]scangearmp2-3.00-1-deb.tar.gz[/COLOR]

It installs in the format described above; and runs first time from a terminal with the command ```
scangearmp2
``` and thereafter one sets up a launcher...............details provided if you would like them

---

### Post by Martin_Srensen on 2015-04-03
> **pdc said:**
> Hi Martin;

for the Canon MG2900 series, as you say, Canon provide linux drivers; they come in three formats: rpm and debian and source code; for each, they come in 32bit and 64bit formats;

............so you need the debian; and Canon provide an install script that should do all for you ............. you can ignore the source code variant!!

-____________


Hi,

Thank you for the detailed instructions, I only got around to try now as business took priority.

I think you are mistaken regarding the source code variant, what I get is 

```
Command executed = sudo dpkg -iG ./packages/cnijfilter2_5.00-1_i386.deb
dpkg: error processing archive ./packages/cnijfilter2_5.00-1_i386.deb (--install):
 package architecture (i386) does not match system (powerpc)
Errors were encountered while processing:
 ./packages/cnijfilter2_5.00-1_i386.deb
Command executed = sudo dpkg -P cnijfilter2
dpkg: warning: ignoring request to remove cnijfilter2 which isn't installed
```

Doesn't look promising to me. Any ideas?

Thanks, Martin

---

### Post by affkar on 2015-10-06
@pdc

Thanks a ton. both printing and scanning worked for me.

---

### Post by U_Mate on 2016-03-30
Thanks for the info. It has been very useful to me.
But I do not get to run the ocr. 
Do you know how to make it work ocr?
Thanks.

---

