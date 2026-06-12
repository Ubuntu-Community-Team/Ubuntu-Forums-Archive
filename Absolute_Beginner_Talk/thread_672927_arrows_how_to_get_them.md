---
title: "arrows how to get them ?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by kikili on 2008-01-20
hi
i'm not only an absolute absolute beginner, but not english speaker at all
so excue-me for both things
i tried to find an answer in the ubuntu french forum but no answer that i can use, so i try with the english one
i was a very basic customer of windows (@mails and texts), no any knowledge of computing, but because my keyboard became crazy, i had to install ubuntu (1 week ago, very fresh !), and "kill" the keyboard, at least in linux, with the help of a man on the french forum, and modifying a piece of xorg.conf (the keyboard is still crazy on windows)
as i write texts, i need the arrows (up, down, left, right), but they don't work
i tried absolutely everything in the graphic session, but no way to have those arrows
i suppose i have to make a command line (excuse me : not only i don't know the vocabulary of computing, but i don't know the translations.... so i try to be the clearest possible !!), but i don't know how, and what to say (ok, i know already how to open the terminal, how to reconfigure completely ubuntu, how to spend HOURS to re-open a normal session, how to change a part of xorg.conf)
i already read everything there is on this forum, but nothing i can or use or understand !
i'm french and italian speaker
does somebody can help me ?
thank you

---

### Post by frup on 2008-01-20
Have you been able to try another keyboard and see if that works or has problems too?

---

### Post by mali2297 on 2008-01-20
Do you mean that you cannot use the arrow keys for navigation?

..or that you cannot get the special characters &#8592;&#8595;&#8593;&#8594; to show in the text?

---

### Post by The Cog on 2008-01-20
For the keyboard arrows to not work is very unusual - I have never heard of it before. If the keyboard is also crazy on Windows, I think maybe the keyboard is faulty and you should try another keyboard.

---

### Post by kikili on 2008-01-20
hello
it's a laptop, the keyboard of the laptop is "dead" on ubuntu and i use an external usb keyboard
this external keyboard is ok under windows (but i cannot use windows)
to #3 : i want to use them for navigation, because i correct texts, and with the mouse it's  less easy than with the navigation arrows
on the french forum i read a lot of posts from people with problems with keys, often no crtl and alt keys, so i wrote some posts to ask for help or at least for explanation, but till now, answers or not usefull or not for...absolute beginner !
i'm still looking for those arrows...

---

### Post by mali2297 on 2008-01-20
There is a program called **xev** that can be useful. You might need to install it from the package manager Synaptic (or apt-get). 

Open a terminal and type
```

xev

```
A window will pop up. Move the cursor to the window and press the left arrow key on your keyboard. Watch at the same time the output in the terminal. I get the following:
> 
KeyPress event, serial 26, synthetic NO, window 0x1800001,
    root 0x4d, subw 0x0, time 29589445, (101,139), root:(102,158),
    state 0x0, [COLOR="Red"]keycode 100 (keysym 0xff51, Left)[/COLOR], same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

What do you get instead of the line that I have highlighted in red? (If anything.)

Also, check this ["bug" report]("https://bugs.launchpad.net/ubuntu/+bug/115702"). Can it be as simple as this?
> 
Discovery: Scroll lock and numlock must be OFF for arrow keys and PGUP PGDN Del Home and End keys to work.


---

### Post by kikili on 2008-01-20
hello mali
i didn't understand what to do 1st : install it or go to a terminal to command xev
anyway, i opened a terminal and wrote
xev
and i get a long long list, which i give under a tiny piece :


VisibilityNotify event, serial 19, synthetic NO, window 0x3a00001,
    state VisibilityUnobscured

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (0,68), width 178, height 110, count 0

FocusIn event, serial 19, synthetic NO, window 0x3a00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 19, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

but may be i did wrong : have i to type
apt-get xev ?
anyway, thanks for your help

---

### Post by kikili on 2008-01-20
ok, i had not understood in the previous post, now i made the "right" thing with xev BUT it gives a long list in which there is informations about the key, but i'm not sure i copied the good informations, and the arrow up in fact opens the capture of an image, etc., so it has been VERY complicated to get what i got above (generaly, i typed in this order : arrow left, down, right, up)
i hope it's useful !
i sent it in pieces, because the mails administrator tells me i included 10 images in my message, but i included NOTHING, at least no image, i don't understand

KeyPress event, serial 28, synthetic NO, window 0x3a00001,

    root 0x56, subw 0x3a00002, time 2574805873, (38,34), root:(712,110),

    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,

    XKeysymToKeycode returns keycode: 64

    XLookupString gives 0 bytes: 

    XmbLookupString gives 0 bytes: 

    XFilterEvent returns: False



KeyRelease event, serial 31, synthetic NO, window 0x3a00001,

    root 0x56, subw 0x3a00002, time 2574805984, (38,34), root:(712,110),

    state 0x80, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,

    XKeysymToKeycode returns keycode: 64

    XLookupString gives 0 bytes: 

    XFilterEvent returns: False


KeyPress event, serial 31, synthetic NO, window 0x3a00001,

    root 0x56, subw 0x0, time 2574965314, (-177,292), root:(497,368),

    state 0x0, keycode 116 (keysym 0xffec, Super_R), same_screen YES,

    XLookupString gives 0 bytes: 

    XmbLookupString gives 0 bytes: 

    XFilterEvent returns: False

---

### Post by kikili on 2008-01-20
KeyRelease event, serial 31, synthetic NO, window 0x3a00001,

    root 0x56, subw 0x0, time 2574965402, (-177,292), root:(497,368),

    state 0x40, keycode 116 (keysym 0xffec, Super_R), same_screen YES,

    XLookupString gives 0 bytes: 

    XFilterEvent returns: False


KeyRelease event, serial 27, synthetic NO, window 0x4000001,

    root 0x56, subw 0x0, time 2575014143, (487,-36), root:(494,502),

    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,

"   XLookupString gives 1 bytes: (0d) "

    XFilterEvent returns: False



KeyPress event, serial 31, synthetic NO, window 0x4000001,

    root 0x56, subw 0x0, time 2575017653, (487,-36), root:(494,502),

    state 0x0, keycode 114 (keysym 0x0, NoSymbol), same_screen YES,

    XLookupString gives 0 bytes: 

    XmbLookupString gives 0 bytes: 

    XFilterEvent returns: False



KeyRelease event, serial 31, synthetic NO, window 0x4000001,

    root 0x56, subw 0x0, time 2575017797, (487,-36), root:(494,502),

    state 0x0, keycode 114 (keysym 0x0, NoSymbol), same_screen YES,

    XLookupString gives 0 bytes: 

    XFilterEvent returns: False


KeyRelease event, serial 23, synthetic NO, window 0x3a00001,

    root 0x56, subw 0x0, time 2575266499, (146,187), root:(820,263),

    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,

"   XLookupString gives 1 bytes: (0d) "

    XFilterEvent returns: False


KeymapNotify event, serial 21, synthetic NO, window 0x0,

    keys:  4294967207 0   0   0   16  0   0   0   0   0   0   0   0   0   0   0   

           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

---

### Post by mali2297 on 2008-01-20
> **kikili said:**
> hello mali
i didn't understand what to do 1st : install it or go to a terminal to command xev
anyway, i opened a terminal and wrote
xev
and i get a long long list, which i give under a tiny piece :


VisibilityNotify event, serial 19, synthetic NO, window 0x3a00001,
    state VisibilityUnobscured

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 19, synthetic NO, window 0x3a00001,
    (0,68), width 178, height 110, count 0

FocusIn event, serial 19, synthetic NO, window 0x3a00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 19, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

but may be i did wrong : have i to type
apt-get xev ?
anyway, thanks for your help

The program is working. Just move the cursor to the pop up window and press some keys. For example, if you press x, the terminal should output something like
> 
KeyPress event, serial 26, synthetic NO, window 0x1800001,
    root 0x4d, subw 0x0, time 44249052, (125,87), root:(126,106),
    state 0x0, keycode 53 (keysym 0x78, x), same_screen YES,
    XLookupString gives 1 bytes: (78) "x"
    XmbLookupString gives 1 bytes: (78) "x"
    XFilterEvent returns: False

Then press some of the keys that you have problems with , like the left arrow key.
You might not get a reaction at all, but there is a chance that you get some information about a keycode. The terminal will output quite a lot of things, try to extract the relevant part.

Did you check that Num Lock and Scroll Lock are off?

---

### Post by kikili on 2008-01-20
i understood the story of the images, it's the smileys !!!!!

---

### Post by mali2297 on 2008-01-20
> 
the arrow up in fact opens the capture of an image

This sounds like the experience of the person that I linked to.
Again, are you sure that Num Lock and Scroll Lock are off?

> 
.
.
keycode 36 (keysym 0xff0d, Return)
.
.
.
keycode 114 (keysym 0x0, NoSymbol)
.
.

Try to associate the keycode and keysym to each of the arrow keys that you press.
It seems like the keys are recognized but mapped wrong.

---

