---
title: "Printer just.doesn't.work. :("
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-02-24
I have a Canon LBP2900. I download the official drivers from the Canon website. However, whenever I tried printing a test page (or any other page), it just hangs on "processing" infinitely and does nothing. How can I diagnose the problem? I really want my printer to work with Ubuntu. This is my second try. I went back to Windows because this printer didn't work the first time.

---

### Post by linuxwizard on 2008-02-24
According to > [http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP2900](http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP2900) >  that printer is classified as PAPERWEIGHT.

---

### Post by rkakkar on 2008-02-24
> **linuxwizard said:**
> According to > [http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP2900](http://www.openprinting.org/show_printer.cgi?recnum=Canon-LBP2900) >  that printer is classified as PAPERWEIGHT.

what does that mean? that it will never run on ubuntu?

---

### Post by linuxwizard on 2008-02-24
That's a good question. It depends if they ever release or make a linux supported driver.

---

### Post by shanepardue on 2008-02-24
Have you tried setting up the printer without using the manufacturer's driver or is that what 
you have already tried? Ubuntu will try and install it with it's own method by default. I'm 
curious as to what you have already tried (in more detail).

---

### Post by rkakkar on 2008-02-24
> **shanepardue said:**
> Have you tried setting up the printer without using the manufacturer's driver or is that what 
you have already tried? Ubuntu will try and install it with it's own method by default. I'm 
curious as to what you have already tried (in more detail).

By default, Ubuntu installs the "generic printer driver". That does not have any options that i can set. For example the only paper size I can set is 'letter'. So didn't try working with that and ended up going straight to Canon's website and downloaded their Linux driver which came in RPM and DEB format.

---

### Post by rkakkar on 2008-02-24
> **linuxwizard said:**
> That's a good question. It depends if they ever release or make a linux supported driver.

They have! Which is what I installed in Ubuntu!

Btw what does this mean?

```
CAPT_Printer_Driver_for_Linux_V1.50E(6.8MB)
CAPT_Printer_Driver_for_Linux_Driver150v[1].tar.gz
CAPT_Printer_Driver_for_Linux_source file_V150E(5.1MB)
CAPT_Printer_Driver_for_Linux_Src150v[1].tar.gz
distributors_CAPT_Printer_Driver_for_Linux_V150E(6.2MB)
distributors_CAPT_Printer_Driver_for_Linux_Driver150v[1].tar.gz
distributors_CAPT_Printer_Driver_for_Linux_source file_V150E(4.6MB)
distributors_CAPT_Printer_Driver_for_Linux_Src150v[1].tar.gz

Notice on Linux Driver
This Driver requires installation of **Ghostscript including common API**. Before installing this driver, make sure that Ghostscript including common API is installed. Acquiring method of Ghostscript including common API varies in accordance with the kind of distribution.
See the URL below:
http://opfc.sourceforge.jp/index.html.en
```

---

### Post by rkakkar on 2008-02-24
I found something in the readme file of the official Canon printer driver! Maybe this might help others too...

```
 If you are using Ubuntu7.10, you may fail to print because it introduces
 security software called AppArmor.
 As the workaround, disable the AppArmor CUPS profile by running
 sudo aa-complain cupsd to enable printing.
 For more details, see Ubuntu7.10 Release Notes.

```

I'll try it out and see what happens

---

### Post by rkakkar on 2008-02-24
didn't do the trick.. anyone know what they are talking about?

---

### Post by bettlebrox on 2008-02-24
Say's here that it works:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

---

### Post by rkakkar on 2008-02-24
> **bettlebrox said:**
> Say's here that it works:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

I followed the steps mentioned there.. but in the "Second Test", it fails:

```
$ captstatusui -P LBP2900
*** captstatusui Socket Error ***

```

---

