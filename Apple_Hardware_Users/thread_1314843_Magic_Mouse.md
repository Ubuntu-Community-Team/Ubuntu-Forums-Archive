---
title: "Magic Mouse"
date: 2009-11-04
forum: Apple Hardware Users
---

### Post by lunarcloud on 2009-11-04
I've got it connected (kbluetooth >> pair >> code 0000), but it has no scroll functions (or less importantly forward and backward).

Anyone stab at trying to figure how to add that functionality?

```
sam@sam-desktop:~$ xinput list
"Virtual core pointer"  id=0    [XPointer]
        Num_buttons is 32                 
        Num_axes is 2                     
        Mode is Relative                  
        Motion_buffer is 256              
        Axis 0 :                          
                Min_value is -1           
                Max_value is -1           
                Resolution is 0           
        Axis 1 :                          
                Min_value is -1           
                Max_value is -1           
                Resolution is 0           
"Virtual core keyboard" id=1    [XKeyboard]
        Num_keys is 248                    
        Min_keycode is 8
        Max_keycode is 255
"Apple, Inc Apple Keyboard"     id=2    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Power Button"  id=3    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Apple, Inc Apple Keyboard"     id=4    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Power Button"  id=5    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Macintosh mouse button emulation"      id=6    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"Apple Wireless Mouse"  id=7    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1

```

---

### Post by lael on 2009-12-07
Found some ruby code on github that might be useful for someone who wants to sort this out.  

[http://github.com/pedrofranceschi/MagicMouse]("http://github.com/pedrofranceschi/MagicMouse")

---

### Post by thinktyler on 2009-12-09
what version do you have?

I have karmic and I used bluetooth manager to pair with my mighty mouse and it worked perfectly! 

The OTB bluetooth did not work for me. You can find bluetooth manager in the Ubuntu Software channel. 

Hope this helps.

---

### Post by davim on 2010-01-26
check this out -> [https://help.ubuntu.com/community/AppleMagicMouse](https://help.ubuntu.com/community/AppleMagicMouse)

---

### Post by Jay2Cee on 2010-01-29
There is another discussion thread, too: [http://ubuntuforums.org/showthread.php?p=8732535](http://ubuntuforums.org/showthread.php?p=8732535)

---

### Post by davim on 2010-01-29
Could someone add the magic-mouse module and the patched kernel to the macintel PPA??

---

