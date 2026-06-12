---
title: "@-sign broken ubuntu karmic"
date: 2010-01-22
forum: Apple Hardware Users
---

### Post by tom4everitt on 2010-01-22
Hey, 

I have Ubuntu karmic installed on a Macbook Pro 1,1. I've done all available the updates. 

As usual after installing a new linux system on my mac I discovered that the  @-sign was not working. So I went to System->Preferences->Keyboard->Layout and chose right win key as third level chooser. The only place this had effect on was in the terminal, in all other apps this did not help at all. (I also tried the other alt-keys as third level choosers, but still the same). 


Does anyone experienced something similar with karmic? Any ideas on how to solve it are highly appreciated! 

Thanks

---

### Post by linuxopjemac on 2010-01-22
Did you choose the right keyboard layout as being a Macintosh US ?

---

### Post by tom4everitt on 2010-01-22
Well, its actually a swedish keyboard so I chose swedish. Choosing swedish macintosh doesn't reall seem to help.

Choosing US macintosh makes problems worse :)

---

### Post by linuxopjemac on 2010-01-22
I would add the @ key manually with xmodmap

[https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys)
[http://cweiske.de/howto/xmodmap/allinone.html](http://cweiske.de/howto/xmodmap/allinone.html)

---

### Post by linuxopjemac on 2010-01-22
You can maybe also try this:

> First create a file in your homedir called ".Xmodmap"
Add the following line to it:
add mod3 = Super_L
Activate this change by running "xmodmap ~/.Xmodmap"

Next, go to Preferences -> Keyboard -> Layout Options
Under "Third level choosers", select "Press any of Win-keys to choose 3rd level"

And tada, you can now press the right "apple" button together with (in my case) 2 and get the @ that was previously impossible to type
Btw I left the keyboard model at the default "Generic 105-key (Intl) PC", changing it to Macintosh broke everything (only numeric keys worked).

The next time you boot up, xmodmap will ask if you want to automatically load .Xmodmap, tell it to do so, and you're good to go.

Hope this helps someone 

---

### Post by tom4everitt on 2010-01-22
Okay good idea, I should look into to that. 

Do you know any good tutorial on this, otherwise I guess I'll just find one on google.

---

### Post by tom4everitt on 2010-01-22
> **linuxopjemac said:**
> You can maybe also try this:

Hmm, that didn't work at all :(

---

### Post by tom4everitt on 2010-01-22
So one question: 

Which key is it that I should map to what? Is it Super_L that's supposed to be my left windows key? and is mod3 the function it should perform?

---

### Post by linuxopjemac on 2010-01-22
Super_L is the "right Win key", in your case the right alt key?

what does 

```
xmodmap -pk
```

give you ?

---

### Post by tom4everitt on 2010-01-22
This is the output of xev when I'm pushing my right win key:

KeyPress event, serial 36, synthetic NO, window 0x3e00001,
    root 0x67, subw 0x0, time 3205395, (397,535), root:(1067,585),
    state 0x0, keycode 134 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by tom4everitt on 2010-01-22
This might be the problem, cause on my system my right alt works as enter, it gives me a new line. 

Before I always used right win (i.e the apple command key) as third level chooser, but since the latest ubuntu its like the system wants me to use right alt. Which is already in use as enter.

---

### Post by tom4everitt on 2010-01-22
This is the output of xmodmap -pk:

    134    	0xfe03 (ISO_Level3_Shift)	0x0000 (NoSymbol)	0xfe03 (ISO_Level3_Shift)	0x0000 (NoSymbol)	0xfe03 (ISO_Level3_Shift)	

for keycode 134 which seems to be my right win (see above).

---

### Post by linuxopjemac on 2010-01-22
try this

The command/apple keys on macs are recognized as "Super" or "Windows" shift by default. To make the right command key a ctrl key, save this in ~/.xmodmap file:

```
clear control
clear mod4

keycode 37 = Control_L
keycode 134 = Control_R
!### change 134 to 116 if using Ubuntu hardy, not 8.10 or later. ###
add control = Control_L Control_R

add mod4 = Super_L
```

Then run the command 
```
xmodmap ~/.xmodmap
```

from [https://help.ubuntu.com/community/AppleKeyboard#Mapping%20keys%20(Insert,%20Alt,%20Cmd,%20etc](https://help.ubuntu.com/community/AppleKeyboard#Mapping%20keys%20(Insert,%20Alt,%20Cmd,%20etc).)

---

### Post by tom4everitt on 2010-01-22
> **linuxopjemac said:**
> try this

The command/apple keys on macs are recognized as "Super" or "Windows" shift by default. To make the right command key a ctrl key, save this in ~/.xmodmap file:

```
clear control
clear mod4

keycode 37 = Control_L
keycode 134 = Control_R
!### change 134 to 116 if using Ubuntu hardy, not 8.10 or later. ###
add control = Control_L Control_R

add mod4 = Super_L
```

Then run the command 
```
xmodmap ~/.xmodmap
```

from [https://help.ubuntu.com/community/AppleKeyboard#Mapping%20keys%20(Insert,%20Alt,%20Cmd,%20etc](https://help.ubuntu.com/community/AppleKeyboard#Mapping%20keys%20(Insert,%20Alt,%20Cmd,%20etc).)


Thanks, that actually solved it. I needed to do one modification: 

I let my right alt key, that previously functioned as some sort of enter, be right control (so switched 134 to 104 above). 

So I don't see how it actually does anything to my right win key after that. I guess its simply that it clears mod4 and control and then resets them that does it some way... I feel my knowledge about xmodmap is way too small at the moment to really know what happened. 

Thanks a lot :)

---

### Post by linuxopjemac on 2010-01-22
I have to admit that I know very little of Xmodmap as well, it ain't easy at all...But great that it now works for you.

---

### Post by tom4everitt on 2010-01-22
Yeah, I'm glad I found the xev command. It lets you know what the number of the key just being pressed was, together with some other stuff. Very convenient :)

---

