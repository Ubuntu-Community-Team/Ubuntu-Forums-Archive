---
title: "Dell Laser Printer"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2007-06-06
My Dell Laser came with a RPM. How do I run this redhat package in Ubuntu? Or is there a better way to install the driver?

Thanks,
John

---

### Post by FleetAdmiral74 on 2007-06-06
I cannot vouch for how good this program is...but might want to try it out, seems to be what you want.

[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

---

### Post by NilsE on 2007-06-06
I never had a failure of alien creating a .deb file from a .rpm file so go for it.

---

### Post by crjackson on 2007-06-06
> **phr0ze said:**
> My Dell Laser came with a RPM. How do I run this redhat package in Ubuntu? Or is there a better way to install the driver?

Thanks,
John

Wow, I just got this working on my computer today.  I have a Dell 5100cn that came with the RPM driver.  Here's what worked for me.

I used the program/package called alien - I used the program to convert the RPM file to a DEB file.  Then I installed the DEB.

Next, with the printer turned off, I went to the ADD PRINTER dialogue and told it to add.  It searched the printer databae and gave me a long list.  I selected Dell and then M5200.

Next it gave me the option to rename the printer.  I named it 5100cn, then it told me to install the driver and I think I ignored that.

Next I had to change the default paper settings from A4 to US Letter in two different places (look under the printer setup tabs).

Print test page DOES NOT WORK... Don't even worry about that...

Next I made this my default printer, loaded Open Office Word and tested...

It workd Perfectly, color settings worked, resolution settings worked...  I didn't mess with the paper tray or look for the MPF tray at all so I can't say about that.

That's it, it worked for me after several days of begging for help with negative results. I woke up early this morning and started poking around....  It took 5 minutes to fix....  After Days messing around without a clue....


Hope this helps...  Good luck...

---

