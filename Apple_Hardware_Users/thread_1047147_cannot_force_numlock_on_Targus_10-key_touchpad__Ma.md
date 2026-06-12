---
title: "cannot force numlock on Targus 10-key touchpad / MacBook Pro 4,1"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by MaddMatt on 2009-01-22
Hi All, 

I am not currently able to enable numlock on my targus wired 10-key pad... As in right now it is just arrow keys and is not very useful. I tried installing numlockx and enabling it that way, but to no avail. 

Also, I am a little curious as to what the best/default keymap is for Macbooks in Intrepid, and if there was a way of editing the keymap manually? Mine seems to have gotten a little screwy to the point where the volume / backlight keys have stopped working, and I think it may be a related problem. Also possibly related; I am getting an "Error activating XKB configuration" at boot and other times. 

Some other potentially useful information:
```
$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "macbook78", "us", "mac", "grp:alts_toggle"
_XKB_RULES_NAMES(STRING) = "evdev", "macbook78", "us", "mac", "grp:alts_toggle"
```

```
$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us	mac,es	mac,us]
 model = macbook78
 options = [grp	grp:alts_toggle]
```

Pointing me in the right direction would be much appreciated. 
Thanks!

---

### Post by MaddMatt on 2009-01-25
No takers? Hmm. I rebooted a few times and my hotkeys seem to have fixed themselves... I would be curious to see what special characters the keypad outputs - like those 0x28 type numbers. Does anyone know how to find those?

---

### Post by MaddMatt on 2009-01-30
OK so can someone just post their XKB configuration on a working Macbook Pro Penryn (4,1)? Thanks in advance. 

Cheers, 
m

---

### Post by Neural oD on 2009-01-30
not sure if this help - but if you go say to tty1 - ctrl-shift-F1, you should be able to see the key sequence of those keys ie: 0x28
The other issue i'm not able to help at the moment - sorry

---

### Post by MaddMatt on 2009-01-30
> **Neural oD said:**
> not sure if this help - but if you go say to tty1 - ctrl-shift-F1, you should be able to see the key sequence of those keys ie: 0x28
The other issue i'm not able to help at the moment - sorry
HEY! Good thinking! That did help quite a bit.
The keypad works perfectly in TTY1 - as in all numbers and symbols work and it responds to Numlock. 

So what this means is that it's not kernel based but part of Gnome? I think the XKB configuration for Penryn 4,1 is where I will find the solution. Thanks for the tip N.0.

---

### Post by Neural oD on 2009-01-30
np - glad I could help in some small way :)

---

### Post by baking666 on 2009-02-05
Hi :-)

Maybe it's the option in keyboard preferences under Mouse Keys tab that's causing numlock not to work?

---

### Post by MaddMatt on 2009-02-06
I do not have mouse-keys enabled... So nothing is there. Thanks for the suggestion-

I notice that my keyboard will also not switch layouts either (spanish, french, etc.) so I think that this may be related to a larger problem with the keymap settings / XKB... 

I would really like to see someone's XKB configuration from a functioning Intrepid install on a Macbook Pro...

Thanks again for the suggestion

---

### Post by cyberdork33 on 2009-02-06
They currently seem to be grouping all these layout bugs under here:

[https://bugs.edge.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/261573](https://bugs.edge.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/261573)

---

### Post by MaddMatt on 2009-02-07
> **cyberdork33 said:**
> They currently seem to be grouping all these layout bugs under here:

[https://bugs.edge.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/261573](https://bugs.edge.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/261573)

**SWEEEEEEEEEEEEETTTTTTTTTTT**
If they still had the 'thank' button enabled I would thank you, but I guess I'll do it the old-fashioned way;

"Thanks!"

Very simple - I just changed the "keyboard model" from "Macbook/Macbook Pro" to "Apple" in System > Preferences > Keyboard, and I got the idea to do this from that bugtrack. 

Now I can quickly enter data in OOo Calc, AND it's switching to different language keyboard layouts again! Super!

You rock! 
:guitar:
m

---

### Post by MaddMatt on 2009-02-07
Sheiße! I spoke too soon!
Changing it to 'Apple' instead of 'Macbook/Macbook Pro' disables all of the hotkeys.... Weaksauce! I wonder if I can work-around that by installing pommed...

---

