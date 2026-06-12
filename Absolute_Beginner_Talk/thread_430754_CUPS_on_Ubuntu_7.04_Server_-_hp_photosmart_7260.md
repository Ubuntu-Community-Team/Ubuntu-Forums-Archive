---
title: "CUPS on Ubuntu 7.04 Server - hp photosmart 7260"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by bewire on 2007-05-02
Hi, I have installed Ubuntu 7.04 server with CUPS/SAMBA but I can't get my HP Photosmart 7260 to work correctly. I have tried to install different drivers both through the CUPS WEB GUI from another machine with XP and through HPLIP setup from the server console.

1. I downloaded HP-PhotoSmart_7260-hpijs.ppd from linuxprinting.org, but when I try to use it I get an error message "... foomatic-rip failed" and the print job is stopped. What does the foomatic-rip error message mean ?

2.None of the preshipped drivers that are listed in CUPS or suggested by HLIP setup match my printer, and the ones I've tried don't print right. (The test page only print the color circle in the top left and the black borders, no text.)

Any suggestions to how I can pursue my quest for the optimal driver ?

Just for the record: My printer worked fine with my Ubuntu 6.06 LTS Desktop rigth out of the box.

---

### Post by dannyboy79 on 2007-05-02
based on what you're saying, i would use whatever driver you used in dapper.

---

### Post by Seisen on 2007-05-02
Try using the driver from here and see if it works.

[http://hplip.sourceforge.net/downloads.html]("http://hplip.sourceforge.net/downloads.html")

---

### Post by sonnynv on 2007-05-02
I am not using Ubuntu yet, but when I use Stamps com on 
Windows, it wouldn't work and I contacted them and they
said that sometimes you have to fool the printer, so for 
Stamps com we installed the HP Desktop 600 (Monochrome)
drivers. I have an all-iin-one HP 2570 that works for 
everything else.

---

### Post by bewire on 2007-05-02
> **dannyboy79 said:**
> based on what you're saying, i would use whatever driver you used in dapper.

Yes, that might work, but then I have to reinstall dapper  :-)

---

### Post by bewire on 2007-05-02
> **Seisen said:**
> Try using the driver from here and see if it works.

[http://hplip.sourceforge.net/downloads.html]("http://hplip.sourceforge.net/downloads.html")

Hi, I installed the HPLIP package with apt-get. Shouldn't that do the job ?

---

### Post by Seisen on 2007-05-02
You can try it and see if it works if not its back to the drawing board.

---

### Post by dannyboy79 on 2007-05-02
> **bewire said:**
> Hi, I installed the HPLIP package with apt-get. Shouldn't that do the job ?

sudo aptitude show HPLIP

will show you what version is in the repo's. I am guessing that the HPLIP he linked to is newer. DId you even bother to read the changelog or similar within the link he posted? I would use hte link he posted UNLESS you're saying that the above command is resulting in the same version that's within the link he posted.

---

### Post by bewire on 2007-05-02
> **dannyboy79 said:**
> sudo aptitude show HPLIP

will show you what version is in the repo's. I am guessing that the HPLIP he linked to is newer. DId you even bother to read the changelog or similar within the link he posted? I would use hte link he posted UNLESS you're saying that the above command is resulting in the same version that's within the link he posted.


I'm trying the automatic installer, but it hangs:

Running 'sudo apt-get install --yes --force-yes build-essential libjpeg62-dev bu                               ild-essential build-essential python2.5-dev libcupsys2-dev libusb-dev lsb openss                               l libsnmp9-dev python-qt3 python-reportlab sane sane-utils xsane'
Please wait, this may take several minutes...        

I should maybe try the manual install ?

---

### Post by dannyboy79 on 2007-05-03
> **bewire said:**
> I'm trying the automatic installer, but it hangs:

Running 'sudo apt-get install --yes --force-yes build-essential libjpeg62-dev bu                               ild-essential build-essential python2.5-dev libcupsys2-dev libusb-dev lsb openss                               l libsnmp9-dev python-qt3 python-reportlab sane sane-utils xsane'
Please wait, this may take several minutes...        

I should maybe try the manual install ?

i'll ask that you see my above comments and post back about that prior to going forward. also, I don't understand what your saying about an automatic installer? are you saying that you did download the HPLIP package that the above linked to? and if so, you're trying to install that? if the installer fails, and you're seeing what is failing, try to install each package seperately OR try whatever this manual method is that you're referring to.

---

### Post by bewire on 2007-05-03
> **dannyboy79 said:**
> i'll ask that you see my above comments and post back about that prior to going forward. also, I don't understand what your saying about an automatic installer? are you saying that you did download the HPLIP package that the above linked to? and if so, you're trying to install that? if the installer fails, and you're seeing what is failing, try to install each package seperately OR try whatever this manual method is that you're referring to.


Hi and thanks for your effort ! I will look into the documentation and follow your advice.

I'll post and update if I make any progress :-)

---

### Post by bewire on 2007-05-05
Hi all, I may have fixed my problems, but I'm not sure what worked ...

Update: Only the testpage worked. If I try to send a file to the printer with lp - printername filename I only got blank pages. However, installing hpijs looks like fixing everything, look in my reply below. 


The last thing I did was to run the following commands from the console:

foomatic-gswrapper
ln -s /usr/bin/foomatic-rip /usr/lib/cups/filter/
sudo chmod 777 /usr/share/cups/model/HP-PhotoSmart_7260-hpijs.ppd

Then I installed the printer with the CUPS GUI and selected the "HP PhotoSmart P100 Foomatic/cdj1600"

The test page prints as shown in the manual (the last picture):
[https://192.168.0.102:631/help/overview.html?TOPIC=Getting+Started&QUERY=](https://192.168.0.102:631/help/overview.html?TOPIC=Getting+Started&QUERY=)

Only thing for now is the print margins. There are some white space in all directions (most for top and bottom margins).

I will study the documentation and try to tune my setup further. 

For now this doc has been most useful for me:
[http://www.linuxprinting.org/~till/printing-tutorial/tut.html](http://www.linuxprinting.org/~till/printing-tutorial/tut.html)

I will try to figure out the HPLIP install when I get a better understanding of the basic configuration. 

WinXP (off topic I guess ...)

Another story is how to obtain a driver for Windows XP. When I try to add the printer in XP I can't get an function driver (see attached picture). I don't have the install CD from HP anymore, and the software on HPs site don't seem to help when installing a network printer:
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=no&dlc=no&product=305337&lang=no](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=no&dlc=no&product=305337&lang=no)
There are no Photosmart printers in the list. I have tried other models but they doesn't print right (overlapping text, etc.)

I've started to study this documentation for setting up the XP client:
[http://www.cups.org/documentation.php/man-cupsaddsmb.html](http://www.cups.org/documentation.php/man-cupsaddsmb.html)

I made printing from XP working with cups6.inf and cups6.ppd. But I only get Black & White printing.

I will try to get hold of HPs inf and ppd file for this printer if i exists. Anyone who knows ?

---

### Post by bewire on 2007-05-06
Hi again, I installed foomatic-hpijs, and now everything looks fine ! :-)

-CUPS GUI found and installed my printer driver
-The testpage prints
-I sent a pdf file to the printer with lp -d HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP  kobling.pdf and it worked ...

I used apt-get install foomatic-hpijs to install hpijs.

I'm not sure if I have HPLIP installed, and if so, how it works with hpijs. I did try to follow the instructions in the link you provided, and read the install notes, relase notes, etc. It looks like a have some issues related to dependencies. In CUPS GUI however it looks like HPLIP is present, hence the device name HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP (?)

I will study linuxprinting further to understand the details, and tweak my printer setup, but for now I'm glad to actually print something.

Any comments or advice to speed up my learning curve are welcome.

Thanks !

---

### Post by bewire on 2007-05-08
Hello, I have now a server setup with samba. I use the cups6.inf and cups6.ppd file for my printer. It gives only black and white though. So I tried to follow the instructions for cupsaddsmb:
[http://www.cups.org/documentation.php/man-cupsaddsmb.html](http://www.cups.org/documentation.php/man-cupsaddsmb.html)

Right now I'm struggling with the drivers. I copied the required files to /usr/share/cups/drivers and ran cupsaddsmb. Windows first detected the network printer, but when I installed it I got a message about no applicable driver for my printer (I don't remember the actual message). Right now Windows doesn't detect the network printer, but I can install it with [http://192.168.0.102:631/printers/HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP](http://192.168.0.102:631/printers/HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP). I may have messed up the driver files after copying them a second time to /usr/share/cups/drivers, so I will try again. 

Question: Why does the cups6.inf/ppd only print black and white ?
Question: Is there a way that I can add a driver for my printer to the cupsaddsmb export ?

---

### Post by dannyboy79 on 2007-05-09
ok, well I think we are off track here. we need to get back to the basics before we end up with a bunch of garbage on your machine. According to here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7260](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7260)

your printer is supported by both hpijs and for more advanced printing functions, hplip. I think it's possible that since you installed hplip using apt-get, that may have done something more than it needed to? I can't say for sure. WHat I can tell you is my experience with my HP d135. I simply use the gnome printer interface to add my printer and it suggested I use the hplip driver, I said ok and it worked flawlessly. now this is a network attached printer that is hooked up to my win xp box, so I simply told win xp to share the printer and during the printer setup within ubuntu, I just chose a network printer versus usb attached printer. Like I said, once I chose the printer Officejet d135, it just suggested hplip on it's own and did it's thing in the background. I didn't use apt-get or anything other than the printer gui located within system, admin, I believe that's where it was. I am not at home so not completely sure.

So you stated that you couldn't find the exact name of your printer within the gnome printer setup gui? is that true??? also, you stated that originally it wasn't printing correctly, can you be more specific? and what drivers were you using which resulted in this not printing correctly and how did you install them? This link here can help you align prints to the page if that's what was wrong: 

[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

so what I suggest is trying to start from scratch if you can, undo everything you did so that you can start from a clean slate and we can go from there. also, you're hooking the printer directly to ubuntu or is it attached to windows? you might want to maybe hook it to windows as that's the way I have mine set and liek I said, setting up mine thru network printing using the gnome printing gui was a piece of pie.

I unfortunately can't help otherwise if you want to continue down the path you're going as I wouldn't know what to suggest.



OR

I even found this from back in 2005: ([http://ubuntuforums.org/archive/index.php/t-12162.html](http://ubuntuforums.org/archive/index.php/t-12162.html))

I have managed to get this printer working using packages from ubuntu and universe, there should be no need to compile anything at all ... trick is that this printer does not work with kernel printer module. It needs hpoj driver.
here is how i've done it:

1) apt-get install hpoj
postintstall script will find your printer
2) /etc/init.d/cupsys restart
3) Now go to computer -> sys conf -> printing -> add new printer
choose 'ht photosmart 7200 series' not the other one
next steps are easy ...

hope it helped, good luck

---

### Post by bewire on 2007-05-09
> **dannyboy79 said:**
> ok, well I think we are off track here. we need to get back to the basics before we end up with a bunch of garbage on your machine. According to here: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7260](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7260)

your printer is supported by both hpijs and for more advanced printing functions, hplip. I think it's possible that since you installed hplip using apt-get, that may have done something more than it needed to? I can't say for sure. WHat I can tell you is my experience with my HP d135. I simply use the gnome printer interface to add my printer and it suggested I use the hplip driver, I said ok and it worked flawlessly. now this is a network attached printer that is hooked up to my win xp box, so I simply told win xp to share the printer and during the printer setup within ubuntu, I just chose a network printer versus usb attached printer. Like I said, once I chose the printer Officejet d135, it just suggested hplip on it's own and did it's thing in the background. I didn't use apt-get or anything other than the printer gui located within system, admin, I believe that's where it was. I am not at home so not completely sure.

So you stated that you couldn't find the exact name of your printer within the gnome printer setup gui? is that true??? also, you stated that originally it wasn't printing correctly, can you be more specific? and what drivers were you using which resulted in this not printing correctly and how did you install them? This link here can help you align prints to the page if that's what was wrong: 

[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

so what I suggest is trying to start from scratch if you can, undo everything you did so that you can start from a clean slate and we can go from there. also, you're hooking the printer directly to ubuntu or is it attached to windows? you might want to maybe hook it to windows as that's the way I have mine set and liek I said, setting up mine thru network printing using the gnome printing gui was a piece of pie.

I unfortunately can't help otherwise if you want to continue down the path you're going as I wouldn't know what to suggest.



OR

I even found this from back in 2005: ([http://ubuntuforums.org/archive/index.php/t-12162.html](http://ubuntuforums.org/archive/index.php/t-12162.html))

I have managed to get this printer working using packages from ubuntu and universe, there should be no need to compile anything at all ... trick is that this printer does not work with kernel printer module. It needs hpoj driver.
here is how i've done it:

1) apt-get install hpoj
postintstall script will find your printer
2) /etc/init.d/cupsys restart
3) Now go to computer -> sys conf -> printing -> add new printer
choose 'ht photosmart 7200 series' not the other one
next steps are easy ...

hope it helped, good luck

Thanks ! I'll will try to start from scratch. Actually I'm tempted to reinstall the ubuntu server since I haven't any critical data or services running yet.

---

### Post by dannyboy79 on 2007-05-09
> **bewire said:**
> Thanks ! I'll will try to start from scratch. Actually I'm tempted to reinstall the ubuntu server since I haven't any critical data or services running yet.

reformatting and reinstalling  would most likely be your best bet, no worrys about stuff getting mixed up. also, you didn't answer my questions.

---

### Post by bewire on 2007-05-09
> **dannyboy79 said:**
> reformatting and reinstalling  would most likely be your best bet, no worrys about stuff getting mixed up. also, you didn't answer my questions.

Here are some answers to your questions:

1. Yes, apt-get may have done something more than needed.
2. The printer is attached to my ubuntu server box, not XP. It works well from the Ubuntu command line, ie lp -d HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP kobling.pdf.
3. It's within XP I can't find a driver when I try to add a network printer (add new printer). After running cupsaddsmb -a I expected the driver to be provided by cups from the Ubuntu Machine. I tried to follow the steps described here: [http://www.cups.org/documentation.php/man-cupsaddsmb.html](http://www.cups.org/documentation.php/man-cupsaddsmb.html)

4.I found a workround using the CUPS6.PPD and and CUPS6.INF from CUPS v6 PostScript printer driver for Windows. when installing the printer in XP. I entered the printername [http://192.168.0.102:631/printers/HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP](http://192.168.0.102:631/printers/HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP) and provided CUPS6.PPD and and CUPS6.INF when the XP dialog prompted for a driver. The only problem is that the driver doesn't support color so I only get Black and White prints.

---

### Post by dannyboy79 on 2007-05-09
> **bewire said:**
> Here are some answers to your questions:

1. Yes, apt-get may have done something more than needed.
2. The printer is attached to my ubuntu server box, not XP. It works well from the Ubuntu command line, ie lp -d HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP kobling.pdf.
3. It's within XP I can't find a driver when I try to add a network printer (add new printer). After running cupsaddsmb -a I expected the driver to be provided by cups from the Ubuntu Machine. I tried to follow the steps described here: [http://www.cups.org/documentation.php/man-cupsaddsmb.html](http://www.cups.org/documentation.php/man-cupsaddsmb.html)

4.I found a workround using the CUPS6.PPD and and CUPS6.INF from CUPS v6 PostScript printer driver for Windows. when installing the printer in XP. I entered the printername [http://192.168.0.102:631/printers/HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP](http://192.168.0.102:631/printers/HP_photosmart_7200_series_USB_CN3782C262E0_HPLIP) and provided CUPS6.PPD and and CUPS6.INF when the XP dialog prompted for a driver. The only problem is that the driver doesn't support color so I only get Black and White prints.


well because of the color printing issue it sounds like you'd be better off hooking it to xp and then sharing it to ubuntu like I do but I can only suggest it as it's your setup. sounds like you got it under control from here on out.

---

### Post by bewire on 2007-05-10
> **dannyboy79 said:**
> well because of the color printing issue it sounds like you'd be better off hooking it to xp and then sharing it to ubuntu like I do but I can only suggest it as it's your setup. sounds like you got it under control from here on out.


It works !

1. I installed the printer locally on the XP machine with the driver software from HPs homepage
2. I attached the printer back to the ubuntu server
3. I installed the network printer on my XP machine and used the driver I just installed

(Actually I just changed the driver I had installed in properties>advanced>driver, see screenshot)


Not sure if this is the right way, but now my prints get colors :-)

Thanks for all help !

---

### Post by dannyboy79 on 2007-05-10
hah!!!! brilliant. I didn't suggest that but that's just awesome. I was just suggesting to leave it hooked to winxp and use the hplip drivers as a network printer but this sounds even better the way you resolved this issue. great job.

---

