---
title: "Printer problems"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by getut on 2007-05-16
Hello...

I'm running Ubuntu Feisty that was originally installed from scratch as Herd 2 and then updated through all updates to the completely current install I have now. I have also installed the kubuntu-desktop packages.

I was previously running Ubuntu Edgy on this same machine and my Epson Stylus Photo RX500 worked fine. Now with Feisty, there seems to be no printer driver. What happened... I thought the database grew over time, not shrunk.... or is there something wrong with my install?

Please help me get my printer working with Feisty.

---

### Post by Hobo Joe on 2007-05-16
System>Administration>Printers>New printer.

Follow the instructions. Or is this what you already did?

---

### Post by getut on 2007-05-16
Thats what I did, but there is no driver option for the RX500 anymore. It existed in Edgy.

Could this be a problem created by my having loaded kubuntu-desktop on top of my Ubuntu (in other words a kde problem)... or did the driver database truly go backwards in this newer version of Ubuntu.

---

### Post by chamberlain2006 on 2007-05-16
If the driver existed and worked in Edgy, it must surely exist on the net somewhere.  Let me see if I can find it.

---

### Post by chamberlain2006 on 2007-05-16
It reccomends the gutenprint driver, so i think that installing the cupsys-driver-gutenprint package will provide ther necessary driver.

---

### Post by getut on 2007-05-17
Thanks for the reply. 

Ok.. I checked as soon as I got home tonight and cupsys-driver-gutenprint is already installed. In fact it said it was a dependency for both ubuntu-desktop and kubuntu-desktop and offered to remove both of those... I of course said no.

Any other ideas to get the correct driver for that printer?

---

### Post by igb on 2007-07-15
Did you ever find a solution? The same thing happened to me when I did a fresh install of Feisty, there is no driver for the RX500.

Edit.
Managed to add it using the CUPS web interface at [http://localhost:631](http://localhost:631)

Don't know why the printer isn't listed in the KDE add printer wizard.

Ian.

---

