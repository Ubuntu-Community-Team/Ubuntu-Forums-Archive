---
title: "Printer Sharing"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2008-01-20
Cheers,

I just installed a FujiXerox Docuprint 203A laser printer on my xubuntu.
Had an initial problem with the driver, but I read somewhere that the Xerox P8e
worked, so I tried that and it did in fact worked.

Now my problem is that I want to share that printer with the other computers 
in my network, a laptop that has Ubuntu 7.10, and a desktop that is dual boot 
to Vista and Ubuntu 7.10.

Any ideas on how to accomplish this? thanks.

---

### Post by mikeyphi on 2008-01-20
Make a start with installing Samba
then, on xubuntu (I'm on Ubuntu so don't know if you have this) go to System/Administration/Printing and enable 'share published printers connected to this system'

Install the printer on your other systems - should be automatic under Ubuntu (might need to install that same driver), not sure about windows but I think you will need a vista driver.

---

### Post by delphiguy on 2008-01-20
Thanks, I got it working now.
Now I have another question, how do i get to monitor the status of the printer, like remaining ink and such.

---

### Post by mikeyphi on 2008-01-20
> **delphiguy said:**
> Thanks, I got it working now.
Now I have another question, how do i get to monitor the status of the printer, like remaining ink and such.

I doubt you can get access to those settings until a printer-specific linux driver is issued.
Although if you look under System/Administration/Printing - highlight your Printer and look under the printer options tab - you might find something.....assuming you have these settings in Xubuntu!!

---

### Post by delphiguy on 2008-01-20
thanks I will have a look at that.

---

### Post by BuntuFreak on 2008-01-27
I am having trouble printing to my Ubuntu printer from Vista. I got the driver installed on Vista of course. And I have shared the printer on Ubuntu and everything. Problem is how do I "add printer" on vista?

I did [http://ubuntu-box-name/printers/ubuntu-printer-name](http://ubuntu-box-name/printers/ubuntu-printer-name). But Vista has problems connecting to it.

Any suggestions?

---

### Post by halitech on 2008-01-27
> **delphiguy said:**
> Thanks, I got it working now.
Now I have another question, how do i get to monitor the status of the printer, like remaining ink and such.

if the machine is hooked up via ethernet then you can open a browser and go to the IP address of the machine and the Centerware Internet Services page should give you information about supplies and status of the machine.

---

