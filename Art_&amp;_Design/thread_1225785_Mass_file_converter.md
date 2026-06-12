---
title: "Mass file converter?"
date: 2009-07-28
forum: Art &amp; Design
---

### Post by Heldrex on 2009-07-28
I have a 174 files in psd that I want converted over to jpg. I want to use them as a screensaver but the "pictures" option for the screensaver won't recognize .psd.

Is there a mass file converter that is open source? (preferably with a GUI since I am a novice in terminal.)

---

### Post by kaibob on 2009-07-29
Phatch has a GUI and will read PSD files:

[http://photobatch.wikidot.com/](http://photobatch.wikidot.com/)

I personally would use the mogrify command-line utility from the Imagemagick suite. To do this, open a terminal window and change to the directory that contains the image files. Then, enter the following:

```
mogrify -format jpg *.psd
```

I don't know if Imagemagick is installed by default. If not, it a small install that's in the repo's.

---

### Post by vinutux on 2009-07-29
I think nautilus image converter works for you ```
sudo apt-get install nautilus-image-converter
```

---

### Post by Dragonbite on 2009-07-29
Couldn't Gimp be scripted to do this?

---

### Post by binbash on 2009-07-30
Phatch can do this easily

---

### Post by vinutux on 2009-07-30
> **binbash said:**
> Phatch can do this easily

**Yeh..Phatch is really gr8 app...........**

```
sudo apt-get install phatch
```

**[COLOR="YellowGreen"]Homepage[/COLOR]** - **[http://photobatch.stani.be/download/index.html]("http://photobatch.stani.be/download/index.html")**

---

### Post by hessiess on 2009-07-31
ImageMagik

```

mogrify -format jpg *.psd

```

---

