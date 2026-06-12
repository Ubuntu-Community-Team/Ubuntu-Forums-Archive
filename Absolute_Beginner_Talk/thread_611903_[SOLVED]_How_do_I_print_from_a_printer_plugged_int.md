---
title: "[SOLVED] How do I print from a printer plugged into Gutsy?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by willz06jw on 2007-11-13
Thanks for helping.

Does anyone know how to print in XP from a printer plugged into a Gutsy computer? I can't find a guide or howto anywhere about this. I have samba installed and turned on WINS...but that is as far as I can get. The XP computer can't even see the Ubuntu computer at all.

Thanks!
Will

---

### Post by jfinkels on 2007-11-13
Start here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by willz06jw on 2007-11-17
Thanks for your help,

I think the documentation you linked to was outdated.  It says to Go to the Network configuration GUI and click General tab and change the following settings:


Windows Networking
Tick Enable Windows networking
Description:       <whateveryouwant>
Domain/Workgroup:  <yourdomainorworkgroup>


When I went there, there were no Windows Networking settings like mentioned above.

Is there a way to just share my printer to windows XP computers without SAMBA using CUPS?  I noticed that the author of the doc seems to think that is possible somehow....

Thanks again for your help,
Will

---

### Post by saj0577 on 2007-11-17
Yes. i will post how in a few minute when i look at my set up on both my linux box and my xp box.

Saj

Edited: I cant get the port that is used as the printer at work is not turned on so i will post in the morning. but from memory it is

On the unix machine
systen/admin/printing
Share published printers connected to this system(tick)

then on the windows machine
control panel/printers/add printer and enter
[http://[local](http://[local) ip of computer]:[port]/printers/[name of printer]
           e.g            [http://192.168.0.2:5892/printers/Photo_Stylus_890](http://192.168.0.2:5892/printers/Photo_Stylus_890)

Sorry it is so vague as it is off memory i will post again in the morning.

Saj

---

### Post by Naipes on 2007-11-17
> **willz06jw said:**
> Thanks for helping.

Does anyone know how to print in XP from a printer plugged into a Gutsy computer? I can't find a guide or howto anywhere about this. I have samba installed and turned on WINS...but that is as far as I can get. The XP computer can't even see the Ubuntu computer at all.

Thanks!
Will

I used the information found here: 

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

First I made sure my Ubuntu box could print to my printer.  Then I set the ip address for my Ubuntu box to be static in my router.  That way the Ubuntu box always gets the same ip address.  Then I connect to my Ubuntu box from XP by running the add printer wizard.  Where it says "Specify a printer"  I select "Connect to a printer on the internet..."  (it's the last choice on the wizard)  then I type in the ip address and name of the printer connected to  my Ubuntu box.  [http://192.168.1.5:631/printers/Deskjet_970C](http://192.168.1.5:631/printers/Deskjet_970C)  

Don't forget to edit the cupsd.conf file and to restart the printer services.

Good Luck!

---

### Post by gilesb on 2008-01-15
My printer is different - HP PSC 1410, & like a lot of printers these days it doesn't come with a driver, it comes with an install program.

So when I specify the printer in XP using the URL, (as per Naipes' post) and it then asks me to 'select the manufacturer & model of your printer' I have nowhere to go.

So for me it aint solved.

There is a possible solution via 'raw' printing or print$ at [http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/) but it looks horrendous.

Has anybody got a method?

---

### Post by saj0577 on 2008-01-16
First of all have a look on the list see if their are any names of printers similar. Because their may be one that is slightly different but the driver is the same just that it has a business size paper bank or silly things like that.

Saj

---

