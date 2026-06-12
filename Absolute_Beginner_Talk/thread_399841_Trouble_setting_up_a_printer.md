---
title: "Trouble setting up a printer"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by dr_dirk on 2007-04-02
Hello.  I thought I had set up my printer correctly the first time, but when I tried to print, nothing happened.  I checked the "jobs" for the printer and there was a print job in progress, but no printing was actually taking place.  I tried reconfiguring the printer a couple times to be sure I hadn't done something silly, but I still haven't been successful, even after following some pretty specific instructions in another thread. ([http://www.ubuntuforums.org/newreply.php?do=newreply&p=1896329](http://www.ubuntuforums.org/newreply.php?do=newreply&p=1896329))

It is an HP Laserjet 1020 connected by USB and I have the correct driver, so far as I can tell, but something is still not right.  I'm suspicious about something on the first page of the printer setup.  It gives the option of "Use a detected printer:" or "Use another printer by specifying a port:".  Under detected printer it says that no printers are detected and the port specification option doesn't wholly make sense to me.  In the drop-down menu it gives the options "hp no_device_found", "LPT #1", "Parallel Port #1 (CANON)", and "Parallel Port #1 (EPSON).  I'm using USB so I haven't tried either parallel port (also I'm confused why they would be labeled Epson and Canon), but choosing either LPT#1 or hp no_device_found have solved the problem.

On step 3 of the printer setup there is space to fill in the name, description and location of the printer.  I left the name as Laserjet-1020, the description and the location blank.  The location may be the problem, I suspect, but I have been unable to  locate where the printer lives in the dev folder.  Is that the wrong place to look and/or is the location a necessary part of the installation?

That's all the information I can find that seems relevant.  The printer claims to be ready and doesn't give any messages when I ask it to print...  I just says printing and then doesn't print.  Thank you for any help you can give.

Derek

---

### Post by drs305 on 2007-04-02
You didn't make any reference to a network printer. Will it be used on a network? I have almost the same setup but I have it connected via a network and installed it using cups instead of the foo2jzs... files.

If you go to Applications, System, Adminstration, Device Manager, do you have a USB entry listing the HP printer? You can also use the terminal and type lsusb to see if the printer is connected and talking to the computer. My readout using lsusb is:

Bus 001 Device 007: ID 03f0:0517 Hewlett-Packard LaserJet 1000

---

### Post by dr_dirk on 2007-04-02
I didn't see the printer under device manager and the lsusb readout looks like so:
Bus 005 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046a:0048 Cherry GmbH 
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 

I'm guessing that Cherry GmbH is my keyboard because that's the only other usb device I have plugged in aside from the mouse and printer.  To answer your other question, no, it is not a network printer although I would like to set it up to share once it is working.

How do you use cups instead of foo2zjs?  foo2zjs was the default and only driver option available for the hp 1020 when setting it up.

---

### Post by drs305 on 2007-04-02
I am a linux newbie and don't want to send a lot of people down the wrong path. I have sent you a PM with my email address. If we get it working then we can post how we did it. There is probably an easier way and hopefully someone here can help you out.

---

### Post by ramjet_1953 on 2007-04-02
Hi, there! 

This link may help you, as apparently there is a small issue with this particular printer, which is unusual for HP printers, as they are normally no problem at all.

[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)

Regards,
Roger :cool:

---

### Post by dr_dirk on 2007-04-02
I tried the link you sent ramjet_1953 but it doesn't seem to help in part because I'm not entirely sure what I'm looking at.  I did try the one instruction at the very top:

[The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1020.dl >  /dev/usb/lp0".]

I don't know how to work the hotplug/udev script so I tried the manual instructions.  However, I do not have a directory/file /dev/usb/lp0.  lp0 lives simply under /dev so I changed it to ```
cat /usr/share/foo2zjs/firmware/sihp1020.dl >  /dev/lp0
```

When I tried running that in the terminal it just seemed to hang up.  That is to say, there was no output after waiting a little bit.

---

### Post by dr_dirk on 2007-04-03
I followed instructions here 

[http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/](http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/)

but still had no luck.  When I enter ```
lsusb
``` the printer still does not show up.  It seems that what I need to know is how to get my computer to recognize that the printer is plugged in.  I hope that this is the only thing that needs to be dealt with as it would seem that the rest of the installation should be taken care of.  Any ideas?

---

### Post by dr_dirk on 2007-04-03
This is a bump and a restatement of the question I have now.

How can I get my Ubuntu to recognize there is a device when I plug my printer in?

---

### Post by Dirkomatic on 2007-04-03
Have you seen this thread?

[http://www.ubuntuforums.org/showthread.php?t=220766&highlight=foo2zjs+1020](http://www.ubuntuforums.org/showthread.php?t=220766&highlight=foo2zjs+1020)

---

### Post by dr_dirk on 2007-04-03
> **Dirkomatic said:**
> Have you seen this thread?

[http://www.ubuntuforums.org/showthread.php?t=220766&highlight=foo2zjs+1020](http://www.ubuntuforums.org/showthread.php?t=220766&highlight=foo2zjs+1020)

Yes, I have done most everything in that link.  After doing all of that the printer still isn't detected.  One thing I don't know about is what port I should use in this section ```
# Set $DEV to, e.g. /dev/usb/lp0, to force the device you want
    # Else, leave it null to automatically detect the device
    #
    DEV=/dev/usb/lp0
    #DEV= ""
```

lp0 would be a specific USB port, right?  So would I have to plug the printer into the port specified (or specify the port the printer is plugged into)?  If so, how can I find out which port is which other than trial and error?

---

### Post by dr_dirk on 2007-04-03
The link you sent me, dirkomatic, seems to have solved the problem.  I had followed directions like that beforehand, but this time it seems to have done the trick.  Thanks everyone for the input.

Derek

---

