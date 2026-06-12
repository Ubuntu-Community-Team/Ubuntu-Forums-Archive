---
title: "Windows printer - no linux driver"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by lorre on 2006-08-28
I have a printer that is not supported by ubuntu (Dell A960/Lexmark 6710(?)), as a workaround I have the printer connected to a windows pc in my network and do all the printing on that machine.

Is it possible to print directly from ubuntu to this printer (assuming that is being shared) thus without having the appropriate driver?

---

### Post by hw-tph on 2006-08-28
Yes. Go to System --> Administration --> Printing and click New Printer. Select Network Printer and then Windows Printer (SMB) from the dropdown menu. Enter the network path (host and printer name) and that's pretty much it.

Håkan

---

### Post by lorre on 2006-08-29
Thanks! Will try..

---

### Post by lorre on 2006-08-29
If I select 'network printer (SMB)' give the path and printer name and go to the next screen I STILL have to select brand/model of the printer which isn't there because it is not supported. This brings me back to my original question; can I print on a network printer (Windows) that is not supported by Ubuntu?

---

### Post by sbassett on 2006-08-29
Select raw, then the processing is done on the server of the printer.

---

### Post by lorre on 2006-08-29
Selecting 'raw' get's me one screen further.. Now I have to select a ppd file for my printer. I have looked (intensively) on the web but could not find one for my Dell A960/Lexmark 6170 printer. I also searched my Windows PC to wich my printer is connected. It only finds ppd files in the driver.cab file but not one matching my printer (used grep to look for files containing printer model).

Anything else I can try?

---

### Post by sbassett on 2006-08-29
> **lorre said:**
> Selecting 'raw' get's me one screen further.. Now I have to select a ppd file for my printer. I have looked (intensively) on the web but could not find one for my Dell A960/Lexmark 6170 printer. I also searched my Windows PC to wich my printer is connected. It only finds ppd files in the driver.cab file but not one matching my printer (used grep to look for files containing printer model).

Anything else I can try?

If you select SMB, then raw, this should bring you to the portion where you select the name description and location. Is this not the case.

---

### Post by lorre on 2006-08-30
Yes, I have to fill in the the location and printer name when selecting SMB/raw, but what follows is a screen where I have to select the PPD file for my printer..

---

### Post by hashimoto on 2006-08-30
Maybe this can help you:
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by lorre on 2006-08-30
Hmm, that howto describes exactly what sbassett is suggesting. I've tried this multiple times yesterday but the system keeps asking me where the PPD file is. Maybe I am missing something here, I'll give   it another try tonight..

---

### Post by tomBorgia on 2006-08-30
I usually use the generic PCL/6X setting for printing to SMB printers... seems to work ok and support multiple trays. 
Have a look on linuxprinting.org - You can download a PPD file from there for almost all printers... think of these as drivers - Using the add printer dialog through system>admin>printing>new printer etc... when you get the screen up that allows you to select the printer driver there should be a button "install driver" - use this to open the PPD file you downloaded from linuxprinting.org and all should be sweet!

Tom.

---

### Post by lorre on 2006-08-30
I checked linuxprinting.org but unfortunately no ppd for my Dell A960/Lexmark 6170 printer (also not on the Dell/Lexmark website, or the whole www). You mention 'generic PCL/6X setting', is this a replacement for a printer specific ppd? Is it like a generic ppd that makes basic printing possible on most printers? That'll work for me..

---

### Post by tomBorgia on 2006-08-30
Yer, try the generic PCL / 6 (if that doesn't work try the 5, then 4 etc) - the PCL thingy seems to be a general purpose printer protocol supported by *most* printers... give it a go.

---

### Post by lorre on 2006-08-30
Selecting 'generic PCL / 6' does not help me, I am experiencing the same problem as with 'Raw (Queue)'. I am thankfull for all the (quick) help I am getting here but all of the provided solutions suggest that I no longer have to select a ppd file which is not true:

If I select one of these drivers I have to select 'Forward' and after that it comes with a 'File Open' dialog where I HAVE to select a ppd file (which I don't have). Like with the drivers (Raw/Generic) is it possible to have a generic ppd file allowing basic printing? If so can anyone give the name of this ppd (and where can I find it)?

---

### Post by sbassett on 2006-09-08
Lorre -

Just a quick question, are you using the gnome-cups-admin program or the kcontron - printer module? Or, are you doing this from Gnome or KDE? All my suggestions were based on the assumption that you were using the Gnome printer program.

---

### Post by lorre on 2006-09-08
I am using the Gnome printer program. Are you asking me this because you are not prompted for a ppd when adding a printer?

---

### Post by sbassett on 2006-11-01
> **lorre said:**
> I am using the Gnome printer program. Are you asking me this because you are not prompted for a ppd when adding a printer?

That would be correct. I can setup a generic printer, select raw and go from there.

---

### Post by speedqueen on 2007-11-26
Can't you search your windows machine for the *.ppd file and use it for Linux?  That is, if it is even necessary.

---

