---
title: "How do you get to the HPLIP Toolbox?"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by JimCockfield on 2006-07-25
Can anyone tell me how to start the HPLIP Toolbox?

It appears that HPLIP is installed and running.  But, I don't know enough about Linux to pull up the HPLIP Toolbox to check ink levels, align print heads, etc.

In some other distros, it's a menu choice.  But, I can't find it in Ubuntu (6.06 LTS).

---

### Post by dragon1964m on 2006-07-25
$ hp-toolbox

---

### Post by dragon1964m on 2006-07-25
Or Applications > Accessories > Alacarte Menu Editor > select Administration tab and check "HP Toolbox" then it will show up as a menu item.

---

### Post by Sef on 2006-07-25
If the toolbox don't work, here's how I got my toolbox to work:

> Figured out how to get the toolbox to work.

1) In the tutorial, there are two steps.

[https://wiki.ubuntu.com/HpPrinterIns...ntenanceDapper](https://wiki.ubuntu.com/HpPrinterIns...ntenanceDapper)

2) However, I had three steps. The first two were the same. In the third step, I had this in the box:

Name: HP_1610

Description:

Location:

Since the last two were empty, I decided to fill them in, so in Description, I added local printer.

In Location, I did this: In the terminal, I typed lpinfo -v, next I copied the info from there and then pasted it in the Location. Finally I clicked apply. I got my toolbox

---

### Post by JimCockfield on 2006-07-25
Thanks.

That added the menus.  But, it won't run.   Ditto for trying it from command line.   I get this error screen either way.

"You must install python-qt3 for this program to work"

So, I'll try to search for python-qt3 and install it.

---

### Post by JimCockfield on 2006-07-25
OK

I've got it to where it "tries" to load the HPLIP toolbox now.   But, it tells you that printers must be installed via the CUPS Web Interface.

Unfortunately, the CUPS Web Interface won't work.

Even though you can see a printer, and modify one, etc., at the last step (add or modify), it prompts you for a username and password.  No combination seems to work with it (even setting a root password won't work).

I do see this note when you go to the interface at [http://localhost:631/](http://localhost:631/)

"Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing). /usr/share/doc/cupsys/README.Debian.gz describes the details and how to reenable it again."

I've got the same problem with SimplyMEPIS 6.0 Final (which is the reason I loaded Ubuntu to begin with, to see if it would work instead).  Since SimplyMEPIS 6.0 is based on Ubuntu, I guess it makes sense that it won't work either.  lol

I don't know enough about linux to try and solve it (that read me file is pretty much greek to me).

---

### Post by JimCockfield on 2006-07-25
OK -- I got it working.   Thanks a bunch guys.   The help screens helped me figure it out:

[https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper](https://help.ubuntu.com/community/HpPrinterInstallationAndMaintenanceDapper)

I had to use the second printer choice found before HPLIP Toolbox would recognize my printer (like the help screens show).

One was listed as HP PSC 1400 Series, and the one that worked was shown as HP PSC_1400_Series.

That's probably the same problem I had in SimplyMEPIS.

---

