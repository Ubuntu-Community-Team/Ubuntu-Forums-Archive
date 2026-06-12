---
title: "Installing Brother 5840 Printer?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by nobbynolsn on 2006-05-12
I'm trying to install linux driver to install a Brother 5840 network printer. There doesn't seem to drivers for ubuntu at [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html). Anyway, I have tried downloading the other drivers but the files wont open in "Archive Manager".

Does anyone know what the best way to precede is?

I'm a new user but really want to get printing going before I delve into linux proper. Help would be very appreciated.

---

### Post by mostwanted on 2006-05-12
Looking at the list of drivers in Ubuntu (System &#8594; Administration &#8594; Printing), I see several drivers for other 5xxx models; maybe one of those will work? My printer (canon s750) doesn't have Linux drivers either, but I can manage to print in black and white using a similar driver.

---

### Post by gashcrumb on 2006-05-12
I think you want to go here: [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")

and get the one under the "Drivers for Debian" section (a little more than halfway down the page).  I don't have the printer you have, however, I figured I'd try and install this anyway.  I had to do:

sudo apt-get install csh

and then (assuming you're in the directory where the .deb file you downloaded is) run:

sudo dpkg --install ./cupswrappermfc5840cn_1.0.0-1_i386.deb

I got this for output from the above:

```

(Reading database ... 194073 files and directories currently installed.)
Preparing to replace cupswrappermfc5840cn 1.0.0-1 (using .../cupswrappermfc5840cn_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.
/etc/init.d/cups: Command not found.
Unpacking replacement cupswrappermfc5840cn ...
Setting up cupswrappermfc5840cn (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC5840CN
/etc/init.d/cups: Command not found.

```

However, if you go to System -> Administration -> Printing and double-click the "New Printer" icon, pick whatever method you're connecting the printer to your computer with and then get to the driver selection part you'll see MFC-5840CN in the list under "Brother".  Hope that helps!

---

### Post by nobbynolsn on 2006-05-13
[QUOTE=gashcrumb]However, if you go to System -> Administration -> Printing and double-click the "New Printer" icon, pick whatever method you're connecting the printer to your computer with and then get to the driver selection part you'll see MFC-5840CN in the list under "Brother".  Hope that helps![/QUOTE]Thanks for your help. I am still unable to install using this method, however. I can select "Network Printer" but the list remains empty and there appears to be no way of selecting the printers. 

I shall try and look at again later. Any additional advice would be appreciated.

---

### Post by gashcrumb on 2006-05-18
Does the printer have a print server or anything like that built in?  In that case you'd probably need to use samba to connect to it.  I've only dealt with HP printers and just use an HP JetDirect card in my printer here at home and some printers at work.

Maybe it'd be worth trying to hook up the printer via USB or parallel port first and see if you can get it configured that way and then try setting it up as a network printer afterwards?  At least then you'll have a working printer...

---

### Post by kaoskorruption on 2008-04-15
Hey, I'm also trying to configure my MFC-5840CN

> However, if you go to System -> Administration -> Printing and double-click the "New Printer" icon, pick whatever method you're connecting the printer to your computer with and then get to the driver selection part you'll see MFC-5840CN in the list under "Brother". Hope that helps!

I install the printer drivers just fine, but when I go to the driver list there is no MFC-5840CN under Brother. Now what?

---

