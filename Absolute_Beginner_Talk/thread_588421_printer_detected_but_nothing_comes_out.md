---
title: "printer detected but nothing comes out"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Pulka on 2007-10-23
Printer: Epson Stylus CX3650
Ubuntu Gutsy

lpc status:
PDF:
        printer is on device 'cups-pdf' speed -1
        queuing is enabled
        printing is enabled
        no entries
        daemon present
Stylus_CX3600:
        printer is on device 'usb' speed -1
        queuing is enabled
        printing is enabled
        no entries
        daemon present

When i send a job to print, it says processing, but it stays like this for hours. Nothing comes out

---

### Post by _oOMOo_ on 2007-10-23
Hi if you look in System>Administration>Printing, is your printer listed, and is it set as default?

cheers

EDIT: sorry I see it is on your output above.

---

### Post by Pulka on 2007-10-23
right :)

and yes, it's set as default

---

### Post by _oOMOo_ on 2007-10-23
Does the printer refuse to print from other applications? Have you tried restarting cups:

```

sudo /etc/init.d/cupsys restart

```

Might work if you only just added it, worth a try anyway! Sometimes the printer may have a problem that it can't communicate to Ubuntu; does it work ok in Windows (if you can test it)

---

### Post by Pulka on 2007-10-23
already restarted CUPS. Stays the same

Tried printing from open office, and pdf. It's the same

---

### Post by BertjeBebo on 2007-10-23
i've got the same problem since i upgraded to gutsy & reported a bug

---

### Post by Sef on 2007-10-24
Have you checked out [OpenPrinting]("http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX3650")?

---

### Post by Pulka on 2007-10-24
did everything that website says.

Now, instead of staying processing for ever, it says stopped

---

### Post by Pulka on 2007-10-30
still haven't managed to solve this. Does anyone know how to fix it?

---

### Post by Bablefish on 2007-10-30
I went through this already what you need to know is this if Epison does not have a Linux driver from your printer you are out of luck

---

### Post by philinux on 2007-10-30
**Upgrading to Gutsy** leaves the gnome-cups-manager installed. It should be removed since there is a new system printing manager. This seems to cause a conflict

Remove your printer from the system

Go to synaptic and remove the gnome-cups-manager.

Start the process again and let the system detect your printer.

---

### Post by y6FgBn)~v on 2007-10-30
I am having the same problem here with an HP 722C. The printer is detected but when trying to print a test page or from an application nothing is printed, no activity showing up at all. Connected via LPT. Any help is greatly appreciated.

Thanks in advance.

---

### Post by y6FgBn)~v on 2007-10-30
Its been awhile and still no response. Just wondering since the HPLIP seems to be having the problem with some of the older HP printers couldnt we just delete it and go back to using the old gnome-cups-manager? If so which packages would be deleted via Synaptic?

---

### Post by philinux on 2007-10-30
system-config-printer is the new print manager.

---

### Post by y6FgBn)~v on 2007-10-30
Well that didnt work either, thanks for posting the package though philinux. Oh well I guess it might be time for a new printer. My trusty ole HP has served me well, a shame its not supported any longer :sad:

---

### Post by philinux on 2007-10-30
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_722C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_722C)

[https://answers.launchpad.net/ubuntu/+question/16355](https://answers.launchpad.net/ubuntu/+question/16355)

---

### Post by y6FgBn)~v on 2007-10-30
Thank you again for those links philinux, Tried importing the ppd file with no success. Will monitor the launchpad thread to see if a solution is forthcoming. Knowing the diligent community here it shouldnt take too long :)

---

