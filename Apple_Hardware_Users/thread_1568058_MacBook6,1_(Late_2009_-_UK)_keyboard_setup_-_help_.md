---
title: "MacBook6,1 (Late 2009 - UK) keyboard setup - help please :-)"
date: 2010-09-04
forum: Apple Hardware Users
---

### Post by youbuntu on 2010-09-04
Hi guys. I have a late 2009 MacBook (MacBook6,1 - UK version) which has the tilde "~" key to the left of the "Z" key, on the lower left of the KB. I would like to know how I configure Lucid, so that this key is properly mapped, as at the moment, all it produces is "<" and ">".

Thank you :-)

---

### Post by youbuntu on 2010-09-05
No replies?... I thought you guys were experts! ;-) :P

---

### Post by davidryderuk on 2010-09-05
Hi,
This works for me:

1. Create a file at the location "~/.Xmodmap".

```
gedit ~/.Xmodmap
```

2. Add the following text to the file:

```
keycode 94=grave asciitilde grave asciitilde dead_grave dead_horn
keycode 49=section plusminus section plusminus section plusminus
```

3. Restart the computer. Ubuntu should offer to load the configuration file you just created, which will then swap over the two keys.

4. On the off-chance that Ubuntu fails to load the configuration file on subsequent boots (which happened to me) you can add the following as a startup application:

```
xmodmap /home/**username**/.Xmodmap
```

Note: I got most of this information from the link below.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786)

---

### Post by youbuntu on 2010-09-05
> **davidryderuk said:**
> Hi,
This works for me:

1. Create a file at the location "~/.Xmodmap".

```
gedit ~/.Xmodmap
```2. Add the following text to the file:

```
keycode 94=grave asciitilde grave asciitilde dead_grave dead_horn
keycode 49=section plusminus section plusminus section plusminus
```3. Restart the computer. Ubuntu should offer to load the configuration file you just created, which will then swap over the two keys.

4. On the off-chance that Ubuntu fails to load the configuration file on subsequent boots (which happened to me) you can add the following as a startup application:

```
xmodmap /home/**username**/.Xmodmap
```Note: I got most of this information from the link below.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/214786)


You, Sire, have just made my day, and saved me MUCH hassle!. Thankyou!!

Also, if you create the same file, but call it "Xmodmap" instead of the hidden ".Xmodmap" and put it in ```
/etc/X11
```, you can then tell it to launch, by adding it to:```
 /etc/X11/xinit/xinitrc
``` as shown below. This applies the remapping system-wide for ALL users, instead of having to create the .Xmodmap on a per-user basis:

Add this line to /etc/X11/xinit/xinitrc:

```

. /etc/X11/Xmodmap

```(Leave a space between the "." and the "/")

---

