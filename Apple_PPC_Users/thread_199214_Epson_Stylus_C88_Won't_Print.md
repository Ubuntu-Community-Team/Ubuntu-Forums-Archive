---
title: "Epson Stylus C88 Won't Print"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by mooreted on 2006-06-18
Anyone know how to get an Epson Stylus C88 printer to print?

Printer is not detected. Using the Gnome applet for adding printers, I can add the C88 but it won't print. Print job is pending, but nothing happens.

---

### Post by mooreted on 2006-06-19
Nobody knows? Oh well, this is why I don't use Linux.

---

### Post by eobanb on 2006-06-23
All you should have to do is enable Universe and install the cupsys-driver-gimpprint package.  Basically all Epson Stylus printers are supported by the gimpprint driver.  Good luck!

---

### Post by warp99 on 2006-06-23
[QUOTE=mooreted]Nobody knows? Oh well, this is why I don't use Linux.[/QUOTE]

Can you use Google?

[http://www.freestandards.org/printing/public/]("http://www.freestandards.org/printing/public/")

---

### Post by mooreted on 2006-06-25
I have read and tried the documentation at LinuxPrinting.org. Why do people ASSume you haven't already tried everything before posting a question. I really hate answers like "Can you use Google?". My question is: can you answer questions?

---

### Post by mooreted on 2006-06-25
[QUOTE=eobanb]All you should have to do is enable Universe and install the cupsys-driver-gimpprint package.  Basically all Epson Stylus printers are supported by the gimpprint driver.  Good luck![/QUOTE]

Thanks, I will give that a try. I don't think it's a driver issue though since it's not detecting any printer.

-------------------

Nope, same problem. Thanks anyway.

---

### Post by mooreted on 2006-06-25
Here are the errors found in syslog:

Jun 25 08:18:12 mooreted-desktop no_device_found: INFO: open device failed; will
 retry in 30 seconds... 
Jun 25 08:18:42 mooreted-desktop hpiod: invalid uri:hp:/no_device_found 
Jun 25 08:18:42 mooreted-desktop no_device_found: unable to send Event hp:/no_de
vice_found 1 5012: Broken pipe 
Jun 25 08:18:42 mooreted-desktop no_device_found: INFO: open device failed; will
 retry in 30 seconds... 
Jun 25 08:19:12 mooreted-desktop hpiod: invalid uri:hp:/no_device_found 
Jun 25 08:19:12 mooreted-desktop no_device_found: unable to send Event hp:/no_de
vice_found 1 5012: Broken pipe 
Jun 25 08:19:12 mooreted-desktop no_device_found: INFO: open device failed; will
 retry in 30 seconds... 
Jun 25 08:19:42 mooreted-desktop hpiod: invalid uri:hp:/no_device_found 
Jun 25 08:19:42 mooreted-desktop no_device_found: unable to send Event hp:/no_de
vice_found 1 5012: Broken pipe 
Jun 25 08:19:42 mooreted-desktop no_device_found: INFO: open device failed; will
 retry in 30 seconds... 
Jun 25 08:20:12 mooreted-desktop hpiod: invalid uri:hp:/no_device_found 
Jun 25 08:20:12 mooreted-desktop no_device_found: unable to send Event hp:/no_de
vice_found 1 5012: Broken pipe 
Jun 25 08:20:12 mooreted-desktop no_device_found: INFO: open device failed; will
 retry in 30 seconds... 
Jun 25 08:20:42 mooreted-desktop hpiod: invalid uri:hp:/no_device_found

---

### Post by warp99 on 2006-06-25
[QUOTE=mooreted]I have read and tried the documentation at LinuxPrinting.org. Why do people ASSume you haven't already tried everything before posting a question. I really hate answers like "Can you use Google?". My question is: can you answer questions?[/QUOTE]

According to linuxprinting.org you can test the printer from the command line:

 > "This printer cannot be tested by sending plain text to it, as the printer may or may not respond to the text. The recommended way to test the connection is by checking the ink level with the escputil command as follows:

escputil -i -u -r /dev/lp0

where /dev/lp0 should be replaced with the name of your printer port."

It appears your usb port is not being detected. According to the Hardware Printer Support in the Ubuntu Wiki the USB port with the stylus series is sometimes a problem:

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters?highlight=%28printer%29]("https://wiki.ubuntu.com/HardwareSupportComponentsPrinters?highlight=%28printer%29")

I just noticed this is a duplicate thread anyway:

[http://www.ubuntuforums.org/showthread.php?t=200859]("http://www.ubuntuforums.org/showthread.php?t=200859") 

So good luck with Yellow Dog. :cool:

---

### Post by mooreted on 2006-06-26
Thank you very much for the reply. The printer test at Linuxprinting.org returns: bash: escputil: command not found. I guess I don't have that package installed.

I gave up on YellowDog almost immediately. It took 20 minutes to boot up and was slow as a dog once it got started. At least Ubuntu is blazing fast.

I will read the links you provided and see what I can do.

Thanks again.

---

### Post by mooreted on 2006-06-26
[QUOTE=mooreted]Thank you very much for the reply. The printer test at Linuxprinting.org returns: bash: escputil: command not found. I guess I don't have that package installed.

I gave up on YellowDog almost immediately. It took 20 minutes to boot up and was slow as a dog once it got started. At least Ubuntu is blazing fast.

I will read the links you provided and see what I can do.

Thanks again.[/QUOTE]

Okay, using escputil, it sees the printer just fine. It says:

 Ink color       Percent remaining
       Photo Black                      92
              Cyan                      30
           Magenta                      29
            Yellow                      26

You would think the printer would work. It is seen, it just won't print.

---

### Post by warp99 on 2006-06-26
[QUOTE=mooreted]Okay, using escputil, it sees the printer just fine. It says:

 Ink color       Percent remaining
       Photo Black                      92
              Cyan                      30
           Magenta                      29
            Yellow                      26

You would think the printer would work. It is seen, it just won't print.[/QUOTE]

Which PPD driver is loaded? Many times the driver is the same as other stylus models and they are interchangable. Here's some information on installing a C88:

[http://www.linuxprinting.org/pipermail/epson-list/2005q3/005069.html]("http://www.linuxprinting.org/pipermail/epson-list/2005q3/005069.html")

It appears that you would need the lastest version of the driver, which would be the C86 using gimp-print. :cool:

---

### Post by mooreted on 2006-06-26
I have tried changing drivers before and have read that post before. I just tried the C84 driver again, but printing still does not work. The only connection I can choose is hp://no_device_found. The Gnome Print Manager shows "no printer found".

As a note, the article says the EU tried the C84 driver because the C88 driver was not installed. My version of Gutenprint has the C88 driver.

Hmm, interesting. I get this from the Cups error_log:

E [26/Jun/2006:08:02:55 -0700] CUPS-Delete-Printer: Unauthorized
E [26/Jun/2006:08:03:35 -0700] CUPS-Add-Modify-Printer: Unauthorized
E [26/Jun/2006:08:04:11 -0700] [Job 2] No %%BoundingBox: comment in header!
E [26/Jun/2006:08:07:51 -0700] cupsdAuthorize: Local authentication certificate 
not found!

At least that is something to look up.

Thanks again.

---

### Post by mooreted on 2006-06-26
Looks like this could be Bug #45099.

---

### Post by mooreted on 2006-06-26
Tried installing TurboPrint, but that didn't work either. I give.

Thanks for the help.

---

### Post by tidris on 2006-06-26
[QUOTE=mooreted]The only connection I can choose is hp://no_device_found. 
[/QUOTE]
You definitely don't want to choose that connection for your Epson printer. That message is from the HPLIP printer driver telling CUPS it doesn't see any HP printers connected to the computer. CUPS shouldn't be displaying that error message from the HP printer driver as if it was an available connection.

---

### Post by mooreted on 2006-06-26
Yep, it is weird. That's the only option available though. I am out of ideas for now.

Thanks for the help.

---

### Post by egfrith on 2006-07-11
I've just had a similar problem with a Samsung ML-1210. 

The solution for me has been to run

```
sudo lpadmin -p ML-1210 -v parallel:/dev/lp0
```

You will have to replace ML-1210 with the name of your printer (as in the printer config GUI) and parallel:/dev/lp0 with the DeviceURI of your printer. (Look at point 9 in [http://osr600doc.sco.com/en/PR_admin/cups-start.html](http://osr600doc.sco.com/en/PR_admin/cups-start.html) for advice on what the DeviceURI might be).

Alternatively you could edit /etc/cups/printers.conf and change the line with

```
DeviceURI hp:no_device_found
```

There is a but about this, which I'm going to post to:

[https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/49366](https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/49366)

All the best,

David.

---

### Post by blocky on 2006-08-27
I don't know if you're still checking this thread, but I was having the same problem withmy new Epson Stylus C88+ and fixed it with a single command:
modprobe usblp

---

