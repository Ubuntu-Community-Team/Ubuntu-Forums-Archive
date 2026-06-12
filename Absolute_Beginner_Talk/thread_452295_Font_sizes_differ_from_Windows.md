---
title: "Font sizes differ from Windows"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by eiolv on 2007-05-23
Why is Times New Roman size 12 bigger in OpenOffice on Linux than in Microsoft Word on Windows? When I open a .doc-document made in Word, I get far more pages and less words on each line. Are there some settings in OpenOffice that can be changed?

---

### Post by freesitebuilder on 2007-05-23
Tools >Options allows you to make changes - the "Open Office Writer" section allows you to set default fonts and sizes.

There's also info here: [http://www.openoffice.org/FAQs/fontguide.html](http://www.openoffice.org/FAQs/fontguide.html) 

The difference in sizes of fonts, toolbars, icons, and so on was the thing that I found strange at first. Now I'm used to the differences, I find XP odd. :)

My default font for Writer is Nimbus Roman No9 L, though I use Nimbus Sans for  a lot of my word processing.

---

### Post by Bronto on 2007-05-23
Is Times New Roman installed in your system ?
Open the font list in OpenOffice and look for it (scroll the list, don't trust OpenOffice, it shows the font name in the box even if it's not installed - kinda' stupid behaviour if you ask me).

---

### Post by byenary on 2007-05-23
You might want to play with a parameter Display Size in the monitor section of your /etc/X11/xorg.conf as well

---

### Post by eiolv on 2007-05-23
Times New Roman seemes not to be installed. Where do I find it? 

And, using a different font and size probably works fine as long as I only work on a single computer. However I have to bring my documents to school to print them, and there they only have XP and Word, so the best solution would be that the fonts and sizes works the same way...

---

### Post by Bronto on 2007-05-23
Open up a console and type:

```
sudo apt-get install msttcorefonts
```

When it's done type:

```
sudo fc-cache -f
```

---

### Post by eiolv on 2007-05-23
Installing the font helped a lot. Thanx

---

### Post by O-pos on 2007-06-02
> **eiolv said:**
> Installing the font helped a lot. Thanx

I had the same problem.

Now as I found solution, I would like to ask further question: what happens if I take the whole bunch of .ttf filees from windows fonts folder and copy them directly to ubuntu's fonts folder? theoretically, then there should no more problems with fonts compatibility. Is it possible? can it work?

---

### Post by caro on 2007-06-02
Bronto,

Thanks for the tip.  i've had Ubuntu for about 24 hours now and am loving it.

---

