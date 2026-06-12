---
title: "Using MBRfix to fix broken MBR"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Hillbilly-Rockstar on 2007-01-06
I have Ubuntu on my current laptop partitioned with Windows.  I got a new laptop for Christmas and would like to use that one for Ubuntu, and my current one for Windows.  I would like to remove Ubuntu on my current one to save disk space.  The only problem is that I need to fix the MBR without the Windows Recovery console.  The one that you can download from Microsofts website is for floppy drives only.  I know that MBRfix is a popular program to fix this problem, but I just don't know how to use it.  Any advice?

---

### Post by Hillbilly-Rockstar on 2007-01-06
bump.  I don't want to have to pay $100 for some geek squad guy to come out.

---

### Post by sailor2001 on 2007-01-06
when booting up.....click delete or f1 or f2 or esc (depends on your pc) to open dos screen and just type fixmbr and then ctrl/s and close out

---

### Post by Hillbilly-Rockstar on 2007-01-06
Is that with or without the MBRfix CD in?  I tried that and it didn't work.

---

### Post by CroEragon on 2007-01-06
Somebody told me that fixmbr should work as command in run window. winkey+r and then fixmbr. I din't test it.

---

### Post by Hillbilly-Rockstar on 2007-01-06
> **CroEragon said:**
> Somebody told me that fixmbr should work as command in run window. winkey+r and then fixmbr. I din't test it.

Nope :(

---

### Post by jvc26 on 2007-01-06
Edit: sorry misread and presumed you were trying with recovery console.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
perhaps that may help?
Il

---

### Post by Hillbilly-Rockstar on 2007-01-06
> **Illuvator said:**
> Edit: sorry misread and presumed you were trying with recovery console.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)
perhaps that may help?
Il

The first sentence in that resource says that you must be using the recovery console.

---

### Post by CroEragon on 2007-01-06
Use SuperGRUB. It got option that wil rewrite your MBR same as you used fixmbr. Found it useful when i messed GRUB and had to enable Windows. [Download link]("http://supergrub.forjamari.linex.org/download.php")
Note: it is .iso  of LiveCD and needs to be burned on CD first.

---

### Post by jvc26 on 2007-01-06
> **Hillbilly-Rockstar said:**
> The first sentence in that resource says that you must be using the recovery console.

Hence read the edit ;)
Il

---

### Post by MrKlean on 2007-01-06
The fixmbr that I mentioned in another post is on the original xp disk.  If you don't have that disk , I have no idea..but that worked for me ; )

---

### Post by Bigbluecat on 2007-01-06
As mentioned in an earlier post try SuperGrub disk. Here is the link:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Burn it as an ISO and boot from the CD. It is a superb utility and well worth keeping around.

---

