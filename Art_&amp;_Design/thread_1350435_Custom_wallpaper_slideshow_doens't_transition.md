---
title: "Custom wallpaper slideshow doens't transition"
date: 2009-12-09
forum: Art &amp; Design
---

### Post by oedipuss on 2009-12-09
I'm trying to do a custom transitioning wallpaper, by editing the default cosmos wallpaper xml file. 

It looks something like this :
```

<background>
  <starttime>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime> 
  <static>
    <duration>10.0</duration>
    <file>PATH_TO_FILE_1</file>
  </static>
  <transition>
    <duration>10.0</duration>
    <from>PATH_TO_FILE_1</from>
    <to>PATH_TO_FILE_2</to>
  </transition> 
 <static>
    <duration>10.0</duration>
    <file>PATH_TO_FILE_2</file>
  </static>
  <transition>
    <duration>10.0</duration>
    <from>PATH_TO_FILE_2</from>
    <to>PATH_TO_FILE_1</to>
  </transition>  
</background>

```

It only works when the file is saved from a text editor.. If I hit the save button continuously, I guess gnome is forced to re-read it, and the wallpapers are changing every 10 seconds. If left alone, nothing happens at all. It will calculate the current point in the sequence, display it, and leave it like that. 
I tried it with <year> <month> and <day> at the starttime section, even with no starttime at all, but the behaviour is the same.

Am I doing something wrong?

---

### Post by oedipuss on 2009-12-09
I can't figure out why or when this stopped working ...
I can see the thumbnail transitioning in gnome-appearance, it updates itself when clicked, but only the thumbnail, not the background.


Is there a service I might have accidentally stopped, or some autostart entry I might have removed?

---

### Post by cubeist on 2009-12-09
> **oedipuss said:**
> I can't figure out why or when this stopped working ...
I can see the thumbnail transitioning in gnome-appearance, it updates itself when clicked, but only the thumbnail, not the background.


Is there a service I might have accidentally stopped, or some autostart entry I might have removed?

works for me

first open terminal
search for the cosmos 'controller' file
```
find /usr -name cosmos.xml
```
Wherever that file is, make a copy and edit it with the details of your pictures location... it's straight forward which fields need changing.

Next, (I think you have done this step) create a folder in /usr/share/backgrounds and place your pictures in it, then edit the background-1.xml file with the correct file names for <static> and <transition>

---

### Post by oedipuss on 2009-12-09
I tried editing the cosmos xml, changing only the durations to something more easy to see, but still nothing =(

---

### Post by cubeist on 2009-12-09
> **oedipuss said:**
> I tried editing the cosmos xml, changing only the durations to something more easy to see, but still nothing =(

yes, it only changed once for me as well... and it may have been when I saved the file

I'll keep working on it

---

### Post by oedipuss on 2009-12-10
Found a solution !
There's this bug report : [https://bugzilla.gnome.org/show_bug.cgi?id=601753](https://bugzilla.gnome.org/show_bug.cgi?id=601753)
After applying the patch, and rebuilding from source the package libgnome-desktop (easier than I thought, but I expect a future update will sort it out anyway) it all works =D

---

### Post by cubeist on 2009-12-10
> **oedipuss said:**
> Found a solution !
There's this bug report : [https://bugzilla.gnome.org/show_bug.cgi?id=601753](https://bugzilla.gnome.org/show_bug.cgi?id=601753)
After applying the patch, and rebuilding from source the package libgnome-desktop (easier than I thought, but I expect a future update will sort it out anyway) it all works =D

Thanks for the link, still doesn't work for me though.

Maybe I am doing something wrong.

first I copy the cosmos folder in /usr/share/backgrounds

then I copy over new images

next I edit the background-1.xml file with the proper file names

what am I missing!!

-- Update - Works now, just needed a restart...duh!

---

### Post by RockHero on 2010-01-14
I'm a complete noob with Ubuntu (installed it earlier this morning), but I had this same problem, and my problem wasn't what it appeared to be.

First, i changed the date to my current date, but didnt change the time. So just make sure that your date at the top of the file is set to an earlier date.

Second, the images were going to change, I just didnt know I had to wait 18minutes. Change the duration of 1700 (or whatever it was) to something more reasonable like 360 (which is 5minutes).

Outside of this...thats all I can think of

---

### Post by harzoglups on 2010-01-16
> **oedipuss said:**
> Found a solution !
There's this bug report : [https://bugzilla.gnome.org/show_bug.cgi?id=601753](https://bugzilla.gnome.org/show_bug.cgi?id=601753)
After applying the patch, and rebuilding from source the package libgnome-desktop (easier than I thought, but I expect a future update will sort it out anyway) it all works =D


Hello,

Oedipuss, could you please explain how you rebuilt libgnome-desktop? I difn't find any sources package for it :(.
Just a libgnome-desktop-devel package but it just installs the header files.

Thank you

---

### Post by harzoglups on 2010-01-16
I finally introduced myself to "apt-get source" :D
apt-get source libgnome-desktop-2-11
And everything is fine :popcorn:

---

