---
title: "Logitech EX110 Keyboard not working (Not the &quot;special&quot; keys)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by einversuchisteswert on 2007-07-24
Hi,

i have searched the web and this forum but i only found stuff for the extension keys or that the keyboard works fine.

But my problem is that my keyboard does not connect, ok it connects (lights are blinking) but thats all.

I tried to edit the xorg.conf, but nothing helped.

Has anyone a suggestion, link or anything?

i'm using ubuntu 7.04.

thanks

---

### Post by FleetAdmiral74 on 2007-07-24
You can try using an adaptor (ps/2) and see if that works. There are a few other threads I found googling, but none seem to point to a solution. The problem seems to be its USB, which can cause a driver problem.

---

### Post by einversuchisteswert on 2007-07-26
Hi,

first have to thank you for your Reply but i still have the problem and i still think the solution is to edit the xorg.conf.

Can someone who has the EX110 keyboard post his xorg.conf part of it?

Thank you!

---

### Post by rand1038 on 2007-07-28
> **einversuchisteswert said:**
> Hi,

first have to thank you for your Reply but i still have the problem and i still think the solution is to edit the xorg.conf.

Can someone who has the EX110 keyboard post his xorg.conf part of it?

Thank you!
It is important to note that if the lights on the dongle are *flashing* then you are **not connected**, the device is waiting for a signal from the keyboard or mouse.

I am running Fedora 7 on my box with the EX110 keyboard so I don't know if this xorg.conf config will be the same but since you haven't had any replies yet it might be worth a try (my edgy install has a corded keyboard, if necessary I'll move this one to it and see what happens).  I've posted only the relevant sections, your file will have additional contents.  Note the 'InputDevice' line in the 'ServerLayout' section.  It needs to be there just like that and should be the only line in the xorg.conf file that has 'CoreKeyboard' in it.  In relation to the keyboard, my xorg.conf file is the default as written at install time.
```

Section "ServerLayout"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

```
As you can see, the generic 'kbd' driver is being used with the standard pc105, us layout (I am connected through the ps2 adapter provided with the keyboard).
If you are still having problems post your xorg.conf file so we can take a look.

---

### Post by einversuchisteswert on 2007-07-30
Thanks for the post and i have the same stuff in de xorg.conf (ok different language...).

And i found a ps2 adapter and it works to but not with usb and it not works if i have an usb-storage plugged.

It think i have a general usb problem (if so than it would not fit in this thread).

thanks again but if someone has experience solving usbproblems, feel free to post!

---

