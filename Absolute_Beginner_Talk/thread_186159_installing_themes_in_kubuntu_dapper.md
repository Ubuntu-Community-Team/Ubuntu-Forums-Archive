---
title: "installing themes in kubuntu dapper"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-06-01
Hi

How do I install kde themes in kubuntu dapper?

---

### Post by murph2481 on 2006-06-01
check out [http://www.kde-look.org](http://www.kde-look.org) and get the theme that you want.  Then download the file.  Do not unzip it.  Then open up the Appearance tab and click install and browse to the file you just downloaded.

---

### Post by mrvgarg on 2006-06-01
I can not find any install buttons...

---

### Post by ComplexNumber on 2006-06-01
[quote=mrvgarg]Hi

How do I install kde themes in kubuntu dapper?[/quote] theming kde can be a rather painful and difficult affair. the themes are what you will see in theme manager themes section of kcontrol. there will be an install button there. HOWEVER, those themes are made up of various componenets(eg icons, style, colour scheme, win decs, wallpaer, etc) that may or *may not* be already present on your system. if they aren't already present on your system, the theme will default to whichever is current. for example, if a particular theme uses the reinhardt icons and they aren't on your system, when you activate the theme, the icons won't change at all. 
if you have a look at kde-look, it sometimes says what theme components are necessary to make up the theme. if you want the full theme, you will have to install theme seperately....and thats when the fun often begins. many of the theme components require compiling from source, so extract the tarball, then do the usual ./configure....make...make install. and good luck.

btw the file that you need for the theme manager theme is the kth file, so thats the one you want to select when installing a theme.

---

### Post by mrvgarg on 2006-06-01
Yeh its a kth file. On breezy there was a settings button on the system menu but its missing in dapper.

---

### Post by ComplexNumber on 2006-06-01
[quote=mrvgarg]Yeh its a kth file. On breezy there was a settings button on the system menu but its missing in dapper.[/quote]
what happens when you double click it (if you've got kde in the illogical single click mode, click it once)?

---

### Post by mrvgarg on 2006-06-01
nothing happens...it keep saying install kde theme loading appliaction and nothing happens.

---

### Post by ComplexNumber on 2006-06-01
[quote=mrvgarg]nothing happens...it keep saying install kde theme loading appliaction and nothing happens.[/quote]
it will do. maybe you have a slow system. believe it or not, it is actually installing if thats what it says.

---

### Post by mrvgarg on 2006-06-01
I have an amd3000xp....And I am not sure how to check if it is installed or not cos the settings is missing from systems menu...

---

### Post by ComplexNumber on 2006-06-01
[quote=mrvgarg]I have an amd3000xp....And I am not sure how to check if it is installed or not cos the settings is missing from systems menu...[/quote] just wait about an hour and then check to see if it shows up in theme manager themes :p.

btw what setting?

---

### Post by mrvgarg on 2006-06-01
umm I cant find theme manager...

---

### Post by Horizon on 2006-06-03
[QUOTE=mrvgarg]umm I cant find theme manager...[/QUOTE]
Try launching a konsole and typing ```
sudo kcontrol
```It should be pretty easy to find from there...at least I think, I'm not a kde user >.>

---

### Post by mrvgarg on 2006-06-03
I managed to find it by Adding to panel menu > Add Applet to Menu and selecting settings. :-D

---

