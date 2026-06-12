---
title: "PLEASE HELP!!! Mapping Windows (Tux) Key to Menu"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by Goodson1974 on 2007-03-20
I'm completely stuck!

I'm trying to map my Tux key (windows key replacement on my Cherry Cymotion Master Linux keyboard!) so that it opens the Applications menu (I know that I'm currently able to do it with <Alt> F1, but my girlfriend suggested that i change things so that the Tux key does it!)

I've checked through posts on the forum but there doesn't seem to be anything about opening the application menu.

I tried changing it in System>Preferences>Keyboard Shortcuts, but when i pressed the Tux key in the 'Show the panel menu' section nothing happened.

I checked in xev to see if the key was doing anything and the following was output: -

> KeyRelease event, serial 29, synthetic NO, window 0x3000001,
    root 0x157, subw 0x0, time 1901693613, (511,189), root:521,286),
    state 0x50, keycode 115 (keysym 0xffe7, Meta_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
Can someone please help as i'm sure this must be a simple thing and i'm probably missing something completely obvious!

---

### Post by Falados on 2007-03-20
Sometimes it treats the Windows key as a modifier (Like ALT or SHIFT).  Are you sure you have selected the right keyboard layout?

Also check some of the files in
/etc/X11/xkb/keycodes/
Check for irregularities with <LWIN> <RWIN> and <MENU> which are the definitions of special keys for windows keyboards.

I've also seem to have found this page, it seems very old, but maybe the solutions are still relevant.
[https://bugs.launchpad.net/control-center/+bug/12153](https://bugs.launchpad.net/control-center/+bug/12153)

---

### Post by Goodson1974 on 2007-03-21
I've selected the right keyboard in System>Preferences>Keyboard, and in Keytouch.
Does this change the keyboard in X or should i re-run the X configuration or am i barking up the wrong tree?!
 
As a noob i'm a bit confused as to what needs to be changed where with keyboards.
 
I'll check out the link you suggested in your post and see if i can figure it out!

---

### Post by jvc26 on 2007-03-21
In beryl when setting up shortcuts it registers the Windows/Tux key as <SUPER> (a modifier key like <ALT> or <SHIFT>) Might that help?
Il

---

