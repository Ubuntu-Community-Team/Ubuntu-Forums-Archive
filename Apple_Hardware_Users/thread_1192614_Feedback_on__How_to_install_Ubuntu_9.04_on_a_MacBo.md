---
title: "Feedback on : How to install Ubuntu 9.04 on a MacBook"
date: 2009-06-20
forum: Apple Hardware Users
---

### Post by mabovo on 2009-06-20
Could You please add some additional configuration to other special keys like in portuguese or french keyboard using xmodmap command for a britsh MacBook ?

Xorg doesn't consider those needs for poorly users of Latin countries !   :)

---

### Post by mabovo on 2009-06-20
I found this wiki [https://help.ubuntu.com/community/MacBook4-1/Jaunty#Keyboard](https://help.ubuntu.com/community/MacBook4-1/Jaunty#Keyboard) that states:

```
Middle&Right Click with Left&Right Cmd Keys

After a fresh install of Intrepid (intrepid? This is a Jaunty document...), the middle mouse click is emulated on F11 and the right mouse click on F12. This has numerous disadvantages:

    * the fullscreen hotkey F11 for Firefox, F-Spot, etc. won't work
    * the keys F11 and F12 are hard to reach, when using the trackpad
    *

      the emulation service introduces a bug with the CapsLock key: the LED won't work 

To solve this, you can map

    * Mouse Middle Click to the left cmd key
    * Mouse Right Click to the right cmd key 

The other level chooser keys are mapped by default to:

    * ctrl = Control (used in Ctrl+c, Ctrl+v, Ctrl+x, etc.)
    * left alt key = Alt (used in Alt+Tab to change between windows for example)
    *

      right alt key = AltGr (3rd level chooser for keys like |, @, &#8364;, etc.) 
```

also in [https://help.ubuntu.com/community/AppleKeyboard#Corrections](https://help.ubuntu.com/community/AppleKeyboard#Corrections) says:

```
Ubuntu 9.04 (Jaunty Jakalope)

Since Xmodmap have been replace by X Keyboard Extension, it's impossible to use Xmodmap to proceed with the mapping. Configuration can be done using the Keyboard preference tool.
```

but for MacBook Air we have in [https://help.ubuntu.com/community/MacBookAir1-1/Intrepid?action=show&redirect=Macbook_Air#head-5fd0bcf04cc7da0b5241950916bab5d58cdb84da](https://help.ubuntu.com/community/MacBookAir1-1/Intrepid?action=show&redirect=Macbook_Air#head-5fd0bcf04cc7da0b5241950916bab5d58cdb84da) the following:
```
Several additional keyboard mapping changes might be needed depending on preferences. Here is one example that makes CapsLock a Control key, puts the Alt key on the left apple key, switches keyboard layout when pressing the left control key or by holding down the right apple key.

        Option          "XkbOptions"    "ctrl:nocaps,altwin:swap_lalt_lwin,grp:rwin_switch,grp:switch,grp:lctrl_toggle"
```

and additional configurations for belgian and canadian keyboards
```
Keyboard configurations

Macbook Air Keyboard Canadian Multilingual
https://help.ubuntu.com/community/Macbook%20Air%20Keyboard%20Canadian%20Multilingual
Macbook Air Keyboard Belgian Keyboard
https://help.ubuntu.com/community/Macbook%20Air%20Keyboard%20Belgian%20Keyboard
```

There are some keyboard problems related to Deutch and Spanish in these posts:
[http://ubuntuforums.org/showthread.php?t=1183661&highlight=xmodmap](http://ubuntuforums.org/showthread.php?t=1183661&highlight=xmodmap)
[http://ubuntuforums.org/showthread.php?t=1087671&highlight=xmodmap](http://ubuntuforums.org/showthread.php?t=1087671&highlight=xmodmap)

and bug reports on:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/337016](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/337016)
[https://bugs.edge.launchpad.net/mactel-support/+bug/214786](https://bugs.edge.launchpad.net/mactel-support/+bug/214786)

some interesting questions on:
[http://ubuntuforums.org/showthread.php?t=1083599&highlight=xmodmap](http://ubuntuforums.org/showthread.php?t=1083599&highlight=xmodmap)
[http://ubuntuforums.org/showthread.php?t=894396&highlight=xmodmap&page=2](http://ubuntuforums.org/showthread.php?t=894396&highlight=xmodmap&page=2)
[http://ubuntuforums.org/showthread.php?t=1054276&highlight=xmodmap](http://ubuntuforums.org/showthread.php?t=1054276&highlight=xmodmap)
[http://ubuntuforums.org/showthread.php?t=995303&highlight=xmodmap](http://ubuntuforums.org/showthread.php?t=995303&highlight=xmodmap)

and useful instructions on:
[http://ubuntuforums.org/showpost.php?p=5801976](http://ubuntuforums.org/showpost.php?p=5801976)
[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

but I am still lacking the information on "How to configure Applekeyboard layout for portuguese, german, spanish, french, etc" using a MacBook2,1 in Jaunty with kernel 2.6.30 ?


Thanks so much  !


bump ?

---

### Post by mabovo on 2009-06-20
I am really confused about keyboard configuration in Jaunty with 2.6.30 kernel. 

Is Jaunty using xmodmap by default or using another method in Xorg like xev or xbindkeys ? I noticed that with xmodmap the boot process takes more time to proceed.

The solutions presented in this How To is a workaround for alternative keyboard layouts ?

---

### Post by mabovo on 2009-06-20
Can't install xev.

Terminal prompt says it was replaced by x11-utils.

---

### Post by MrBadger on 2009-07-05
On another thread "Problem on MacBook 5,2" a problem is described in which the load process reports "Not Responding" after "Verify CD" or "Install" is selected. I am experiencing the same thing loading 9.04. So far I haven't seen any response there yet. Maybe this thread is watched more closely? 

Mark

---

