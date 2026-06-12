---
title: "Keyboard Numlock not working"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-03-22
Hi

I've got a problem with my keyboard. The numlock light goes on and off but the keypad is locked in 'numlock'.

It started when I changed monitors. The old monitor was set to 1024 x 768. When I connected the new one and restarted the resolution changed to 640 x 480. I went to [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto). I used the 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum'
sudo dpkg-reconfigure -plow xserver-xorg

```

code block and went through a dialogue. I got the monitor working to 1024 x 768 resolution BUT...

The keyboard has a locked right hand number pad. It's currently locked into numlock - light responds to pressing numlock key but always get a stop when I press del, both light on and light off. £ sign is £ sign, @ is @, #is# etc.It's a standard Compaq business style pc keyboard. Never any trouble. Nothing sticks, all very clean.

What do I need to do to get numlock working again properly please?

Rgds, Bob

---

### Post by zvacet on 2007-03-23
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_turn_on_Num_Lock_on_GNOME_startup]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_turn_on_Num_Lock_on_GNOME_startup")

---

### Post by macogw on 2007-03-23
How the heck did you get the symbols for the top-row numbers to show up when you press keypad numbers?  

I never got why anyone would turn off numlock though.  I mean, there's already a set of arrow keys, why do you need the arrow keys that are under the numbers?  Seems pointless...

---

### Post by bwallum on 2007-03-23
The £, *, @ keys are on the left main keypad. Sorry about the confusion, I was trying to demonstrate that the UK keyboard configuration was ok except for the numlock problem.

I get this error on boot up:-

BEGINNING OF ERROR MESSAGE
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70101000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
END OF ERROR MESSAGE

xprop -root | grep XKB result:-

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc104", "uk", "", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "uk", "", "lv3:ralt_switch"

gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd result:-

 layouts = []
 model = compaqeak8
 options = [lv3 lv3:ralt_switch]
 overrideSettings = true

My keyboard is a Compaq KB-9860.

Regards
Bob

---

### Post by bwallum on 2007-03-23
Tried the How To suggested. Like many of them it didn't work for me. Problem remains, whenever I press the far right del button I get a stop, with or without the numlock light on.

Bob

---

### Post by daynah on 2007-03-23
You know... looking at my keyboard now, I don't have a numlock. What the heck is a numlock for anyway?

Nonetheless, XServer possibly thought that your keyboard was a laptop keyboard, you know, a few crayons short of a box.

I had to reset XServer the other day because of some ATI dumbness, and reset my keyboard also. Maybe you can tell it that it was dumb and get it to pick a different keyboard for you.

During this, you will have to reset also your monitor and lots of other things, and it's like 10-15 minutes long, so though I think it will work, there also is probably an easier way, just like there was probably an easier way of getting my ATI drivers working. (10 minutes seemed long, but researching the "better" way probably would have taken me another hour...)

So to reset your XServer do this... sudo dpkg-reconfigure xserver-xorg

I suggest you back up your xorg file (/etc/X11/xorg.conf) first, incase you have personalized information in there you want to add in.

Have fun!

---

### Post by bwallum on 2007-03-23
Ok, tried that now, completely stuffed. "Failed to start the X Server" message.

My graphics are onboard Intel, Intel 82845/GL/GE/PE/GV. There is no obvious choice for this in the XServer configuration routine. I tried vga. Now have the above message and a blank screen.

This reply is coming from my XP machine. Please don't ask for the error report from X Server. It is a mile long and I have no way of cutting and pasting it, at least now without a 5 year degree in computing to get to know in depth Linux! That seems to be the only way to get to a usable state with it. Simple, it is not.

Please help. i actually started to do some work on Ubuntu and need to get it off before I lose more time. (In my forth week of trying to get Ubuntu beyond the novelty stage)

Regards
Bob
Bob

---

