---
title: "Brother MFC 210C"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by deboare on 2008-01-15
My Brother MFC-210C printer sometimes prints and sometimes does not. If I plug it in on my Windows computer everything works as smooth as it should. The weird thing is; I can print test pages :| :S. Those he does print,
what a fool I was to just believe people when they said Ubuntu was better, I've had nothing but trouble trying to print.

If you guys still want to help a member of this forum whose believe in Ubuntu is dying, then please do :)

Brecht

---

### Post by dstew on 2008-01-15
What driver are you using?

---

### Post by stchman on 2008-01-15
> **deboare said:**
> My Brother MFC-210C printer sometimes prints and sometimes does not. If I plug it in on my Windows computer everything works as smooth as it should. The weird thing is; I can print test pages :| :S. Those he does print,
what a fool I was to just believe people when they said Ubuntu was better, I've had nothing but trouble trying to print.

If you guys still want to help a member of this forum whose believe in Ubuntu is dying, then please do :)

Brecht

According to the Linux foundation that printer works mostly.  That is why you might be getting erratic performance.

[http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-210C](http://openprinting.org/show_printer.cgi?recnum=Brother-MFC-210C)

Blame Brother for not authoring good drivers for Linux not Linux.  HP is the best printer for Linux.

Avoid Lexmark printers as they almost never work with Linux.

---

### Post by Seisen on 2008-01-15
Also are you using 32-bit Ubuntu or 64-bit Ubuntu?

---

### Post by deboare on 2008-01-15
Sorry I'm just a bit pissed because my stephfather always comes to me and it's always this stupid printer that doesn't want to print.
Long time since I installed it, I can't remember where you can see which one you have...

---

### Post by deboare on 2008-01-15
> **Seisen said:**
> Also are you using 32-bit Ubuntu or 64-bit Ubuntu?

64, does it matter?

---

### Post by dstew on 2008-01-15
> Blame Brother for not authoring good drivers for Linux Well, at least they are trying. [Here ]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC210C-1.0.2-3.i386.deb&lang=English_gpl")is the MFC-210 driver from Brother. It is an x86 debian package. Here is a [How-To]("http://ubuntuforums.org/showthread.php?t=590793")

---

### Post by deboare on 2008-01-15
> **dstew said:**
> Well, at least they are trying. [Here ]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC210C-1.0.2-3.i386.deb&lang=English_gpl")is the MFC-210 driver from Brother. It is an x86 debian package. Here is a [How-To]("http://ubuntuforums.org/showthread.php?t=590793")

CUPS that's the one I have

---

### Post by dstew on 2008-01-15
Did you follow that How-To? You need the LPR driver, then the cupswrapper package. There is an extra step for 64 bit systems (step 8 ).

---

### Post by deboare on 2008-01-15
> **dstew said:**
> Did you follow that How-To? You need the LPR driver, then the cupswrapper package. There is an extra step for 64 bit systems (step 8 ).

I followed an other tutorial for it... And it's too long ago to remember the steps

---

### Post by dstew on 2008-01-15
Your problem sounds like a driver issue. My advice is delete the printer, then go through the How-To. You install the Tenex c-shell tsch (not sure why), then the LPR driver for your printer,  then the cupswrapper that attaches it to CUPS. Be sure to do the extra step for 64 bit systems.

---

### Post by deboare on 2008-01-15
> **dstew said:**
> Your problem sounds like a driver issue. My advice is delete the printer, then go through the How-To. You install the Tenex c-shell tsch (not sure why), then the LPR driver for your printer,  then the cupswrapper that attaches it to CUPS. Be sure to do the extra step for 64 bit systems.

Sigh, when I feel like it :)

---

