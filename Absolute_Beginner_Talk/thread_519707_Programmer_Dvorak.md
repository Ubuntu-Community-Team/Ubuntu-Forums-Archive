---
title: "Programmer Dvorak"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by wizardus13 on 2007-08-07
How do I get Programmer Dvorak keyboard layout to work in Ubuntu 7.04? On the website ([http://www.kaufmann.no/roland/dvorak/](http://www.kaufmann.no/roland/dvorak/)), they only have binaries for Red Hat and Debian linux, and the Debian link doesn't work. If I can't get the automatic installation to work, is there any way to make a custom layout?

---

### Post by Hospadar on 2007-08-07
you should be able to download the red hat binary and convert it to a deb with alien, then install that deb.  alternatively this configuration might already be installed and you just need to select it.  go to System-Preferences->Keyboard then go to the layout tab, and add a layout, this will give you a big list of layouts by language, I saw some dvorak layouts under US english, maybe this is close to your layout?

---

### Post by wizardus13 on 2007-08-07
I converted it to a deb package, but then it says that I need to:
su -c 'echo KEYTABLE="dvp" >> /etc/sysconfig/keyboard'

That directory does not exist, so is there a directory on Ubuntu that has the same purpose?

---

### Post by wizardus13 on 2007-08-07
Actually, I don't know if the package put the keyboard layout in the right place. It doesn't show up in System>preferences>keyboard>layout>add>US English.

---

### Post by wizardus13 on 2007-08-07
Is there any way to get the file to work? If there isn't, I'll just have to user regular dvorak... I couldn't find any other sites with programmer dvorak.

---

### Post by mezhaka on 2007-12-25
have you found the solution?

---

### Post by mbsullivan on 2008-01-21
*Bump*... any news?

---

### Post by sque on 2008-02-06
*Bump* I am interested on this too!

---

### Post by Trail on 2008-02-06
Edit: Nevermind, misunderstood

---

### Post by Dr Small on 2008-02-06
Here's how I did it:
```
setxkbmap dvorak &
```

---

### Post by seventhc on 2008-02-06
or get one of these and it works out of the box.
[http://www.typematrix.com/ezr2030/dvorak.html](http://www.typematrix.com/ezr2030/dvorak.html)
This is what I use, it types qwerty/dvorak which you switch between the two by a key combination <Fn-F3>

---

