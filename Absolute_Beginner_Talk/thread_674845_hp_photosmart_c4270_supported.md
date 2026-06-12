---
title: "hp photosmart c4270 supported?"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2008-01-22
Hello,

I am about to buy a new printer, but looking at the future I do want a printer that is supported in Ubuntu. I currently have a hp deskjet 2430 which prints, but a blank piece of paper comes out. Nevermind about that one, I want to replace it anyway.

Now I am looking at the hp photosmart c4270 which is for sale at the Aldi for quite a bargain (€90). 

Now the important question; is it supported in Ubuntu? And is also the scanning option supported in Ubuntu? Does anybody have experience with this or other similar printers?

Any info welcome!

---

### Post by kellemes on 2008-01-22
It seems to be.. But it's not the c4270 I see in the database, not sure if this means much.
[http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200](http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200)

Edit: You can obviously search for other printers and check if they're supported and such..
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

---

### Post by kramer65 on 2008-01-22
Ok thanks. I just (1 sec ago) got that page from HP support chat as well. I just wonder whether the scan function is also supported then?

---

### Post by Malta paul on 2008-01-22
Hi, Yes you printer will work. Check out [http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200](http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200)
Have fun if you need further Info just post:)

---

### Post by bumanie on 2008-01-22
HP are supportive of open source and supply a large number of drivers, including the one you are after.
Go to here [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
and download the self-extracting installer. If the download goes to your desktop, in terminal type cd ~/Desktop and hit enter. Then type
sudo 'sh hplip-2.7.12.run and hit enter. The installer should do everything else, you just have yo answer a few simple questions.

---

### Post by kramer65 on 2008-01-22
Hello,

Thank you. I indeed have good hopes it wil work.. ;-)

However, my question is whether the scan functionality will also work? To my understanding it doesnt say anything at [http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200](http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200) . It says a lot of technical stuff of which I cannot deduct any information about scanning facilities. Does anybody have experience with this scanning functionality or are there reports on it?

---

### Post by bumanie on 2008-01-22
I have hp f4185. I can't say for sure whether the scan function works, as I haven't used it. I can say that in the HP manager  it gives you the option of printing or scanning - the hp management screen looks the same as on windows.

---

### Post by kellemes on 2008-01-22
> **kramer65 said:**
> Hello,

Thank you. I indeed have good hopes it wil work.. ;-)

However, my question is whether the scan functionality will also work? To my understanding it doesnt say anything at [http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200](http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_C4200) . It says a lot of technical stuff of which I cannot deduct any information about scanning facilities. Does anybody have experience with this scanning functionality or are there reports on it?


This is the site of the driver you're suppose to use..  [http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)
I *think* you can safely assume the features of the 4270 are supported..

My experience with hp-printers on GNU/Linux is reasonable positive, the only issue I have with my HP PSC 1610 (using the same driver as the one you need) is the largest printing-resolution isn't supported (yet), as far as I know anyway..
But all the features do work fine, including scanning, using [xsane]("http://www.xsane.org/").

---

### Post by kramer65 on 2008-01-22
Allright! Thats what I would love to hear!

Do you have a screenshot of the scanning software?

---

### Post by bumanie on 2008-01-22
The self extracting installer (as above) will install everything you need, including the scanner. It also takes care of all dependencies. As already stated HP supports open source very well. Your printer model is mentioned on their website as being supported. The hplip installer should work for you as long as you have a reasonable internet connection so the installer can download what it needs. Give it a go, it worked fine for me during multiple installs/reinstalls.

---

### Post by kramer65 on 2008-01-22
Great! Thanks!

I am going down to the store to buy the printer in a minute, and will be back in an hour. I'll report my findings here... :-)

---

### Post by kramer65 on 2008-01-22
Hello, Back again. I just bought the printer...

I now tried to instal HPLIP via [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

But when running the file I see the following:

warning: There are 3 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)

[....]

RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes openssl libsnmp9-dev libsane-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y


Typing yes, gets me no result.

Anybody any tips? Help? Anything welcome at this point since I otherwise just spent 90Euro's for nothing...

---

### Post by kellemes on 2008-01-22
You're trying too hard ;-)
It's much simpler..
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

In gereral.. when you need packages to be installed.. first try the Ubuntu-repositories.. You can startup Synaptic (somewhere in the menu's) to find/install/remove packages.

Post back if needed.

---

### Post by bumanie on 2008-01-22
Do you have all the necessary /etc/apt/sources.lst enabled? If not enable them. Follow this [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
You could also go to synaptic and in the search function, type in the missing libraries and then mark them for installation.

---

### Post by kramer65 on 2008-01-22
Grrrrrrrrrrrrrrrrrrrrrreat!!!

With the simple help of that [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne) it is now working!

The scanner also works like a charm with that Xsane. Wow Jezus! The last hurdles before making a definite change to Ubuntu and finally wiping off Windows is coming closer!

(The only things I now still miss is a working microphone with skype/gtalk, and something like killwinamp for xmms..)

---

### Post by kellemes on 2008-01-22
> **kramer65 said:**
> Grrrrrrrrrrrrrrrrrrrrrreat!!!

Gefeliciteerd!!
(congratulations) for those not speaking Dutch. ;-)

---

