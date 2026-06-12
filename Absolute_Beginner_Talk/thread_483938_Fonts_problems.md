---
title: "Fonts problems"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Anders J on 2007-06-25
I have read multiple postst about ttf font import and I do have my set located in home/my-name/.fonts.

I cannot figure out how to convince any software to use them.

But something else have gone completely wrong in this process, the fonts used in f inst Firefox and Thunderbird are now so small that it is difficult to use the computer at all. I have reset all fonts in System/Preferences/Font to 12 points, no difference

I could of course increase the text size in Firefox, but this makes the headers so ridicolously big that it looks weird.

Help anyone, is there any way to reset to the deafault settings, which I don't like but at least were possible?

---

### Post by DBStevens on 2007-06-25
You need to install those fonts using a font installer.

Which desktop do you use?

---

### Post by Anders J on 2007-06-25
Gnome, straight out of the ubuntu installation. 

But I did just copy the ttf files to a directory on my laptop and it worked like a charm directly and there are various posts stating that it is very simple, just copying the files.

---

### Post by cogadh on 2007-06-25
I just installed the msttcorefonts package and it corrected all my font problems:
```
sudo apt-get install msttcorefonts
```

---

### Post by Anders J on 2007-06-25
Thanks, looks decent now. 

But I still don't get why this was much so easier on the laptop, running the same OS and almost identical set-up?

---

### Post by DBStevens on 2007-06-25
Almost is fine for a game of gernades, but not computers.

The apt-get install would do what the font installer would do.

---

