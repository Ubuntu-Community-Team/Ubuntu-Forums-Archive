---
title: "[easy one] Importing a font"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2007-12-30
Ok right now I have Linux and Windows sharing a hard-drive. As time permits I'm moving the Windows stuff over to Linux.

I want my Ariel font. I type all my documents in it. The bosses EXPECT me to type in Ariel.

I grabbed the fonts from the FONT directory under Windows, and stuck them on a thumb drive. Now, how do I make Linux and Open Office use them?

......should add Linux understands that they are font files already but I'm not seeing how to put them to use.

---

### Post by Dr Small on 2007-12-30
In your home folder, make a new directory called:
```
.fonts
```

Copy the fonts into that directory, and then launch openoffice and you should be able to choose it ;)

Dr Small

---

### Post by jken146 on 2007-12-30
```
sudo aptitude install msttcorefonts
```
is probably the easiest way to get arial.

---

### Post by willie_wang on 2007-12-30
create a folder in your home folder called .fonts

```
mkdir /home/yourusername/.fonts
```

then copy all those fonts on your thumb drive into your .fonts folder.

```
cp /media/thumbdrivename/yourfontfolder/* home/yourusername/.fonts/
```

restart x

ctrl-alt-backspace

hey presto :)

---

### Post by Epic Plecostomus on 2007-12-30
Ok, Jken146's method as I'll prob'ly need other MS fonts for work.   Filed both answers away for refrence though.  Thanks!

---

