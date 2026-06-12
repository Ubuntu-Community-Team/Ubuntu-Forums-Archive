---
title: "X Server HELP (Toshiba Satellite p105)"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by ruiniel on 2007-03-07
Hello guys.

I'm fairly new to Linux.
I tried to install Kubuntu 6.10 and the installation process just stopped at some point and left me in text mode.
I next tried Ubuntu 6.10 and it failed at X Server.

I have a Toshiba Satellite p105-s6024 notebook,
Intel Core Duo t2050 Processor (2 x 1,6 Gh).

I trying to start using Linux :) I have installed a version of Sabayon but I'd like to try Ubuntu as well.

I tried installing Debian some time ago and got the same problem(text mode). I've been through some literature and forums and it seems that there is something with the ACPI.
I found a post here that the ACPI can be fixed by changing some DSDT file: 

[http://www.linlap.com/tiki-index.php?page=Toshiba+Satellite+P105](http://www.linlap.com/tiki-index.php?page=Toshiba+Satellite+P105)

The thing is that I'm a total newb and I don't dare overwrite things like that. I'm totally confused. :confused: 

Wikipedia says that:

"Contrary to early reports, the Intel Core Duo supports Intel's Vanderpool x86 virtualization technology, except in the T2300E model and proprietary T2050/T2150/T2250 mounted by OEMs"

Is the x86 version the wrong one? If so, which one should I dl? (But still, I have a running Sabayon - except for the sound)

Please, help! Ubuntu (especially with KDE) looks really nice, I'd love to give it a try :)
Is there anything I could do (without risking to bug my computer too seriously)?
Or is there any hope that this issue will be solved in the next versions? I know that other people with similar notebooks got the same problem.

Thanx in advance for any answer!:)

---

### Post by haelters on 2007-03-08
I've got a Toshiba P100 and also had to correct my dsdt. On the link you gave, there is a good howto. I simply followed it, and was able to repair my dsdt. I used the 'Build-in Options for Kernel 2.6.9 and Later' option as described in the Gentoo Howto.

Now my sound works correctly.

Try to follow the guide and let me know where you got stuck... I'll try to guide you then.

cu

---

### Post by ruiniel on 2007-03-08
Thanx for the response:)
Being a n00b, I'm stuck at the very first step. I read the gentoo wiki HOWTO here:

[http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

So, I should:
1. try upgrading my BIOS (I'm not sure how to do it but as far as I can understand, I should dl this upgrade here "sp100v24 BIOS Update", record it as an .iso image, then just boot the CD)

2. Change the DSDT file in the Kernel - now this is where I get completely lost. :confused:  I've been a Windows user for years, I recently bought my own computer and now I'm exploring Linux. :) I have some vague idea what the kernel and the BIOS are but I've never really messed with them. How do I edit the kernel? How do I reach kernel config?

Thanx in advance for the help, I know I sound lame.

---

### Post by haelters on 2007-03-11
Hello,

Start by following the Howto. In the section 'Diagnosing a Buggy DSDT' it explanes how to get the DSDL file. Try to follow the howto and tell me where you get stuck.

---

