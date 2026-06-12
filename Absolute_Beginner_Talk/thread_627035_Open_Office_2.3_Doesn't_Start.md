---
title: "Open Office 2.3 Doesn't Start"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by parm289 on 2007-11-29
Hello, 

When I try to start OpenOffice 2.3 (on Ubuntu and GNOME), the splash screen appears, the loading bar fills up, and the process stops right there.  The splash screen never disappears (I waited 10 minutes), and I am forced to end the process.  After I end the process once and try to start OO from the Apps menu or Terminal, nothing happens at all (the process doesn't start).

I tried reinstalling all the OO packages, but same problem occurred.

Any help is appreciated.

---

### Post by wjp.reg on 2007-11-29
> **parm289 said:**
> Hello, 

When I try to start OpenOffice 2.3 (on Ubuntu and GNOME), the splash screen appears, the loading bar fills up, and the process stops right there.  The splash screen never disappears (I waited 10 minutes), and I am forced to end the process.  After I end the process once and try to start OO from the Apps menu or Terminal, nothing happens at all (the process doesn't start).

I tried reinstalling all the OO packages, but same problem occurred.

Any help is appreciated.

What do you mean by: > I tried reinstalling all the OO packages, but same problem occurred.?  was this a custom install or did you use the 'buntu/synaptic package install?

---

### Post by parm289 on 2007-11-29
> **wjp.reg said:**
> What do you mean by: ?  was this a custom install or did you use the 'buntu/synaptic package install?

Well OO came preinstalled with Ubuntu, but then I reinstalled all the OO-related packages via Synaptic.

---

### Post by SOULRiDER on 2007-11-29
Run it from a terminal to see if it spits any errors. To run it type:
```
soffice
```

---

### Post by philinux on 2007-11-29
what are your system specs?

---

### Post by parm289 on 2007-11-29
I tried running it with soffice, but nothing happens.  The program doesn't start, and teminal continues to the next line without the user@... prefix.

System:
Gutsy
Pentium Dual-Core 1.86 GHz processor
1 GB RAM
NVIDIA Graphics card (G70 [GeForce 7600 GS])

Anything else you need to know, just ask.

---

### Post by fatespeaks on 2007-11-30
Try disabling desktop effects.  I have had a couple of problems with Compiz-Fusion running my NVidia card out of memory.  Usually the result is a black window, but occasionally I get no visual response.
Cheers,
Aaron

---

### Post by sourcemorph on 2007-11-30
i had a similar problem.. in my case the impress application wont start...if it doesnt open even wit the default human theme then  try uninstalling openoffice.org-gtk frm synaptic n then opening the application... this solved my problem.

i think ooo has some prob with the gtk engines...

---

### Post by bhaumik_thacker on 2008-02-14
hello,

my open office 2.3 doesn't start i.e. flash screen appears for a second and then disappears. now i tried starting it using the "soffice" command after reading this thread.and this is the error message i m getting 
"/usr/lib/openoffice/program/soffice.bin: relocation error: /usr/lib/openoffice/program/libuno_cppuhelpergcc3.so.3: symbol uno_type_sequence_assign, version UDK_3_0_0 not defined in file libuno_cppu.so.3 with link time reference"

meanwhile i also tried it after uninstalling  the open office.org-gtk package but in vain

---

### Post by Hagar Delest on 2008-02-15
You can try to rename your OOo user profile folder (~/.openoffice.org). If no improvement, you can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by bhaumik_thacker on 2008-02-15
> You can try to rename your OOo user profile folder (~/.openoffice.org).

i saw one of your replies in another thread as well. and it read same as above.
but how do i do this.?
sorry, but i m a very first time user of free software,read about it on the internet and loved the idea.
i m using ubuntu 7.10.
thanks for the response.

---

### Post by FuturePilot on 2008-02-15
Open your home folder and press Ctrl+H to show the hidden files. Find the .openoffice.org2 folder and rename it. The next time you start Open Office it will create a new one.

---

