---
title: "Trouble with desktop effects"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by xXsupern00bXx on 2007-05-29
I am getting an error saying "The Composite extension is not available". Also before that I would get the whitescreen whenever i tired to enable the effects. 
I'm useing a x1900 to and having trouble getting drivers for it..First time useing Ubuntu for an OS.

---

### Post by DJ Wings on 2007-05-29
Post the results of a "glxinfo" command.
EDIT: Commands are launched from Applications > Accessories > Terminal.

---

### Post by xXsupern00bXx on 2007-05-29
[IMG]http://i137.photobucket.com/albums/q221/xXsupern00bXx/Screenshot-supern00bsupern00b-deskt.png[/IMG]

---

### Post by bone43 on 2007-05-29
> **xXsupern00bXx said:**
> I am getting an error saying "The Composite extension is not available". Also before that I would get the whitescreen whenever i tired to enable the effects. 
I'm useing a x1900 to and having trouble getting drivers for it..First time useing Ubuntu for an OS.


Ati does support your card on linux...


[http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=26907)

you need to use beryl 2.0 "older version" and XGL you can also use compiz "desktop effects" but beryl is way better IMHO but be warned its a bit tricky i suggest NOT starting beryl at log in but instead thru your menu after you are on your desktop.


go here for that I used the close source method..

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/EyeCandy](http://ubuntuguide.org/wiki/Ubuntu:Feisty/EyeCandy)

or here...

[http://www.linuxquestions.org/questions/showthread.php?t=555247](http://www.linuxquestions.org/questions/showthread.php?t=555247)

Good luck

---

### Post by DJ Wings on 2007-05-29
Use this command:
```
sudo nano /etc/X11/xorg.conf
```
Mind the case, you can copy and paste. Then, find the "Modules" section and add this:
```
Load dri
```
to it. Finally, reboot.
EDIT: Your mileage may vary. If it's already in there, don't add it, and follow ^'s advice.

---

### Post by xXsupern00bXx on 2007-05-29
OK I will try this real fast and see if i can get it to work. Thanks
*edit* works perfect now thanks

---

