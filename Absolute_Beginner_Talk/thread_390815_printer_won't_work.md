---
title: "printer won't work"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by easher on 2007-03-22
I booted up Ubuntu 6.10 from the cd to see how it would work.
The problem I have is my all in one printer Lexmark x3350 will not print. I don't know how to install drivers for it to work with Ubuntu.
Please Help!!!!!:confused:

---

### Post by Jussi01 on 2007-03-22
Hei, it doesnt look like your printer is supported in ubuntu... Im sorry.

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-X3350](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X3350)

---

### Post by RealG187 on 2007-04-13
I too have the x3350, so I can't use it [actaully have 2]? Would using wine on the install CD work for us?

---

### Post by igknighted on 2007-04-13
I do not believe so.  You MIGHT be able to run a virtual windows and transfer documents to the virtual machine and print from there, but even then I'm not sure.  Printers are so cheap it might be best just to grab a cheap HP (they have great linux support).

---

### Post by Austin_KW on 2007-04-14
If you have a home network with linux and windows, the best thing to do is leave this printer attached to an old windows PC. Install ghostscript and Redmon port redirection on the windows PC and print over the network from your linux machine to the printer using a postscript driver.

[edit] I dont know if this would work if you installed the windows PC in a virtual machine on linux, I suppose it might?

---

### Post by igknighted on 2007-04-14
> **Austin_KW said:**
> If you have a home network with linux and windows, the best thing to do is leave this printer attached to an old windows PC. Install ghostscript and Redmon port redirection on the windows PC and print over the network from your linux machine to the printer using a postscript driver.

[edit] I dont know if this would work if you installed the windows PC in a virtual machine on linux, I suppose it might?

Assuming the unrecognized device would go straight through to the virtual USB port as is, you would still need to transfer anything you wanted to print to "virtual windows" via Samba or ftp or something else, so it would be no walk in the park.  From a technical standpoint I would worry that the VM would only get told what linux thinks is there, and if it cannot recognize the printer, it might just tell the windows VM that there is an unknown device there, or it could tunnel the USB drive to the client (in this case windows) and the device could work... I don't have a windows VM, but if someone does and wants to try, I would love to know if this works.

---

### Post by RealG187 on 2007-04-14
I heard of ghost script, is that the weird promt this for *.gs files?

---

### Post by Austin_KW on 2007-04-14
ghostscript is a free software that allow you to render (view, print..)  postscript (printer) files.

So, in linux we could print to a postscript file, transfer the postscript file to a windows PC, run ghostscript to view the postscript file, print from ghostscript to the lexmark printer using the windows driver.

Except of course we dont actually do that as it is all automated.  So on linux when I print, I just select my 'lexmark postscript network printer' and it pops out on the lexmark attached to the windows PC.

Now to do this you need a windows PC to connect the lexmark, what I have not tried is doing it when the 'windows PC' is a virtual PC or wine running on linux. I think that a virtual pc might work and that wine would not work.

---

### Post by RealG187 on 2007-04-16
Why don't I just transfer the file as it is then? Like no use converting a JPG or Word file when I can just send those...

---

### Post by Terl on 2007-04-16
I am stuck with a printer that won't work under Linux also.  I just went ahead and kept a small windows partition and drop the files to be printed on that and print them from Windows when I have to.  When the printer breaks I will just get one that works with Linux.  I don't print all that much so it doesn't matter to me.

---

### Post by Austin_KW on 2007-04-16
> Why don't I just transfer the file as it is then? Like no use converting a JPG or Word file when I can just send those...Well of course you could, but you would have to login to the windows PC, open the file, print it and then delete the temproary copy. Also you would need an equivalent program on the windows PC for everything you need to print. Using gs/redmon, it is a lot more convient to just select print on the linux box as I have a windows PC running on my network.

---

### Post by RealG187 on 2007-04-17
I can run JPGs on Windows anyways...

Maybe between word and open office there might be issues...

---

### Post by ubu-for on 2007-05-01
> **easher said:**
> I booted up Ubuntu 6.10 from the cd to see how it would work.
The problem I have is my all in one printer Lexmark x3350 will not print. I don't know how to install drivers for it to work with Ubuntu.

Maybe you have [this problem](http://ubuntuforums.org/showthread.php?t=413002), too?

---

### Post by Gram1982 on 2007-07-23
> **igknighted said:**
> I do not believe so.  You MIGHT be able to run a virtual windows and transfer documents to the virtual machine and print from there, but even then I'm not sure.  Printers are so cheap it might be best just to grab a cheap HP (they have great linux support).

I was able to get my Lexmark X3350 working in a Windows XP virtual machine, using VMware 6, by just simply connecting it and installing the drivers from Lexmark!  I'm running Debian Etch.

Test page printed perfectly :)

[IMG]http://img511.imageshack.us/img511/6673/snapshot6bj4.jpg[/IMG]

For the sake of showing the functionality I took the paper out of the tray.

---

