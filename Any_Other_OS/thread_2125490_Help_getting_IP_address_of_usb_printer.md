---
title: "Help getting IP address of usb printer"
date: 2013-03-14
forum: Any Other OS
---

### Post by CaptainMark on 2013-03-14
I'm trying to get a Ricoh printer working on the work computer which is running an old version of Red Hat and has no internet access, I downloaded a script from the Ricoh website and ran it on the work office pc but the script needs the printers IP address or hostname, its attached via USB so does it still have an IP, if so how do find it, I ran lpstat -s and got a device name usb:/dev/usb/lp0 but the script isn't accepting this as valid input, can anyone help me as I've not got much experience with printers (not having one at home)

Regards
Mark

---

### Post by varunendra on 2013-03-14
*Thread moved to **Hardware**.*
-------------------------

USB doesn't use TCP/IP, so it does not have an IP address. Maybe we can help if you post the script itself?
Also post the full and exact model no. of the printer.

---

### Post by CaptainMark on 2013-03-14
[Heres a link to where I found the script]("http://support.ricoh.com/seresBB/servlet/VSORPageServlet?OBJPATH=bb/pub_e/dr_ut_e/0001231/0001231130/V300/r58117en.tar&EURA=bb/html/dr_ut_e/re/resource/eula_unixfilter.txt&VSORSELFWID=WRU001&VSORSELNWID="), its from the Ricoh website, the printer is a Ricoh Aficio SP 4310n, I can network the printer via ethernet if that's easier but I've never done that before either. I can't really use the provided .rpm's because the essential software on the computer requires such specific libraries I can't risk messing it up.

---

### Post by varunendra on 2013-03-14
Well, I didn't 'accept' the EULA ;)

..but it says the following in 'Requirements' -
> **System Requirements**
[list]
[*]**TCP/IP Network**
[*]Supported UNIX platform
[*]**Internal NIB (Network Interface Board)**[/list]

So I think you do need to connect it via ethernet. It is usually as easier as connecting via usb.

Instead of trying to tweak the script (if that's possible at all), I suggest you try the ethernet first, and post back if there you face any issues.

---

### Post by steeldriver on 2013-03-14
Have you tried just using the CUPS web interface? open a browser and enter

```
http://localhost:631/admin/
```

then press the 'Add Printer' button - does the Ricoh show up as a local printer?

You will need to have installed the cups package, and be a member of the lpadmin group iirc

---

### Post by varunendra on 2013-03-14
Just realized -
> which is running an old version of Red Hat

..as such.. *Thread moved to **Other OS/Distro Talk**.*

---

### Post by CaptainMark on 2013-03-14
Cups is installed and running for other printers already on the network, where its old though, the drivers are not up to date, I've got it working with an old Ricoh driver for a different printer model but some prints come out garbled and full of random characters and some features are missing such as duplex printing

---

