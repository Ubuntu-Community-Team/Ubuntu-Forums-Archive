---
title: "Can anybody print direct from Scribus to an inkjet printer"
date: 2007-10-27
forum: Art &amp; Design
---

### Post by xhilyn on 2007-10-27
Hi all

Just wondering if anybody has managed to print direct to an inkjet printer with Scribus.

I have an old Epson 740 which works fine with Open Office and will print PDF's that I have output from Scribus but it just spits the paper straight out when I try to print direct from Scribus itself.

I have searched the Ubuntu groups and the net but have yet to find any answer.#

So any help would be much appreciated as I wanted to start to learn how to use Scribus but if I cannot print directly from the programme then there is little point in learning how to use it.

---

### Post by CDL-WarChilde on 2007-10-27
I don't have an old epson printer to try anymore, but if you're able to print pdf files, might try to print your scribus pages as a pdf then print those pdf files.

---

### Post by xhilyn on 2007-10-28
Yeah that's what I'm doing at the moment but thanks for the answer.

I'm just not that impressed with a DTP programme that cannot print.
I assume it's the Printer Driver but it works fine in other programmes

So it's certainly not ready for a production enviroment.

Thanks for your though.

---

### Post by Pete051 on 2007-10-30
Not me, in fact I've just been trying to print from Scribus  1.3.4 and
Scribus 1.3.3.9 and the results are:
Scribus 1.3.4 print direct no, print from dpf hmm yes but nothing like the print preview, in fact not usable.
Scribus 1.3.3.9 print direct no, print from pdf yes good quality.
I tried with pdf 1.3, 1.4 and 1.5 and the results were the same.
So in conclusion Scribus 1.3.3.9 id usable Scribus 1.3.4 is not but it a tad odd to have a DTP program that can't print direct :)
The printer is a Epson R360

---

### Post by jjalocha on 2007-11-22
I am having problems printing with Scribus, too, here:

Epson Stylus CX3900

* Scribus under Feisty, prints OK.

* 'scribus' package under Gutsy: Prints totally black pages. PDF output somehow crapped. (VERSION 1.3.3.9.dfsg-1ubuntu1)

* 'scribus' package from the Scribus repository ([http://wiki.scribus.net/index.php/Getting_Scribus_on_Ubuntu/Kubuntu_up_and_running):](http://wiki.scribus.net/index.php/Getting_Scribus_on_Ubuntu/Kubuntu_up_and_running):) Prints black pages, but PDF output seems to be OK. (VERSION 1.3.3.10.dfsg~svn20071109-1)

Haven't tried 'scribus-ng' package yet, don't know if this would improve situation, or just make it worse somewhere else. But I am honestly so tired of fighting with Scribus annoyances...

Sadly, printing the PDF is no solution for me either, since Evince doesn't want to print PDFs for me ([http://ubuntuforums.org/showthread.php?t=616169](http://ubuntuforums.org/showthread.php?t=616169)).

---

### Post by jjalocha on 2007-11-24
There might be a solution for some of you (with blank pages):
[https://bugs.launchpad.net/ubuntu/+source/scribus/+bug/131442](https://bugs.launchpad.net/ubuntu/+source/scribus/+bug/131442)
I can't test it from my current location, since I don't have a printer here.

---

### Post by Harvs on 2007-11-27
Wow - I can print directly from Scribus now....

Following the link, I just selected "Alternative print command" and entered "lpr" (Strangely though, setting the 'set print media' in advanced options, as I think it means in the bug report, stopped it working.)

Bit of a pain, but not as much as saving it as a pdf, finding where I saved it and pricing it from there....

There's always some workaround for everything in Ubuntu!!

---

### Post by zool2005 on 2007-12-02
I had the same problem with a HP Deskjet printer.
As I had no problem printing from Adobe PDF reader, I copied the exact print command (print --> properties) to the custom command entry in Scribus and everything works fine !
e.g. /usr/bin/lpr -P DeskJet-5550

Hope this helps

---

### Post by xhilyn on 2007-12-20
Hi all

Well I've tried the workaround for the blank page bug but to no avail here.
I still cannot print to an Epson inkjet printer from Scribus so I just cannot use it at this time. Which is a real pain as I am trying to change over to Ubuntu Linux permantly but without Scribus I cannot do half of what I need to do and no sign of a fix any time soon. Ah well I will just have to go back to my old Winows and Mac computers, which of course completely defeats the object of trying Ubuntu in the first place. So Linux still isn't ready for me to recomend, and I was so hoping that it was. So at the moment I am a rather disapointed x Scribus user

xhi

---

### Post by billandteresa on 2008-01-03
Hello all 

I have just got scribus working fine with my Epson stylus cx3650, just done this...... "In the box named Alternative print command" in the scribus print setup thingmy enter......lpr

Job done.... made me happy now the only reason I need xp is for Medieval total war ii....:)

---

### Post by danielph on 2008-01-19
I am still getting this with scribus 1.3.3.11-1. I was wondering if anyone here actually opened a bug against this problem with scribus. The workaround works, but are the devs aware of the problem?

---

### Post by jal on 2008-03-08
> **jjalocha said:**
> There might be a solution for some of you (with blank pages):
[https://bugs.launchpad.net/ubuntu/+source/scribus/+bug/131442](https://bugs.launchpad.net/ubuntu/+source/scribus/+bug/131442)
I can't test it from my current location, since I don't have a printer here.

Yep, that did it, Thank you jjalocha.

Scribus was printing beautiful pitch black A4 pages on the Epson CX3900 (using CX3800 driver), the bug workaround was needed.

menu print...
check Alternative printer command -> Command: "lpr"
Advanced Options tab -> check "Set media size"

---

### Post by RINKO on 2010-01-16
> **billandteresa said:**
> Hello all 

I have just got scribus working fine with my Epson stylus cx3650, just done this...... "In the box named Alternative print command" in the scribus print setup thingmy enter......lpr

Job done.... made me happy now the only reason I need xp is for Medieval total war ii....:)

thats the solution for me.

thanks man

---

