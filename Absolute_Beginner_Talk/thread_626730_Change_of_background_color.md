---
title: "Change of background color"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-11-29
After having changed the theme color to blue in my computer I couldn't get rid of the peach color which pops after I log in I changed it thruogh system>administration>login window background color to blue when I first boot I have blue but after I log in I will have peach color any Idea how to change it.

---

### Post by civic_si on 2007-11-29
in the change background section. you can change the color below the area where you select the background image. just right click on the background and select "change desktop background" it will be at the bottom.

---

### Post by dimbulb1024 on 2007-11-29
I've had this issue with 7.10 from the start and can never get rid of the "peach" color no matter what I do. It always shows up after login and before my desktop image loads. I have the background in the login window and desktop both set to black. I think it may be a bug.

---

### Post by ShodanjoDM on 2007-11-29
Try this after you logged in:

```
$ sudo gedit /etc/gdm/PreSession/Default
```

find this line: 

```
BACKCOLOR="#dab082"
```

and change it to:

```
BACKCOLOR="#000000"
```

Save, logout and log in again.

---

### Post by civic_si on 2007-11-29
I usually change the color in both places and it never happens to me.

---

### Post by dimbulb1024 on 2007-11-29
ShodanjoDM - That worked for me. Thanks!

---

### Post by evilregis on 2007-11-29
System -> Administration -> Login Window -> Local tab

Below the theme listing you can select the background colour that will appear.  If it does not, try the following (this advice is safe [though not ideal] and found on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/132833")):

```
sudo gedit /etc/gdm/PreSession/Default
```

And change the following from:

```
# Default value
  if [ "x$BACKCOLOR" = "x" ]; then
  BACKCOLOR="#dab082"
  fi
```

to

```
# Default value
  if [ "x$BACKCOLOR" = "x" ]; then
  BACKCOLOR="x"
  fi
```

---

### Post by jmfa59 on 2007-11-29
ShodanjoDM thanks alot work fine.
Civic_Si
I tried everything I changed it from log in Windows and from background color  it didn't work untill I did what ShodanjoDM you need to change it in three places
Thanks all of you

---

