---
title: "Saving screenshots as JPG"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by AFT on 2007-01-13
Ok so the keyboard shortcut to taking a screenshot is ALT+PrintScrn. Its the same as windows, BUT how can I save it as a JPG?

I used to be able to do this under windows by opening Microsoft Paint  > Paste > Save

---

### Post by taurus on 2007-01-13
Use Gimp to convert png to jpg.

---

### Post by AFT on 2007-01-13
How do I place the screenshot in GIMP if I do ALT + PrntScrn?

---

### Post by 23meg on 2007-01-13
Just drag and drop the PNG file on it.

---

### Post by raul_ on 2007-01-13
I though you could just change the extension in the dialog box...

---

### Post by 23meg on 2007-01-13
> **raul_ said:**
> I though you could just change the extension in the dialog box...
That will change just the extension, not the file format.

---

### Post by AFT on 2007-01-13
Let me again clarify if I may,

When I hit PrintScrn it opens a "Save ScreenShot" window
When I hit ALT + PrintScrn it doesn't look like anything has happened

How can I have ALT+PrntScrn behave like Prntscreen, without altering the keyboard shortcuts???

(i figured out that if I alter them then I get my desired result, but I would like to not use this workaround and actually have ALT+PRNSCRN a single window to a PNG file and PRNTSCRN capture the entire screen to a PNG file, then convert it to JPG if i have to.

---

### Post by Threbus5 on 2007-01-13
Hi,

Ubuntu has a screen capture utility (look through the accessory menu items).

I believe that utility allows defining the save location and format.

Take care

---

### Post by Pobega on 2007-01-13
> pobega@ackbar:~$ aptitude search scrot
i   scrot                                                                  - command line screen capture utility

You might want to install that. Then make your screenshot command: (For Alt+PrntScrn)

> scrot ~/screenshot.jpg

If you want to put a delay on it use -d, for example a delay of three seconds:

> scrot -d 3 ~/screenshot.jpg

---

### Post by raul_ on 2007-01-13
> **23meg said:**
> That will change just the extension, not the file format.

Yes, true. My bad

---

### Post by K.Mandla on 2007-01-13
If you're feeling adventurous, you can use scrot and imagemagick to do the same thing from a command line.

```
sudo aptitude install scrot imagemagick
```
When that's done ...

```
scrot -d 5 -c -q 100 -e 'convert scrot*.png screenshot.jpg'
```
The nice thing about this method is that you don't need the Gimp or XFCE's screenshot plugin or Gnome's screen capture stuff or. ... You get the idea. ;)

---

