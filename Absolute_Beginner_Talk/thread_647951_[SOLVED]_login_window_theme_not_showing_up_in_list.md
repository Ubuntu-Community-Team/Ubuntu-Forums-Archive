---
title: "[SOLVED] login window theme not showing up in list"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by spiderbatdad on 2007-12-22
I have installed several themes by simply moving the necessary files into /usr/share/gdm/themes/newfolder. Recently i tried to build my own using my own .jpg and copying some .xml and .desktop programs. everything is executable and should work. But when I go to Login Window Preferences-->Local my theme is not there. I can't understand, as other themes with similar files do appear after being manually added to /usr/share/gdm/themes/newfolder. Could anyone help please?

ACK! posted to the desktop customization forum also...please remove from there.

---

### Post by blueridgedog on 2007-12-23
Can you post an ls -al /usr/share/gdm/themes ?

Coming from a windows background, sometimes I use spaces in file/folder names and that at times breaks things.

---

### Post by spiderbatdad on 2007-12-23
```
drwxr-xr-x 16 root    root    4096 2007-12-23 01:05 .
drwxr-xr-x  5 root    root    4096 2007-12-22 03:11 ..
drwxr-xr-x  2 private private 4096 2007-12-22 19:54 arch-underlight-blue
drwxr-xr-x  2 private private 4096 2007-12-22 19:54 arch-underlight-grey
drwxr-xr-x  2 private private 4096 2007-12-22 19:54 arch-underlight-red
drwxr-xr-x  2 private private 4096 2007-12-20 15:33 chin
drwxr-xr-x  2 root    root    4096 2007-12-22 03:11 circles
drwxr-xr-x  2 private private 4096 2007-12-22 22:22 DarkGno
drwxr-xr-x  2 root    root    4096 2007-12-22 03:11 happygnome
drwxr-xr-x  2 root    root    4096 2007-12-22 03:11 happygnome-list
drwxr-xr-x  2 private root    4096 2007-12-23 03:00 hot
drwxr-xr-x  2 private private 4096 2007-12-22 22:52 hot1
dr-xr-xr-x  2 private admin   4096 2007-12-23 02:42 hott
drwxr-xr-x  3 root    root    4096 2007-10-15 19:21 Human
drwxr-xr-x  2 root    root    4096 2007-10-15 19:21 HumanCircle
drwxr-xr-x  3 root    root    4096 2007-10-15 19:21 HumanList

``` 
DarkGno is the one i use now, from gnome-look,org. hot, or hott are ones I cant get to show up in the gdmsetup. They are the same except name. I thought hot might be too short. The .xml and .desktop are also identical between DarkGno and hot except I have changed the .png and .jpg references.

---

### Post by blueridgedog on 2007-12-23
Well, the permissions look right and the files names look sane.  What happens when you click "add" while on the local screen?

---

### Post by spiderbatdad on 2007-12-23
not much. the select theme archive window opens, and i can navigate to the directory, manually, but opening it (or any other) from that window shows nothing, including existing themes. Under local, all the other themes are present and selectable.

---

### Post by blueridgedog on 2007-12-23
Ok, I just did the same.  I copied Human (the entire directory) to HumanTest.  In the local screen I then had Human listed twice.  

I renamed the xml file inside HumanTest from Human.xml to HumanTest.xml and then it was not available on the local screen.

There must be a master list or index of themes someplace.

There is a hint of that here:

[http://ubuntuforums.org/archive/index.php/t-428189.html](http://ubuntuforums.org/archive/index.php/t-428189.html)

---

### Post by spiderbatdad on 2007-12-23
if i try to just drag and drop the .tar.gz into local theme window, it offers to install the package. I click yes and then get an error message: not a theme archive.

---

### Post by spiderbatdad on 2007-12-23
> **blueridgedog said:**
> Ok, I just did the same.  I copied Human (the entire directory) to HumanTest.  In the local screen I then had Human listed twice.  

I renamed the xml file inside HumanTest from Human.xml to HumanTest.xml and then it was not available on the local screen.

There must be a master list or index of themes someplace.

There is a hint of that here:

[http://ubuntuforums.org/archive/index.php/t-428189.html](http://ubuntuforums.org/archive/index.php/t-428189.html)

you might have to edit the greeter.desktop so that Greeter=HumanTest.xml

---

### Post by blueridgedog on 2007-12-23
There is some step you/we are missing, how about:

[http://www.jirka.org/gdm-documentation/x1454.html](http://www.jirka.org/gdm-documentation/x1454.html)

Also, see gdmthemetester:

[http://www.google.com/search?q=gdmthemetester&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enUS253US253&aq=t](http://www.google.com/search?q=gdmthemetester&sourceid=navclient-ff&ie=UTF-8&rlz=1B3GGGL_enUS253US253&aq=t)

---

### Post by spiderbatdad on 2007-12-23
finally got it. The greeter (i think, thanks to the link you sent) should be named GdmGreeterTheme.desktop. Then for some reason this theme (which was a copy, as you had tried earlier) was creating extra information in the .desktop file, including a version 1.0 which xml didnt like. after deleting that extra stuff a separate document was created. I could not open it, but was able to change it to executable. Then  it became viewable as xml type. BUT the theme is now available in the themes manager. Whew.

---

### Post by blueridgedog on 2007-12-23
Once you get it down pat, write a how-to.

---

### Post by spiderbatdad on 2007-12-23
How-to-Pirate XML Files and Copyrighted Images. :lolflag:   "For Educational Purposes Only"

---

