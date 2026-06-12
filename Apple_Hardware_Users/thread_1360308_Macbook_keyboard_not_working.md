---
title: "Macbook keyboard not working"
date: 2009-12-20
forum: Apple Hardware Users
---

### Post by vincebs on 2009-12-20
Hi everyone,

I'm using a fourth-generation Intel Macbook and I can't seem to get the built-in keyboard to work in Ubuntu 9.10. Curiously, if I attach an external keyboard, it does work.

Also, the keyboard seems to work until I log in, i.e. at the login screen I can enter my credentials, as well as switch to a console and things work. Once I log in and after I hear the Ubuntu startup sound, I get the following message:
```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The .org Foundation
10604000

If you report t his situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

```

xprop says:

```

_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us", "intl", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us", "mac", ""

```

gonftool-2 says:

```

layouts = [us mac]
options = []
model = macbook79

```

Anyway, here is what my xorg.conf says:
```

Section "InputDevice"
   Identifier "Generic Keyboard"
   Driver "kbd"
   Option   "XkbModel"  "macintosh"
End Section
```

Any hints?

---

### Post by tom4everitt on 2009-12-21
What happens if you create a new user? Does the new one get the same problem?

Also, I assume you've installed all updates, tends to help :)

Otherwise I have no idea...

---

### Post by anticapital on 2009-12-23
I have just installed 9.10 on Macbook 1,1.

I am receiving the same error message as above when I try to use "Keyboard Preferences" to switch to the Macbook layout.

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

All help is greatly appreciated. Thanks.

---

### Post by vincebs on 2010-01-02
bump.

I installed all the latest updates. Anyone else have this problem?

Once again, this is a Macbook 4,1 with an Intel Core 2 Duo (Penryn-class?) 2.1 GHz processor and 2.5 GB of 667 MHz DR2 RAM.

---

### Post by wearyroad on 2010-01-30
I have the same problem as well, I've installed all the updates and I've looked at the bug reports for this problem. It seems that this might take a while to handle, so I'm writing his from the mac partition rather than break out the keyboard.

---

### Post by vincebs on 2010-09-11
bump. Same problem with 10.04. I'm wondering if it's due to xorg being confused because it is trying to save settings for two keyboards, one the laptop keyboard, and the other the  sometimes-present external USB keyboard.

---

### Post by borth92 on 2010-09-11
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

try that

---

### Post by vincebs on 2010-09-18
> **borth92 said:**
> [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

try that

Doesn't work / doesn't apply.

The keyboard works during the Ubuntu login screen (which is on the X server). It's when it logs into GNOME when my keyboard stops working.'

Help, anyone?

---

### Post by linuxopjemac on 2010-09-18
Maybe this helps:
Maybe this helps:
[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

You might also want to remove mouseemu
[https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/513932](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/513932)

This also worked:
> I finally found the problem. In /etc/modprobe.d/options.save I had the line of "options hid pb_fnmode=2". Ubuntu was confused by the extension ("save") and showed it to me as a binary file which is why it took me so long to fix this. I removed "pb_" (that is, the line became "options hid fnmode=2") and now my keyboard works just fine, with functional keys working as normal keys.

---

### Post by HanDuo on 2010-09-21
What do you get when you ```
sudo dmesg
``` ?

---

### Post by vincebs on 2010-10-10
HanDuo,

When I type "sudo dmesg", I get a lot of lines of stuff.

If I do "sudo dmesg | grep Keyboard" I get:

```
[    3.644784] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.0/input/input6
[    3.644909] apple 0003:05AC:0229.0004: input,hidraw3: USB HID v1.11 Keyboard [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input0
[    3.653394] input: Apple Computer Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2:1.2/input/input7
[    3.653510] apple 0003:05AC:0229.0005: input,hidraw4: USB HID v1.11 Device [Apple Computer Apple Internal Keyboard / Trackpad] on usb-0000:00:1d.2-2/input2
[    4.049230] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/input/input8
[    4.049373] generic-usb 0003:047D:2043.0006: input,hidraw5: USB HID v1.10 Keyboard [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.7-1.3/input0
[    4.054633] input: NOVATEK Kensington U+P Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.1/input/input9
[    4.054764] generic-usb 0003:047D:2043.0007: input,hidraw6: USB HID v1.10 Device [NOVATEK Kensington U+P Keyboard] on usb-0000:00:1d.7-1.3/input1
[    4.441535] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1.2/2-1.1.2:1.0/input/input10
[    4.441674] apple 0003:05AC:0220.0008: input,hidraw7: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-1.1.2/input0
[    4.445090] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.1/2-1.1.2/2-1.1.2:1.1/input/input11
[    4.445207] apple 0003:05AC:0220.0009: input,hidraw8: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-1.1.2/input1

```

Windows and Mac OS X seem to handle my multiple keyboards just fine.

It seems like Ubuntu thinks my default keyboard is just a numeric keypad, because if I type "UIOPJKL;NM./" I get 456*123-0.+

& no other keys work.

btw I just updated Ubuntu to 10.10 and I'm still getting this problem.

---

### Post by nkraich on 2010-11-28
Hello,

I had this same issue and figured out the problem.

First, here is the issue I was having (same as the original poster, I believe):
I was having trouble with my built-in Macbook keyboard (although this might happen on other laptops as well, I'm not sure.)  I do use an external keyboard and this worked fine even though the built-in keyboard did not.  My keyboard would work on the login screen, but would stop working once I had logged in.  A few of the keys printed numbers.  In fact, the keyboard was acting like a numeric keypad.

The problem: When I was using my external, full-size keyboard I turned on the num lock.  When I unplugged it, my laptop was stuck in num lock mode.

How to fix it: Log in.  Plug your external keyboard back in and turn off the num lock.  Then unplug the keyboard and your built-in keyboard should behave normally again.

Hope this helps!

:popcorn:

---

### Post by vincebs on 2011-05-03
Thanks, that worked! Does anyone know if this problem persists in Ubuntu 11.04?

> **nkraich said:**
> Hello,

I had this same issue and figured out the problem.

First, here is the issue I was having (same as the original poster, I believe):
I was having trouble with my built-in Macbook keyboard (although this might happen on other laptops as well, I'm not sure.)  I do use an external keyboard and this worked fine even though the built-in keyboard did not.  My keyboard would work on the login screen, but would stop working once I had logged in.  A few of the keys printed numbers.  In fact, the keyboard was acting like a numeric keypad.

The problem: When I was using my external, full-size keyboard I turned on the num lock.  When I unplugged it, my laptop was stuck in num lock mode.

How to fix it: Log in.  Plug your external keyboard back in and turn off the num lock.  Then unplug the keyboard and your built-in keyboard should behave normally again.

Hope this helps!

:popcorn:

---

### Post by Willynux on 2011-08-19
I'm having this problem but my keyboard doesn't work from the beginning, even the log in screen.
I never plugged in an external keyboard but plugged an external mouse since the trackpad is not working.
I'm on 11.04
Isn't there a way to reset it to a clean keyboard configuration or something like that?

It makes the computer unusable. My other computer (a sony) just works with no problem at all...

---

### Post by Willynux on 2011-08-20
I found on another thread that said to reset configurations you have to remove the hidden folder .gconf located in the home folder ( it solveed my problem !)

---

### Post by dharmaurchin on 2011-12-02
> **Willynux said:**
> I found on another thread that said to reset configurations you have to remove the hidden folder .gconf located in the home folder ( it solveed my problem !)

For me this erased my preferences, but keyboard still doesn't work.  I have 10.04 and my keyboard doesn't work at login or at the GRUB kernel selection menu

EDIT:  But this fix worked for my 1st gen Macbook Pro 1,1 Core2Duo, when my keyboard didn't work at login screen, in gnome, or with the GRUB kernel selection menu.  I ran sudo dpkg-reconfigure console-setup and selected Macbook/Macbook Pro as my keyboard and used all the default options and restarted.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891)

---

### Post by DARKAD on 2011-12-08
I'm sorry but I haven't found a solution to this problem, so I'll start a new thread dedicated to xfce and ubuntustudio 11.10 64bit on a macbook 4,1 as you may see here:

 [http://ubuntuforums.org/showthread.php?t=1892942](http://ubuntuforums.org/showthread.php?t=1892942)

---

