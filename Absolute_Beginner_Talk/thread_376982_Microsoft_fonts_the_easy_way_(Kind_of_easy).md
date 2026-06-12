---
title: "Microsoft fonts the easy way (Kind of easy)"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by icelechi on 2007-03-05
Hi,
I am still kind of getting used to Linux so maybe everyone already knows this but here goes...
I noticed that if you want to get the windows true type fonts (Times New Roman, Comic Sans,...), and you still have a windows partition, you can simply go into the Windows folder and copy the Fonts folder to your desktop or somewhere else that is accessible. You can then make a folder called .fonts in your home directory ( /home/your_user_name) and copy all the files that end with .ttf from the Fonts folder. And Bob's your uncle.:biggrin:

I just thought it was cool anyhoo. Let me know if this was useful
thanks

---

### Post by mikewhatever on 2007-03-05
Nice if works. Just out of curiosity, where are fonts located in Windows XP?

---

### Post by kevmartin on 2007-03-05
Fonts in XP should be in the same place as all other Windows systems:
C:/windows/fonts

Cheers

---

### Post by kevmartin on 2007-03-05
> **icelechi said:**
> Hi,
I just thought it was cool anyhoo. Let me know if this was useful
thanks

It sure was useful - was exactly what I was looking for - I was getting worried I'd be losing my font collection, which I depend on a lot.

Thanks

---

### Post by ajax75 on 2007-03-08
**Fantastic**. It works
I'm new to Linux and have been trying to do this for sometime!

---

### Post by bgyorok on 2007-03-11
I owe you one!

---

### Post by PlatoDan on 2007-03-11
Thanks for the how to! :)

---

### Post by Najand on 2007-03-11
Well, you would need to run:
```

sudo fc-cache -f

```
after coopying them. There is a much more easier way to get the package "msttcorefonts" installed. To do so, just run:
```

sudo apt-get install msttcorefonts

```
Actually you need multiverse repository enabled in your /etc/apt/sources.list

---

### Post by konungursvia on 2007-03-11
I've got the fonts, but I can't for the life of me get the subpixel rendering as in windows. My x fonts, even ttf from ms, look kinda mediocre. Any ideas?

---

### Post by joeashcraft on 2007-04-04
try System > Preferences > Font.
Choose Subpixel Smoothing (LCDs)

is that what you're looking for?

---

### Post by craigmac on 2007-04-06
Najand, the sudo fc-cache -f was just what I was looking for. It is easy to copy the fonts to the right folder but you need to get the system to register them - thanks.

The msttcorefonts package doesn't contain Tahoma which is freely distributable by MS and it looks fabulous to my eyes as THE system font.

---

### Post by awiggin on 2007-04-12
Hey all,

I went through the trouble of getting the microsoft fonts and then bringing over Tahoma, but something went wrong.

The Tahoma font(s) look like wingdings.  They didn't transport properly or something.  I would really like to get this fixed because the fonts in ubuntu don't look so great.

I will also try the font smoothing (LCD) option to see if that helps.

That said, if I can't get Tahoma to work, what would you all suggest are some good fonts that are easy to read that might resemble Tahoma?  I tried Arial, which isn't bad but not great.

Thanks,
AWiggin

---

