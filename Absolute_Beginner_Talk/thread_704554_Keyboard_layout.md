---
title: "Keyboard layout"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by bachibusuc on 2008-02-22
Hi,

Im using ubuntu right now and I want to change the keyboard layout. I went on system/preferences/keyboard

I added lets say Canadian Multilangual and it just askes me if it's on default or not.

I want to be able to switch from US keyboard layout and canadian multilangual but seems that I can't...

Plus I'd like to switch with some kinds of shortcuts...is it possible???

Anyone???

---

### Post by drs305 on 2008-02-22
I have a way to do it but there might be an easier way. 

You can make shortcuts using the gconf-editor settings. You will need to know the name used for each keyboard. Once you have that, you can make a shortcut whose command line would look something like:

gconftool-2 --type string --set /desktop/gnome/peripherals/keyboard/kbd/layout "layout name"

You can open gconf-editor and drill down the menu using the path above starting at "desktop" to see what setting you would be changing with the above shortcut. 

The names would be from the Keyboard, Layoauts, Layout in the Keyboard Preferences tab  ( from Syst, Preferences, Keyboard, Layouts). 

Continued next post...

---

### Post by drs305 on 2008-02-22
Continued:

Background: Skip to next paragraph for the solution...  I was able to solve this with an input from mbsullivan in [http://ubuntuforums.org/showthread.php?p=4387482#post4387482](http://ubuntuforums.org/showthread.php?p=4387482#post4387482)  
I had been able to change from Canada Multilingual to english using the "us" script but couldn't get the other script to change from us to canada multilingual. The problem was with the Canada Multilingual designation "ca multix" which was separated by a tab (no spaces). I still can't find a way of directly entering a cut and paste "ca multix" entry into the gconf-editor gui, but by running the script below it works.

Disclaimer: Running these scripts in Gutsy 64-bit the changes take effect immediately, placing both the US default and Canada Multilingual keyboards in the layouts section of gconf and in Keyboard Preferences. I don't know how 'sticky' these settings are in relation to other system settings. Of note, I found the following discussion "Now some background info. The /desktop/gnome/peripherals/keyboard/kbd keys are not really used. Since v2.12 gnome automatically uses the system (/etc/X11/xorg.conf) kbd values. The checkbox &#8216;overrideSettings&#8217; doesnt have any affect whatsoever."  at [http://linuxtidbits.wordpress.com/2007/12/19/gconf-and-keyboard-warnings/](http://linuxtidbits.wordpress.com/2007/12/19/gconf-and-keyboard-warnings/)
I can confirm that running the gconf line below does NOT alter the xorg file settings. Nevertheless, the following scripts appear to work.  Let me know if it works for you!

The Solution:

The following scripts will place the US default and Canada Multilingual keyboards in the layouts section of gconf and in Keyboard Preferences.  Note there is a LAYOUT and a LAYOUTS section; this input goes into the LAYOUTS section. Keyboard response is based on which entry occurs first - i.e. if us is first in sequence the keyboard acts like US default. If 'ca multix' is first, that becomes the default. You can see how these scripts change things by opening 3 windows on the same desktop. Open one with System, Preferences, Keyboard, Layouts. The changes will appear in the Layout window. Open the second by running the following in terminal:
```
gconf-editor &
```
Open a third window with a terminal and run the following to change the keyboard layouts:

The overrideSettings box of the gconf-editor keyboard setup should be selected/checked.

You should be able to run the following scripts to change from one to the other:

Change priority from US to Canada Multilingual:
```
gconftool-2 --type list --list-type string --set /desktop/gnome/peripherals/keyboard/kbd/layouts ["`echo -e "ca\tmultix"`",us]
```
Change priority from Canada Multilingual to US:
```
gconftool-2 --type list --list-type string --set /desktop/gnome/peripherals/keyboard/kbd/layouts [us,"`echo -e "ca\tmultix"`"]
```

Now all you have to do is make a script, a shortcut for the script, and place it on your panel or desktop. If you don't know how to do that just ask.

Finally, if you are interested in making other changes via this method, and of the four keyboard blocks can be changed in a similar fashion. Note that the layout and model block entries contain only --type string
The layouts and options contain both --type list and --list-type string 
If you want other keyboard layouts, one way to do it is to enter the new layout via the System, Prefs, Keyboard, Layout option to see what the code is for the keyboard you want. Then just substitute the values into the strings above.

Let me know if it works for you!

---

### Post by bachibusuc on 2008-02-22
thank you, I' ll give it a try :)

---

