---
title: "Keyboard Problem - (Caps lock, Numlock) Hardy"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by cvasilak on 2008-04-25
Hi there,
I have just installed Hardy on a Macbook Pro Core 2 Duo. Everything is working, ati driver, wireless(although i had to manual install from a svn version of madwifi as described in the macbook pro wiki).

The only problem i have is that the caps lock key and the numlock key are not working in the sense that the light doesn't light when i press it. Although i do get the uppercase letters when i push it. 

Futher what i see is that pressing a key in the keyboard hangs the mouse temporally and when i release it the mouse works again.

Is this a known issue? any workaround?

By the way i did a clean install of Hardy and not an upgrade.

(In Gutsy I didn't have this problem, the keys were working fine and the 
mouse issus)

Any ideas?

Thanks in advance,
Christos

---

### Post by cyberdork33 on 2008-04-25
> **cvasilak said:**
> The only problem i have is that the caps lock key and the numlock key are not working in the sense that the light doesn't light when i press it. Although i do get the uppercase letters when i push it.  you might just have to deal with it. this is not an unusual problem, but you might try pommed to see if it changes the behavior.

> **cvasilak said:**
>  Futher what i see is that pressing a key in the keyboard hangs the mouse temporally and when i release it the mouse works again.This is actually done on purpose for some reason and was the case in gutsy too... See this thread:
[http://ubuntuforums.org/showthread.php?t=545244](http://ubuntuforums.org/showthread.php?t=545244)

---

### Post by cvasilak on 2008-04-25
Thanks cyberdork33 for your reply.

I don't know if it breaks some other program but for the time being i have uninstalled "mouseemu" package and everything is back to normal. Seems to be some conflict of mousemu with the rest of the system.

Caps lock and numlock keys work, touchpad works, mouse doesn't hang when i press a key and all of the functions keys(volume up down, brightness, backlight) work ok (I haven't used pommed, they work by default).

I guess i will see in the future if it breaks sth else but for now I am happy :)

Thanks,
Christos

---

### Post by mabovo on 2008-04-25
For keyboard leds check in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218263](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218263)
and [https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/103375](https://bugs.launchpad.net/ubuntu/+source/mouseemu/+bug/103375)
Confirmed removing package mouseemu fix problem with keyboard leds not lighting up.

Probably there is some kind of problem with mouseemu.
On my MacBook 2nd gen trackpad mouse sometimes doesn't load if I keep pressing touchpad before GDM screen displays.

Normal boot I have this:
[   26.015669] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.015806] PNP: No PS/2 controller found. Probing ports directly.
[   26.016659] i8042.c: No controller found.
[   26.035879] mice: PS/2 mouse device common for all mice
[   66.900568] appletouch: incomplete data package (first byte: 2, length: 4).
[   66.984528] input: Mouseemu virtual keyboard as /devices/virtual/input/input12
[   67.038998] input: Mouseemu virtual mouse as /devices/virtual/input/input13
[   69.559087] usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -71

Mouse don't working sometimes:
[   23.897250] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.897384] PNP: No PS/2 controller found. Probing ports directly.
[   23.898237] i8042.c: No controller found.
[   23.917577] mice: PS/2 mouse device common for all mice
[   40.094619] input,hidraw4: USB HID v1.11 Mouse [HID 05ac:1000] on usb-0000:00:1d.3-1
[   65.237096] input: Mouseemu virtual keyboard as /devices/virtual/input/input14
[   65.268671] input: Mouseemu virtual mouse as /devices/virtual/input/input15
[   67.702014] usb 4-1: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -84

---

### Post by cyberdork33 on 2008-04-25
> **cvasilak said:**
> I don't know if it breaks some other program but for the time being i have uninstalled "mouseemu" package and everything is back to normal. Seems to be some conflict of mousemu with the rest of the system.
That is actual what it is supposed to do... Changing the config file as I outlined in the other post turns that option off.

---

### Post by felipe51 on 2010-01-12
I removed (uninstaled) from my system the 'mouseemu' and it solved the capsLock led issue. But I still had the problem that could not increase or decrease the keyboard brightness with F5 or F6 keyboard keys on my [MacBookPro5,4]

I solved this issue by creating two (2) shell scripts
[LIST]
[*]kbdBrightnessUp.sh
[*]kbdBrightnessDown.sh
[/LIST]

I copy those files to my home directory or the /usr/local/bin/ directory.

then grant my self permissions to write to the file which controls the keyboard brightness on this laptops.
```
sudo chmod 777 /sys/class/leds/smc::kbd_backlight/brightness
```

Then I configured the keyboard shortcuts by means of 
**System > preferences > Keyboard Shortcuts**

To configure the shortcut to increase the brightness
Click [Add]
Assign a name: **Keyboard Brightness Up**
Assign a command:**/usr/local/bin/kbdBrightnessUp.sh**
Click [Apply]
Now click the word *"Disabled"* of your newly created "shortcut" and  press the **"F6"** key

Configure the shortcut to decrease the brightness
Click [Add]
Assign a name: **Keyboard Brightness Down**
Assign a command:**/usr/local/bin/kbdBrightnessDown.sh**
Click [Apply]
Now click the word *"Disabled"* of your newly created "shortcut" and  press the **"F5"** key

Finally Click [Close]

Now when you hit the corresponding keys F5 or F6, your keyboard should increase or decrease its brightness accordingly.

I've only tested this on a *MacBookPro5,4* but there is a great chance that you could make it work on other systems where the keyboard brightness behaves this way, by editing this scripts and assigning the
variable **KBD_BRIGHTNESS_FILE** the corresponding and appropriate full path.

Best regards,
Felipe

---

### Post by Nikos.Alexandris on 2012-03-02
> **cvasilak said:**
> Thanks cyberdork33 for your reply.

I don't know if it breaks some other program but for the time being i have uninstalled "mouseemu" package and everything is back to normal. Seems to be some conflict of mousemu with the rest of the system.

Caps lock and numlock keys work, touchpad works, mouse doesn't hang when i press a key and all of the functions keys(volume up down, brightness, backlight) work ok (I haven't used pommed, they work by default).

I guess i will see in the future if it breaks sth else but for now I am happy :)

Thanks,
Christos

Still in 2012 this _was_ a problem for me (on a MacBook Pro 5,1) up until a few minutes ago :confused:. I had, on a clean Oneiric install, non-functional: 

[LIST]
[*]Capslock light indicator
[*]F11 & F12 keys
[*]Pommed crashing causing keyboard backlight to switch off after a few secs
[/LIST]

Removed mouseemu and presto, it works :D

---

