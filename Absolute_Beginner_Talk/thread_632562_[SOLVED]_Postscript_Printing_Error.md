---
title: "[SOLVED] Postscript Printing Error"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by fatality_uk on 2007-12-05
Previously, all the printers I have used under the various Linux distros worked well, but,**you knew there was a but**, we have a Panasonic DP-C264 and for the life of me I can't get the thing to work properly.

1) I tracked down the correct .PPD for that printer from [http://www.workio.info/](http://www.workio.info/). I know it's the right one because the printing options, Duplex, stapler etc are all present and correct and because it's named dpc264c.ppd :)

2) I went to System->Administration->Printing and added a new printer in there. It's installed on Windows 2003 SBS and shared there under **Pana DPC264** and could be verified when installed.

-------------------------------------------------------------

**_3_**) Now to the **PROBLEM**. Whenever I send anything to print to it, the output is basically what looks like a PS error header, single line and then about 54 blank pages. I have searched around and most advice is to get the right PPD file, which I have! I am using system-config-printer-py as installed with Ubuntu 7.10

**ANY** and I mean ***ANY*** help would be really appreciated

Thanks in advance

---

### Post by stchman on 2007-12-05
> **fatality_uk said:**
> Previously, all the printers I have used under the various Linux distros worked well, but,**you knew there was a but**, we have a Panasonic DP-C264 and for the life of me I can't get the thing to work properly.

1) I tracked down the correct .PPD for that printer from [http://www.workio.info/](http://www.workio.info/). I know it's the right one because the printing options, Duplex, stapler etc are all present and correct and because it's named dpc264c.ppd :)

2) I went to System->Administration->Printing and added a new printer in there. It's installed on Windows 2003 SBS and shared there under **Pana DPC264** and could be verified when installed.

-------------------------------------------------------------

**_3_**) Now to the **PROBLEM**. Whenever I send anything to print to it, the output is basically what looks like a PS error header, single line and then about 54 blank pages. I have searched around and most advice is to get the right PPD file, which I have! I am using system-config-printer-py as installed with Ubuntu 7.10

**ANY** and I mean ***ANY*** help would be really appreciated

Thanks in advance

I checked the openprinting.org website and your printer is not even listed.  Chances are it is not very Linux compatible.

The DP-C322 is a paperweight in Linux so the outlook is not good.

---

### Post by fatality_uk on 2007-12-06
Thanks for the answer. I did check openprinting.org, but I guessed that PS was PS, either on Unix, Mac, Windows or Linux.

To coin an olde English phrase, BUGGER!

---

### Post by robbak on 2008-01-14
This printer actually works quite well in linux, at least until recently, for me.
If you have paid (quite alot, actually) for postscript support, then it would understand postscript. Its PS support is very good, as they licence the official adobe implementation. That is why it costs so much.

If not, then the printer speaks an emulation of HP's PCL6e, which is supported by a number of cups backends. Just select a HP printer model that speaks PCL6. I have been using "Laserjet 6 CU". However, just recently, it has begun to play up on the hardy previews, crushing the page to a6 size, without adjusting fonts.

Edit: I have just now switched to "HP LaserJet Series PCL 4/5, 1.3", which has the printer working in monochrome, which is OK for me for now.

---

### Post by fatality_uk on 2008-02-08
Revived this as got some advice from a man in the know. Using HP PCL6 driver and works yay :D B&W but hey ;)

---

