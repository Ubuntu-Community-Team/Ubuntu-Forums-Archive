---
title: "Printers and network printers"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by makinde on 2007-07-11
ok I have a bit of a printer problem. I knew already that the PIXMA MP110 was incompatible with linux so I downloaded an emulator type software that lets ubuntu use it, it works but it has a watermark on all my print outs unless I buy it. Now it's not that much of a problem to me because I'm young and all I realy print out is my book and my homework. However my parents need to print things for work and for conferances and of cause can't give out prints with watermarks. is there a free version out there?

also how do I setup a network printer on ubuntu?

---

### Post by Espreon on 2007-07-11
Is the Printer USB compatible if so, (I assume you once used Windows), download and install Virtualbox, Goto Users and Groups and add your username to the vboxusers, log out and back in, start Virtualbox (in the System Tools Menu) and Make a new VM, then pop in a reinstallation CD and change the settings and enable USB and add your Printer and a thumbdrive or something to the USB filters. Then install Windows in the VM and use your printer within the VM, files accessed via thumbdrive.

---

### Post by makinde on 2007-07-11
slight problem there, my windows system currupted itself and it didn't come with a disk (main reason i'm on ubuntu) and I can use the printer no problem, they just want me to pay to remove the watermark and I can't do that, I just want a free version of "turbo print" (printer software i use)

---

### Post by Espreon on 2007-07-11
No I am telling you to use a reinstallation CD.

---

### Post by makinde on 2007-07-11
kk, thing is ubuntu can detect my printer and all that it's just whenever i try to print a test page it doesn't work

---

### Post by Espreon on 2007-07-11
I don't think you get it, find a tutorial on how to Install Virtualbox (I would love to but I am not at my computer but at a Winblows 2K computer). Then use the reinstallation CD to install Windows into the a VirtualBox VM.

Also you maybe choosing the wrong driver when you are setting up your printer. (Natively)

---

### Post by makinde on 2007-07-11
My computer didn't come with an install disk

---

### Post by Espreon on 2007-07-11
When you set up your printer natively how many different drivers does it give you?

---

### Post by makinde on 2007-07-11
five

---

### Post by Espreon on 2007-07-11
Try each and every one till you find the one that is the creme of the crop. Don't stop at one driver just cause it works try other drivers and see which one is the creme of the crop.

---

### Post by Sam I am on 2007-11-11
Hi all I have a Xerox DocuPrintC2100 which is not included in the Ubuntu program. I have spent many hours and tried everything to install the printer but it is virtually impossible. Can anyone help?
Sam:(

---

### Post by Whiffle on 2007-11-11
[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP110](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP110)

---

### Post by Whiffle on 2007-11-11
> **Sam I am said:**
> Hi all I have a Xerox DocuPrintC2100 which is not included in the Ubuntu program. I have spent many hours and tried everything to install the printer but it is virtually impossible. Can anyone help?
Sam:(

Have you tried these?

[http://www.fujixerox.com.au/support/downloaddriver?productId=606&operatingSystemCode=Linux](http://www.fujixerox.com.au/support/downloaddriver?productId=606&operatingSystemCode=Linux)

---

### Post by Sam I am on 2007-11-11
yes I have but Ubuntu does not seem to read it as it is not able to unpack it.. thanks anyway

---

### Post by Whiffle on 2007-11-12
you need to use the "alien" program to turn the RPM's into .deb's.

---

### Post by Sam I am on 2007-11-12
alien? where is that? sounds like star wars ....

---

### Post by Sam I am on 2007-11-13
well looks like the printer cannot be installed .. in addition I cant set up a number of other programs ...:(

---

