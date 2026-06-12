---
title: "iconpackage files"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Duncan_Idaho on 2006-09-07
the other day I downloaded a icon theme for use in E17 for it were so cool
but when I downloaded it, I found that inside the .zip it were an .iconpackage file, I dont' know what to do with it, I can't extract it nor open it with wine, how can I use them?
and what is an iconpackage file? is a windoze-only thing? :confused:

---

### Post by jordanmthomas on 2006-09-07
If I'm not mistaken, an iconpackage extension is for Stardock's IconPackager.  (or maybe it is ip?)

A good thing to try is to rename it to be* filename.zip* and see if you can get the icons out.  If it is indeed a Stardock thing, all their files are just renamed zip files.

Hope that helped some.

---

### Post by Duncan_Idaho on 2006-09-07
> **jordanmthomas said:**
> If I'm not mistaken, an iconpackage extension is for Stardock's IconPackager.  (or maybe it is ip?)

A good thing to try is to rename it to be* filename.zip* and see if you can get the icons out.  If it is indeed a Stardock thing, all their files are just renamed zip files.

Hope that helped some.

well, I tried it with, but it doesn't work
it says that it isn't a valid zip file
I'm gonna try with a rar

EDIT: rar won't work either :(

---

### Post by jordanmthomas on 2006-09-07
Where did you get the file?  Maybe I can hunt one down and try to get it open.

---

### Post by Duncan_Idaho on 2006-09-08
> **jordanmthomas said:**
> Where did you get the file?  Maybe I can hunt one down and try to get it open.

thank you, I downloaded it from [here]("http://www.customize.org/details/46759")
those are the icons I wanna use :-?

---

### Post by jordanmthomas on 2006-09-08
OK, I'll see what I can do.
**edit**
by the way, those would be AWESOME for e17

---

### Post by jordanmthomas on 2006-09-08
I'm sure I'm probably not supposed to do this, but I did anyway.
[here]("http://jordanmthomas.googlepages.com/SystemForceJapan.tar.bz2") is an extracted version of your file.  Turns out, the icl is where the icons were.  

I downloaded some shareware program for Windows that could extract icons from icl files and installed it in wine.  Then, I extracted them and tarred them up for you.  

I'm not sure what you'll need to do to convert the icons into a format e17 will be able to use.  Right now, they are .ico files.  (I know they can be converted though, because "back in the day" I used to do some skinning and I've used such software)

Enjoy!

---

### Post by Duncan_Idaho on 2006-09-08
I thank you SOOOO much man!!!
I thought i'll never be able to use those :cry: 
as for using the icons in E17, I found that for using custom icons in entagle first you have to make an eap
```

The easy way to make an eap is to
1) Start the program you want to create an eap
for from the command line. 

2) Right-click on the icon in the top left corner of the program and choose "create icon"

3) Give the eap an icon that is in .png format
a)make a new one using gimp if necessary
b)icons are often found in /usr/share/icons or /usr/share/pixmaps however you can use an icon from any location
since the icon will be embedded in the eap after it is created

4) If the program must be run as root add "gksu -u root"
before the command so for and eap for synaptic it would look like "gksu -u root synaptic" without the quotes

5) Click apply.


```

thanks again, and hope this might be useful

---

