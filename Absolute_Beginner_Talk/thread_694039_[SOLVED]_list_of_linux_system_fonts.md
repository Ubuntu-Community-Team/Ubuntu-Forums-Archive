---
title: "[SOLVED] list of linux system fonts"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by reeksy on 2008-02-11
Hi

I'm a web developer and have recently installed Linux at home to develop an open source app. Things looked fine in a browser on a windows box, but the system fonts are different on linux so the styles have been thrown out a little!

Im really after knowing what the default system fonts are on a linux box? For example on windows you can take a safe bet that the user will have arial or verdana so you can code your style sheet around that. But on linux i dont know what's a safe bet!

Ideally, i want the name of a system font that's close to Calibri. Failing that Arial or Verdana.

Any ideas?

Regards.

---

### Post by Tenken on 2008-02-11
/usr/share/fonts/ has all the default fonts that come with Ubuntu, and I'm guessing those are standard on most *nix distributions.

---

### Post by hyperair on 2008-02-11
Well... I don't really see an issue with using the actual Calibri font. =P I dragged all my fonts over from Windows.

---

### Post by jan quark on 2008-02-11
you can install the small application 

gnome-specimen

```
sudo apt-get install gnome-specimen
```

and run it through the terminal by simply typing

```
gnome-specimen
```
and enter


it will list all installed fonts and show you a preview

---

### Post by reeksy on 2008-02-12
OK thanks for the replies. Problem solved.

---

### Post by erginemr on 2008-02-12
And two more ways to view installed (and default) fonts are:

1. Main Menu -> Preferences -> Appearance -> Fonts Tab

2. Nautilus File Browser -> Address Bar -> "fonts:///"

P.S. You should also check out the Live CD's of other popular distro's, such as Open SuSE, Fedora Core, PC Linux OS, Mandriva, etc. 
(the list taken from [http://www.distrowatch.com](http://www.distrowatch.com)) to record their default fonts.

---

### Post by reeksy on 2008-02-14
Thanks erginemr, that's great.

---

