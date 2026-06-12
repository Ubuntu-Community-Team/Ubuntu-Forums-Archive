---
title: "Printer Problem Hp 7660"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by bob scott on 2007-07-26
Here is what happening:

the test print is not real bad.   but the 100% black is white!

open office will not print typed input.   but it prints drawn input.   it prints inserted photos with incorrect color.

on the web  the word   "UBUNTU" and the Ubuntu logo and some graphic is printed but no other alphabets.

the photo editor will print:  but,  incorrect colors.

the driver is whats recommended.
 
thanks for your help.

---

### Post by linuxwizard on 2007-07-26
What I would do is remove or uninstall the printer and than reinstall. I have this printer using it under Dapper Ubuntu/Kubuntu , Edgy Ubuntu/Kubuntu, Feisty Kubuntu/Ubuntu. It works perfect in all. Better than it worked in windows You didn't say what version you are using and how the printer is connected. Something didn't get setup right that is why I recommend removing and start over.

According to this also shows perfect
[http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7660](http://www.openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_7660)

You can look over this to make sure on setting it up
[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

When you start to setup your printer make sure you take recommended driver. Also when you come to the printer connection window it should show 2 HP 7660. You want to take the one looks like this HP _7660. Not HP 7660.

---

### Post by spur on 2007-07-26
I would try uninstall first then install HP toolbox and python.
Then navigate to /usr/lib/hplip/ and run ./toolbox It will ask you to install the printer, do so. Using this method I had only one choice and the toolbox includes everything you need to maintain/use the printer including copying from the card input opn the printer.
If icons on the main menu aren't created you can create them youself.

---

### Post by bob scott on 2007-07-26
Thanks for your reply.  I am using   Feisty  Ubuntu.   my driver is hpijs.   my  selected  printer is 
HP PHotosmart 7600 series  usb MY41A322H6PT HPLIP.

I did a reinstall and got the same results.

---

### Post by linuxwizard on 2007-07-26
Where you selected your printer did it show. 

HP PHotosmart 7600

HP PHotosmart _7600  this is the one you want see the difference

---

### Post by bob scott on 2007-07-26
Another bit of information.   on the test print yellow, magenta and blue which are the ink colors are printed correctly.  Rust,  green,  and dark blue do not vary as they should.

---

### Post by spur on 2007-07-27
I am wondering about your ink cartridges. Are you using new ones or could they be nearly empty? When mine get nearly empty I get what sounds like a similar problem. Poor quality ones could also give similar results. Just a thought,

---

### Post by bob scott on 2007-07-27
The problem is the printer.   Tests with my other computer shows  that it does not print typed information!  Thanks for the help.

---

### Post by deadgobby on 2007-07-27
All check in Synaptic if hplip and hplip-data is install. All so go into printing and click on the printer icon and check the properties and click on the driver tab. If you have more than one option, play with the options.
Gobby

---

### Post by spur on 2007-07-27
> **bob scott said:**
> The problem is the printer.   Tests with my other computer shows  that it does not print typed information!  Thanks for the help.
Bummer!!! Do you have a warranty still. I've had my 7660 for 4 years now and it is still working flawlessly.


[img]http://smileys.smileycentral.com/cat/23/23_29_107v.gif[/img]

---

