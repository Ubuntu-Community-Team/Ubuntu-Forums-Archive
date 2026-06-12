---
title: "having problems samsung ML-2010 printer"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by absolutetom on 2007-06-12
please help I have been using ubuntu for a while but have never been able to get my printer working.  Today I attempted again with the same result, I went to samsung website and downloaded driver, I open it with cdroot/autorun and it walks me through setting up printer. When complete it says it was successful I have a Samsung Unified Driver Configurator on the desktop it has a test button that when clicked opens a window that says local printer ml2010 (Samsung ML-2010 Series (SPL ll)) on mfp:/dev/mfp/4.  Then steps check printer, test device and backend, and print test page. When I click start it shows everything as ok and it appears that is going to print the page which the test results say Printing test page ok but the printer never prints. The icon at the top of the screen shows the printer is stopped when I attempt to  restart it it never does. Also on the configurator is a tab that says classes when I click on it there are no classes there. I'm not even sure what a class is I tried to go to cups site to see if I could figure out anything; tried a couple of the post there and no luck.  Now I have a dual boot system and when I tried to boot in to XP Pro it just keep going back to the boot screen.

I sure would appreicate any help

---

### Post by Skrynesaver on 2007-06-12
This guy claims to have got it working without the supplied driver [http://ubuntuforums.org/showthread.php?t=65111](http://ubuntuforums.org/showthread.php?t=65111)

---

### Post by flowheat on 2007-06-12
I have the ML-2010 and it works perfectly following the instructions in the link above.   Don't bother using the Samsung driver.

PS - It is an excellent printer.

---

### Post by philbert on 2007-06-16
The ml-2010 works fine with Fiesty Out of the Box without the unified driver. 
However, It is not working with Gutsy - Tribe 1 ( from the live cd).  
Fiesty is using Kernel 2.6.20 and Gutsy is using 2.6.22, nor with Fedora 7 with kernel 2.6.21.

---

### Post by vivabenfica on 2007-07-18
I spent half a day getting this printer to work (Samsung ML 2010) under Xubuntu 7.04.

DO NOT run samsung website's unified driver. It gives a great GUI, ... but would not work for me. If you do install it, remove it, as no other method worked until I removed it. To do so navigate within the cdroot folder it creates, and within Linux/i386 there is a uninstall.sh script. Run it as sudo to remove all samsung universal driver evilness before you proceed with other methods.

I tried using CUPS via browser interface ([http://localhost:631](http://localhost:631))  and it didn't work, but granted I didn't try it after uninstalling samsung junk. I tried various drivers ML-200, ML-2010, ML-4500, ...

Also tried Applications|Settings|Printing (I think this is gnome cups interface?) and it didn't work, but again, as above, not after removing samsung junk.

ONLY THING THAT WORKED ---
1. removed samsung junk as above
2. restarted computer in Xubuntu with printer off
3. used Applications|System|Printer, which autodetected printer on usb port. I chose ML-4500 gdi as driver -- works like a charm from evince, firefox, openoffice, but mousepad won't print? This was a small problem that I "fixed" by installing gedit which is nicer anyway, and punishing mousepad for being a pain in the a$$ by uninstalling it. I like pettiness some times. :) gedit rewarded me by printing fine.

This is the relevant section from my /etc/cups/printer.conf file
<Printer ML-4500>
Info 
Location 
DeviceURI usb://Samsung/ML-2010
State Idle
StateTime 1184797772
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

This is actually a great printer. The driver stuff on Samsung is obsolete I think and won't work in modern linux distros. If I had trusted Ubuntu itself I would have saved many hours of frustration. There's a moral in here somewhere!

---

### Post by icheyne on 2008-01-13
> **vivabenfica said:**
> 
DO NOT run samsung website's unified driver. It gives a great GUI, ... but would not work for me. If you do install it, remove it, as no other method worked until I removed it. To do so navigate within the cdroot folder it creates, and within Linux/i386 there is a uninstall.sh script. Run it as sudo to remove all samsung universal driver evilness before you proceed with other methods.


sudo /usr/share/applications/linux-uninstall

---

### Post by icheyne on 2008-01-13
I spent ages trying to get this printer to work, but in the end my problem was just that I had not pushed the toner cartridge in far enough. You will know it has engaged, because the "On Line" light turns green.
It was detected and works fine using the regular Ubuntu Gutsy Add Printer dialog box.

---

