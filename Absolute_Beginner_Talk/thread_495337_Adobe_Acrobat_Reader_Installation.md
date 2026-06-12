---
title: "Adobe Acrobat Reader Installation"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by giulian on 2007-07-07
New to Ubuntu, what is the best way to install the .tar.gz file of Acrobat Reader downloaded from the Adobe website, thank you!

---

### Post by RomeReactor on 2007-07-07
Hi. Extract the file (it should give you a folder named **AdobeReader**;  cut & paste that folder to your **home folder** (if it's not there already). Now open a terminal (Applications->Accessories->Terminal), and enter this:
```
cd AdobeReader
```
and then
```
./INSTALL
```

---

### Post by ramjet_1953 on 2007-07-08
Acrobat reader is available in the repositories.

You can use Synaptic package manager and search, using [COLOR="Blue"]acroread[/COLOR]

Otherwise just copy and paste this command into a terminal:

[COLOR="Red"]sudo apt-get install acroread[/COLOR]

Doing it this way gets you a version which is optimised for Ubuntu.

Regards,
Roger :cool:

---

### Post by aysiu on 2007-07-08
*acroread* is no longer in the standard (or even Multiverse) Ubuntu repositories.

If you [add the Medibuntu repositories](http://medibuntu.sos-sts.com/repository.php), though, you can use Synaptic Package Manager to install Acrobat Reader.

---

### Post by ramjet_1953 on 2007-07-08
You're right, aysiu!

After some time, I tend to forget which repositories that I have enabled!

Thanks for the heads-up!

Regards,
Roger :cool:

---

### Post by aysiu on 2007-07-08
Well, it used to be in Multiverse a few releases ago. Don't know why that situation changed.

---

### Post by neoguy2012 on 2007-07-08
Hi,

A PDF viewer may already be installed by default.  Just try downloading a pdf from somewhere and try opening it.  If it doesn't work, try installing Evince, which is a nice pdf viewer for GNOME, or KPDF for KDE (I believe these are installed by default, but I could be wrong...).  If you must install acroread, then you may obtain it from the medibuntu repositories.  This is the easiest way to install it.  You can obtain information regarding setting up the medibuntu repository from here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Please read the disclaimer though.  Good luck!

---

### Post by aysiu on 2007-07-08
neoguy2012 has a point.

The first year I used Linux, I always "needed" to have Adobe Acrobat installed.

Then I realized that the PDF readers that came with Ubuntu or Kubuntu (Evince or KPDF, respectively) were actually better for more purposes than Adobe Acrobat Reader (which tended to take a really long time to load).

Give Evince a chance.

---

