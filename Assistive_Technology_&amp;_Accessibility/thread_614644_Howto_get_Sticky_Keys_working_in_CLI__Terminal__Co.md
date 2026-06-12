---
title: "Howto get Sticky Keys working in CLI / Terminal / Console / tty#"
date: 2007-11-16
forum: Assistive Technology &amp; Accessibility
---

### Post by Firestone on 2007-11-16
I have always found it annoying to work in the CLI because of the lack of some kind of sticky keys feature. However; I've recently found a way to enable a crude, but effective, way of enabling them.

Step I:
Get the program 'xkeycaps' using 
```
sudo apt-get install xkeycaps
```

This program will enable you to easily check the keycode of certain keys on your keyboard.

Step II:
After selecting the type of keyboard you have, you can read the keycode by selecting the key. The 3rd number from the left is the one you need.
Now write down the keycodes of the left shift, left ctrl, left alt, right shift and right crtl. The right alt can be used for other functions, which we disable if we change it, so we won't.

Here is an example of my Logitech UltraX keyboard(US-alt):
```
LCtrl = 29 
LShift =  42 
LAlt = 56
RShift = 54 
RCtrl = 97 
```

You can now close xkeycaps.

Step III:
Next; run the command:
```
sudo dumpkeys | head -1
```
This will give you something like 
```
keymaps 0-63
```

Write the output and the keycodes in a new file:
```
keymaps 0-63
keycode 29 = SCtrl
keycode 42 = SShift
keycode 56 = SAlt
keycode 54 = SShift
keycode 97 = SCtrl
```
The function after the keycodes enable the sticky keys function on those keys.
Now save the file with a good name like customkeys.

Step IV:
Load your file by entering:
```
sudo loadkeys <file>
```

You can now test it by going to the CLI(alt - ctrl - F1), and type some stuff. The sticky alt and ctrl can be tested to go back to X(alt - ctrl - F7). 
**Note that when you've entered the wrong keycodes in your file, that you may not be able to return to X. So if you can't press multiple keys by yourself, better wait. Still, a reboot will always reset it.** 

Step V:
If you are sure that the keys work fine, you can make it permanent change by editing rc.local:
```
sudo gedit /etc/rc.local
```

The resulting file should look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

loadkeys <file>
exit 0
```

You're done! If you kill your Xserver the next time, you can at least try to fix it :)


Note: I have not thought of this method by myself, but combined it from info I found on a few sites.

---

