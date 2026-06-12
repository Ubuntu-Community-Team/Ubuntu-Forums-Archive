---
title: "Shell problem"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by ~/Chromekaldra/~ on 2007-12-15
Yeah, i'm trying to install an ATI video card. There's a driver for it which i ddl, which is a .run (in properties it says shell) and i also have an file called, "ati-packager.sh"

From what i gathered in the 20 plus sites i visited to resolve the issue, i came across this format code,

' sh <shell file name> ' sh being the command; got nothing.

ddl click and stuff doesn't work, don't really konw how to deal with a shell file nor a .run file. 

Oh, and i can't have my card in since when it's plugged in i get a black screen and DOS like state (whatever it's called for Linux...) 

I run Ubuntu Gusty 7.10, the driver (from ATI's site) apparently covers it...the card is ATI Radeon 2600 PCI. Some have solved their problems with similair cards but not the same issue as me. 

Hope you guys are willing to help?

---

### Post by taurus on 2007-12-15
Assuming you have saved it to ~/Desktop,

```
cd ~/Desktop
sudo sh ./ati-packager.sh
```

---

### Post by ~/Chromekaldra/~ on 2007-12-15
I got this: 

```

./ati-packager.sh: 9: ./ati-packager-helper.sh: not found
./ati-packager.sh: 10: ./ati-packager-helper.sh: not found
./ati-packager.sh: 10: ./ati-packager-helper.sh: not found
: unsupported option passed by ati-installer.sh

```

*EDIT*

tried it with the other file, the one with .run and it worked. Now i'm going to see if my ATI card will work once plugged in. I might be back :P

Many thanks Taurus! :D

---

### Post by Dr Small on 2007-12-15
Apparently it is missing the file "ati-package-helper.sh".

Dr Small

---

### Post by ~/Chromekaldra/~ on 2007-12-15
Alright, i don't get the black screen anymore now that something has changed. The restricted drivers manager shows that it is enabled but not in use. That i'd like to change. It also says to run 'aticonfig' which i did but it does nothing. I remember vaguely from my early searches this moring code that went something like:

```

aticonfig initial-f

```

But i think i'm missing something in that line. HOWEVER, it does return a non '~ doesn't exist' response, it gives me,

```

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

```

Basically, how do i "use" this graphics card? 

Oh, and tampering with my graphics stuff turns my screen funny, lots of pixel block green scattered everywhere, in globs, tends to stick to an off shade black (so where there was black there's green.)

---

### Post by ~/Chromekaldra/~ on 2007-12-18
I know there's dozens of others out there that desperately need help too, but just wondering if i'm too far in the page numbers to get noticed...really don't want to bug a mod...

and sorry for the dbl post, but i was hoping it'd get me noticed, even at the expense of any help...

---

