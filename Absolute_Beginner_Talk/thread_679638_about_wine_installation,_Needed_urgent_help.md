---
title: "about wine installation, Needed urgent help"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by haroonsayyad on 2008-01-27
Hi,
I follow every steps given for WINE installation on ubuntu-gutsyGibbon ver 7.10. But from synaptic package manager ask for Installable CD like below.

Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)
in drive /cdrom/

---

### Post by jhenager on 2008-01-27
Are you connected to the internet? I have never been prompted for the original install disk that I can recall.

---

### Post by AlexenderReez on 2008-01-27
in terminal

> gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

uncheck installable from cd-rom/dvd part

and

reload...

---

### Post by Incense on 2008-01-27
> **jhenager said:**
> Are you connected to the internet? I have never been prompted for the original install disk that I can recall.

If you don't have an internet connection during your install, then the CD will remain part of your sources.list.

---

### Post by jhenager on 2008-01-27
> **Incense said:**
> If you don't have an internet connection during your install, then the CD will remain part of your sources.list.

You are correct, because I did exactly that, but I just installed 185 updates this morning and it did it all across the wire without asking for the CD.
It is still listed in my software sources, too.

---

### Post by Incense on 2008-01-27
> **jhenager said:**
> You are correct, because I did exactly that, but I just installed 185 updates this morning and it did it all across the wire without asking for the CD.
It is still listed in my software sources, too.

If you have a good internet connection it's good to just comment the CD out as a source. Then you don't have to worry about a CD request when you don't have one. 

```
gksudo gedit /etc/apt/sources.list
```

Place a # in front of the line CD repo so that it looks like this. 

```
 # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

save and close.

---

### Post by haroonsayyad on 2008-01-28
> **Incense said:**
> If you have a good internet connection it's good to just comment the CD out as a source. Then you don't have to worry about a CD request when you don't have one. 

```
gksudo gedit /etc/apt/sources.list
```

Place a # in front of the line CD repo so that it looks like this. 

```
 # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

save and close.

Thanks for your best advice, because of you I can solved my problem. Any way I want to know , if some one who don't have a good internet connection, then how he/she will install the wine?

---

### Post by david_kt on 2008-01-28
> **haroonsayyad said:**
> Thanks for your best advice, because of you I can solved my problem. Any way I want to know , if some one who don't have a good internet connection, then how he/she will install the wine?

Download it from here:

```
http://wine.budgetdedicated.com/archive/index.html
```

using other computer with internet connection, and then transfer it to the said computer, and double click to install. Anyhow, if it require additional packages, you should notice what they are and the download locations, and do the same.

DK

---

### Post by haroonsayyad on 2008-01-28
> **david_kt said:**
> Download it from here:

```
http://wine.budgetdedicated.com/archive/index.html
```

using other computer with internet connection, and then transfer it to the said computer, and double click to install. Anyhow, if it require additional packages, you should notice what they are and the download locations, and do the same.

DK

Thanks a lot 

I will remember this technique

---

