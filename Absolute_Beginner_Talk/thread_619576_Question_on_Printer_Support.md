---
title: "Question on Printer Support"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-11-21
I was just wondering if my HP PSC 2410xi photosmart all-in-one would have some of the functionality it has under Ubuntu as it does under Windows XP. 

I am mostly concerned about its ability to scan images/documents and save them. I have had Ubuntu in the past, and it printed fine, so I know the printer is at least detected. In addition, I believe the copy function is dependent on just the printer so that isn't an issue.  The ability to fax may be of concern to other people in my house. 

Any information on any of these functions of my printer would be helpful :-)

---

### Post by newlinux on 2007-11-21
> **SilverDragon said:**
> I was just wondering if my HP PSC 2410xi photosmart all-in-one would have some of the functionality it has under Ubuntu as it does under Windows XP. 

I am mostly concerned about its ability to scan images/documents and save them. I have had Ubuntu in the past, and it printed fine, so I know the printer is at least detected. In addition, I believe the copy function is dependent on just the printer so that isn't an issue.  The ability to fax may be of concern to other people in my house. 

Any information on any of these functions of my printer would be helpful :-)

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)

It looks like through HPLIP scanning is supported (probably through xsane by itself as well). Just install hplip.
```

sudo apt-get install hplip
```

Faxing probably won't have an interface through the computer, but you can probably do it stand alone (like copying) on the printer.

You might want to just go the hplip home page to get a little more info on using it... Any questions feel free to ask...

---

### Post by SilverDragon on 2007-11-21
Thanks for the quick response :-)

I should be wiping off Windows and installing Ubuntu again after I do some stuff in Microsoft Office 2007 for a class and backing up everything.

My only concern for now was if the printer's functions would work and it seems like they will.

May I ask what "xsane" is?

---

### Post by newlinux on 2007-11-21
You are welcome.

xsane is an app that interfaces with scanners.

[http://www.xsane.org/](http://www.xsane.org/)

It is also in the Ubuntu repositories.

---

