---
title: "[SOLVED] Openoffice's font wrong"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2008-02-20
[Screenshot]("http://www.flickr.com/photos/23987553@N02/2280896476/")

Whats going on?

---

### Post by talsemgeest on 2008-02-21
Try changing your fonts. Go to system>preferences>appearance and customize. Change the font and see what happens

---

### Post by toasty_ghosty on 2008-02-21
I tried to change the font, but it still displays the little boxes.

---

### Post by talsemgeest on 2008-02-21
Have you tried reinstalling openoffice.org?

---

### Post by toasty_ghosty on 2008-02-21
Yes. I have reinstalled openoffice-writer and nothing seems to have improved. Also, it is not just in writer, but all the openoffice applications. (presentation, database etc)

---

### Post by stchman on 2008-02-21
> **toasty_ghosty said:**
> Yes. I have reinstalled openoffice-writer and nothing seems to have improved. Also, it is not just in writer, but all the openoffice applications. (presentation, database etc)

No completely uninstall OO.  To do it use this in a terminal:

```
sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

Once that is done remove the residual config in Synaptic and remove your ~/.openoffice folder in your home directory.

To reinstall do this in a terminal:

```
sudo apt-get -y install openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer
```

That should do it.

---

### Post by toasty_ghosty on 2008-02-21
I wish that would fix it. It is still displayed like the screenshot. Wow, this is a pain.

---

### Post by spiderbatdad on 2008-02-21
seems like I had a similar occurrence after a failed attempt at loading a gfx card driver.

---

### Post by toasty_ghosty on 2008-02-21
I don't think that is the issue as I have working 3d rendering and everything seems fine. I'm glad that I know Openoffice well enough to still use it. I would like to be able to read the menus though.

---

### Post by spiderbatdad on 2008-02-21
hmmm. that struck a chord. something wrong in a gtk init.script...or are you using a custom gtk-2.0
at any rate there is a gtk config for OO. I would think the problem is there.
You might reinstall via this package by clicking on it.
.
.
.
.
.
.
.

---

### Post by teeleef on 2008-02-21
I saw that today on my daughters pc.  Her boyfriend has a login and he altered his desktop and application fonts to bold.....I forget the typeface.  I changed the application font to bitstream vera sans and all was well.




teeleef

---

### Post by toasty_ghosty on 2008-02-21
THANKS! It was the font. I changed it back and all was well.

---

