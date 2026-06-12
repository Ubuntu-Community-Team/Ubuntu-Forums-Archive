---
title: "please help me"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by yellowpagesguy on 2007-05-20
my laptop is dead

[http://farm1.static.flickr.com/197/493753091_aaf2f5a249.jpg?v=0](http://farm1.static.flickr.com/197/493753091_aaf2f5a249.jpg?v=0)

---

### Post by starcraft.man on 2007-05-20
Ummmm, you have to give us more information then that. Did this spontaneously happen after you rebooted once you completed your install? Did you modify something in particular right before you crashed your xserver? Was it maybe your graphical drivers you were installing? If so, then all you need to do is run this command in the console it should pop up when it shunts you to the text login.

```
sudo dpkg-reconfigure xserver-xorg
```

Then just select ok, or accept the default for any options till you get to the graphic driver section, pick the vesa drivers (or alternatively, nv if your using nvidia card) and then keep going, and then reboot.

If ya weren't installing drivers, please be a lot more specific as to what you modified...

---

### Post by yellowpagesguy on 2007-05-20
Did this spontaneously happen after you rebooted once you completed your install?


yes i installed beryl :(

---

### Post by yellowpagesguy on 2007-05-20
ok its gettin there what shall i type for generic video card?

---

### Post by seshomaru samma on 2007-05-20
what video card do you have?

---

### Post by starcraft.man on 2007-05-20
> **yellowpagesguy said:**
> ok its gettin there what shall i type for generic video card?

"nv" is the 2d generic one for Nvidia cards, if you have anything else I think you want "vesa". I don't think theres a 2d ati driver, I could be wrong someone correct me if I am...

---

