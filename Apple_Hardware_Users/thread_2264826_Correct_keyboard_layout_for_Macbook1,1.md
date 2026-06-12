---
title: "Correct keyboard layout for Macbook1,1"
date: 2015-02-10
forum: Apple Hardware Users
---

### Post by Sigrid_Rhling on 2015-02-10
I am running Lubuntu 14.04.1 on a Macbook1,1 with a US keyboard layout. In this particular layout the SECTION/PLUSMINUS key is where the TILDE key is on most other keyboards, which is left of the 1 key and below ESC. The TILDE key on my keyboard is between the left SHIFT and the Z key. 

I have used **Keyboard Layout Handler** with the following settings:

Model: macbook78
Layout: us(mac) and de(mac)
Options: -option apple:badmap

(For model I also tried all the other Mac variants, but since I am now pretty sure that the problem does not lie there, I have settled on what I think is actually correct: macbook78.)

With this setup I have the correct layout, with the exception of those two swapped keys. After serious study of the xkb files, it appears that this is not a new problem and the option "apple:badmap" is offered to correct the swap. I used xev to make sure that the keys in question returned the appropriate keycodes, so I am fairly certain that "badmap" is the option I need. For good measure, I also tried "apple:goodmap" which has the opposite mapping to "badmap", just in case I had read the files wrong after all ... but no luck there either. 

After some more googling I tried setting the layout from the command line using 

```
$ setxkbmap -model macbook78 -layout "us(mac)" -option -option "apple:badmap" -v 10
Setting verbose level to 10
locale is C
Warning! Multiple definitions of keyboard model
         Using command line, ignoring X server
Warning! Multiple definitions of keyboard layout
         Using command line, ignoring X server
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      macbook78
layout:     us(mac)
options:    apple:badmap
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)+macintosh(badmap)
types:      complete+numpad(mac)
compat:     complete
symbols:    pc+us(mac)+inet(evdev)
geometry:   macintosh(macbook78)
```

Apparently setxkbmap is *trying* to include the badmap keycodes when building the keymap, but when I then print its setup, they are not there.

```
$ setxkbmap -print
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)"      };
        xkb_types     { include "complete+numpad(mac)"  };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us(mac)+inet(evdev)"        };
        xkb_geometry  { include "macintosh(macbook78)"  };
};
```

I just ran these commands again, to copy and paste into this post, and they suddenly worked. I got this output, note how the badmap keycodes are included:

     ```
$ setxkbmap -print
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)+macintosh(badmap)"      };
        xkb_types     { include "complete+numpad(mac)"  };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us(mac)+inet(evdev)"        };
        xkb_geometry  { include "macintosh(macbook78)"  };
};
```

I then remembered that I had removed **Keyboard Layout Handler** from the panel this morning. I added it to the panel again just now and now I'm back with the two keys swapped into the wrong places again! Anyone know what's happening? I would like to be able to swap between the DE and the US layout in the GUI. But it seems that if I want the two troublesome keys in the right places I cannot.

---

### Post by Sigrid_Rhling on 2015-02-14
I have managed to get the swapped keys sorted out by following these instructions ([source]("https://help.ubuntu.com/community/AppleKeyboard#Correcting_swapped_keys_and_wrong_keymaps_for_international_.28non-US.29_keyboards")):

> 1. Append the configuration line to the file /etc/modprobe.d/hid_apple.conf creating it if necessary:
```
$ echo options hid_apple iso_layout=0 | sudo tee -a /etc/modprobe.d/hid_apple.conf
```
2. Trigger copying the configuration into the initramfs bootfile.
```
$ sudo update-initramfs -u -k all
```
3. Optionally, reboot
```
$ sudo reboot
```

Also, by looking at the actual geometric layout of the keyboard models using *xkbprint*, I have figured out that my model is a *macbook79*.

However, I now can't get Keyboard Layout Handler to remember the layouts on reboot. Both **/etc/default/keyboard** and **Keyboard Layout Handler** are set exactly the same:
```
XKBMODEL="macbook79"
XKBLAYOUT="us,de"
XKBVARIANT="mac,mac"
XKBOPTIONS="grp:shift_caps_toggle,lv3:rwin_switch,terminate:ctrl_alt_bksp"
```

When I reboot, after login, **Keyboard Layout Handler** shows up in the panel with a US flag. When I hover over the flag, it says *English (US)*, which corresponds to XKBLAYOUT="us" and XKBVARIANT="", and **does not match** the *mac* variant I need. When I click on the flag I cannot switch to the *de* layout.  When I right-click on the flag and go into **Keyboard Layout Handler** settings, the correct settings (i.e. us(mac) and de(mac)) are all there! I don't understand why it is not using the settings and using *English (US)* as the layout instead.

I've fiddled with this for a while and it used to be that when this happened, making a change in the **Keyboard Layout Handler** settings, such as changing the model and closing the settings dialog, would prompt **Keyboard Layout Handler** to function properly, in that clicking on the flags would then switch between *English (Macintosh)* and *German (Macintosh)*. This no longer works either as of the last reboot, so now I am stuck with *English (US)*.

---

