---
title: "Trouble mapping keys on MacBook with Dapper"
date: 2006-09-09
forum: Apple PPC Users
---

### Post by rscow on 2006-09-09
Hi, I've got a pretty smooth running Triple Boot setup on my MacBook, but I'm having trouble getting keys mapped so that I can use the right Apple and Enter keys for middle and right mouse click.  I would settle for just right mouse click with the right Apple/Command button.

Here is my xmodmap file:

keycode 115 = Alt_L Meta_L
add mod1 = Alt_L Meta_L

keycode 101 = F1
keycode 212 = F2
keycode 160 = F3
keycode 174 = F4
keycode 176 = F5
keycode 214 = F7
keycode 215 = F8
keycode 216 = F9
keycode 217 = F10

keycode 116 = Pointer_Button2
keycode 108 = Pointer_Button3

xkbset m


I have xbset and xmodmap in my System->Preferences->Sessions->Startup Programs file.

Yet, I still don't have any right or middle mouse click.

Anyone have more success with this?

Roger

---

### Post by hajk on 2006-09-10
I prefer putting xmodmap keycode commands and the call to xkbset in a single executable script, for example /usr/local/bin/keyboard, then putting this script in the Startup programmes. This avoids the problem of xkbset being run before the xmodmap lines...

The keycode lines in /usr/local/bin/keyboard should all be  of the form

```
xmodmap -e "keycode xxx = FUNCTION"
```

where xxx = the keycode, like 108
and FUNCTION = the key function, like Pointer_Button3, and the quotes are intentional.

The final line should then be

```
xkbset m
```

Make this file executable with "sudo chmod +x /usr/local/bin/keyboard".

This works for me... 

N.B. Key bindings are different in a Parallels VM, use "xev" to check.

---

### Post by rscow on 2006-09-10
Thanks, I'll try working it that way.  BTW, I have gotten the wireless working reliably, though is is tedious.  I log into Ubuntu.  Then I open Networking.  Then I deactivate ath0.  Then I reactivate ath0.  Then I sudo ifup ath0.  At this point, I'm up and it works great.  Must be a better way.  I suppose some kind of startup shell script might work, if I knew how to write one.  Also, I don't know how to do the timing for waiting for ath0 to be up, before running ifup.

Anyway, I'll try your script method of keymapping.

Thanks again for your help.

Roger

---

### Post by rscow on 2006-09-10
that worked great!  I am a right-clicking fool.  For the help of anyone else who wants to do this, here is my /usr/local/bin/keyboard file:

xmodmap -e "keycode 115 = Alt_L Meta_L"
add mod1 = Alt_L Meta_L

xmodmap -e "keycode 101 = F1"
xmodmap -e "keycode 212 = F2"
xmodmap -e "keycode 160 = F3"
xmodmap -e "keycode 174 = F4"
xmodmap -e "keycode 176 = F5"
xmodmap -e "keycode 214 = F7"
xmodmap -e "keycode 215 = F8"
xmodmap -e "keycode 216 = F9"
xmodmap -e "keycode 217 = F10"

#Make lower Enter key the right click...
xmodmap -e "keycode 108 = Pointer_Button3"

#Make lower Apple key the middle click...
xmodmap -e "keycode 115 = Pointer_Button2"

#...fix this for the mouse.
xkbset m


Now to figure out the trackpad scroll and tap functions

Roger

---

### Post by pcbroch on 2007-05-19
Hey, thanks for posting your changes.  I can get the right Apple/Enter key to work fine, but my function keys still behave as they initially did (volume up, down, mute, etc).  Actually, F1 works (it brings up the help window.  F2, I'm not sure, I'm used to do alt-f2 to get the run dialog, but this does not work, so it my be my Alt/Meta binding that is not right (see below).

Did you have to do anything else aside from the keyboard file?

One thing, I don't think the "add" command works, I get an "add: command not found".  What is it supposed to do?

I'm so close!, Help!

---

### Post by luopio on 2007-11-26
add mod1 = Alt_L Meta_L 
should probably be something like
xmodmap -e "add mod1 = Alt_L Meta_L"

and if you're using pommed, which you probably are since you're running on a mac, then you can control the Fn-functionality from /etc/pommed.conf 

Good luck

---

