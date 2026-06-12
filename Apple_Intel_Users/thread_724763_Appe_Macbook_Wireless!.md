---
title: "Appe Macbook Wireless!"
date: 2008-03-14
forum: Apple Intel Users
---

### Post by JohnRowley on 2008-03-14
This may or may not be in the correct Category, and i wholy apologize if it isnt. However the problem is, i recently switched to Ubuntu from Leopard, had a few niggles getting Wireless sorted, but thats not the problem. Im capable of scanning for devices, ive found my device and inputted the key. However it doesn't work. I get the Server not found screen in Firefox! Any help would be appreciated! Look forward to getting this sorted and seeing what the os can do :P

Edit: Ok, its now saying looknig up [www.google.com](www.google.com), yet the cursor just keeps spinning

Edit2: By the way, so's not to make another thread, If someone could tell me how to change the keys to fit the 'mac' keyboard id be greatfull :)

---

### Post by aongenae on 2008-03-16
> **JohnRowley said:**
> 
Edit2: By the way, so's not to make another thread, If someone could tell me how to change the keys to fit the 'mac' keyboard id be greatfull :)

You have to replace, in /etc/X11/xkb/rules/base, “badmap” by “goodmap” in the following line:

```
$macbooks      =       macintosh+macintosh(badmap)
```
become
```
$macbooks      =       macintosh+macintosh(goodmap)
```

The default lv3 switch is «enter switch», to the right of the right Appel key. If you want to use the two Apple keys as switch, you should replace "enter_switch" by "win_switch" in the following line:

```
$maclaptop    =       +inet(apple)+level3(enter_switch)
```
become
```
$maclaptop    =       +inet(apple)+level3(win_switch)
```

And your xorg.conf keyboard section should look like:

```
Section "InputDevice"

Identifier      "Generic Keyboard"

Driver          "kbd"

Option          "CoreKeyboard"

Option          "XkbRules"      "xorg"

Option          "XkbModel"      "macbook79"

Option          "XkbLayout"     "fr"

EndSection
```


Reload X, and enjoy!

*note*: it is not exactly the same as it's under osX, for the special key, like " [ " 
under macosx, you do this:            [alt]+[shift]+(
under ubuntu, you have to do this:  [appleKey]+[shift]+(
but it's quite the same...

*note*: As you have noticed, it's the way for a belgian or french keyboard, you can try to change the "XkbLayout" value by your country... tell us if it worked

*note*: It works as well for a Macbook Pro... (**without** changing macbook to macbook pro !!!)

---

