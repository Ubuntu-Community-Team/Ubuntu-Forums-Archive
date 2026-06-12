---
title: "[SOLVED] Toggle fn without pommed?"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by bryonak on 2008-10-30
I've got a MacBookPro 3 (Santa Rosa) and have been using the F1-F12 keys for things like refreshing, alt+F2 and other shortcuts I've configured... which means that the brightness and volume functionalities should be triggered only with the fn key pressed, not the other way around.
This has been easy with pommed, setting the fn mode to '2' in pommed.conf.
But pommed seems to be deprecated in Intrepid, replaced by mactel+applesmc... still I'd like my old functionality back, but I can't figure out where to change this setting.
Anyone got a hint?

---

### Post by kosumi68 on 2008-10-30
> **bryonak said:**
> I've got a MacBookPro 3 (Santa Rosa) and have been using the F1-F12 keys for things like refreshing, alt+F2 and other shortcuts I've configured... which means that the brightness and volume functionalities should be triggered only with the fn key pressed, not the other way around.
This has been easy with pommed, setting the fn mode to '2' in pommed.conf.
But pommed seems to be deprecated in Intrepid, replaced by mactel+applesmc... still I'd like my old functionality back, but I can't figure out where to change this setting.
Anyone got a hint?

Check the Keyboard Setup section here: [https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

---

### Post by bryonak on 2008-10-30
Uh, this one I had no chance to figure out...

Why isn't there some central place for those settings? (well, like pommed.conf...)
Or a GUI if it must be ;)

---

### Post by bryonak on 2008-10-31
Well... it doesn't seem to work after yesterdays kernel upgrade (2.6.27-7-generic came up in the Update Manager after a few hours of Intrepid usage).

applesmc and mbp_nvidia_bl are loaded, /etc/modprobe.d/options contains ```
options hid pb_fnmode=2
``` and I've installed the hal-applesmc package from mactel.

Still the /sys/module/hid/parameters/pb_fnmode is set to 1 when I look it up after booting.
My current solution is ```
sudo su
echo "2">/sys/module/hid/parameters/pb_fnmode
```

I could put this into rc.local, but isn't there any non-workaround solution?


Just another quick question: I'm using the gconf-editor to change the keyboard lighting (turned it off all the way). Is there any "recommended" way to do this? ... So that my gconf settings won't be overridden later by some specific tool which I should have used in the first place.

IMO things were pretty straightforward when everything was in the xorg.conf (+ pommed.conf). Now they're not anymore.

---

### Post by _mario_ on 2008-10-31
> **bryonak said:**
> Well... it doesn't seem to work after yesterdays kernel upgrade (2.6.27-7-generic came up in the Update Manager after a few hours of Intrepid usage).

applesmc and mbp_nvidia_bl are loaded, /etc/modprobe.d/options contains ```
options hid pb_fnmode=2
``` and I've installed the hal-applesmc package from mactel.

Still the /sys/module/hid/parameters/pb_fnmode is set to 1 when I look it up after booting.
My current solution is ```
sudo su
echo "2">/sys/module/hid/parameters/pb_fnmode
```

I could put this into rc.local, but isn't there any non-workaround solution?
just a thought: did you rebuild your initial ramdisk? the hid modules get loaded very early in the boot process taking their options from the /etc/modprobe.d/* files incorporated into the ramdisk.

> **bryonak said:**
> 
Just another quick question: I'm using the gconf-editor to change the keyboard lighting (turned it off all the way). Is there any "recommended" way to do this? ... So that my gconf settings won't be overridden later by some specific tool which I should have used in the first place.

to be honest: i don't really understand the question. isn't it sufficient to press the keyboard backlight buttons to change it?

ciao,
Mario

---

### Post by bryonak on 2008-10-31
> **_mario_ said:**
> just a thought: did you rebuild your initial ramdisk? the hid modules get loaded very early in the boot process taking their options from the /etc/modprobe.d/* files incorporated into the ramdisk.

I didn't, I wasn't aware this has become necessary with Intrepid. Will I have to make a new initrd on every kernel upgrade? Because I'd like to keep getting the newest kernel via Update Manager.

> **_mario_ said:**
> 
to be honest: i don't really understand the question. isn't it sufficient to press the keyboard backlight buttons to change it?

That works fine, but I don't want it to change to 50% on battery and to 100% when I plug in the cord, no matter what light conditions. If I need it, I'll turn it on.
So my question was if the gconf-editor is the right ("future-safe") place to do this.

---

### Post by _mario_ on 2008-10-31
> **bryonak said:**
> I didn't, I wasn't aware this has become necessary with Intrepid. Will I have to make a new initrd on every kernel upgrade? Because I'd like to keep getting the newest kernel via Update Manager.
i don't know whether a kernel upgrade rebuilds the ramdisk. i will have to see soon. it was just a thought.
> **bryonak said:**
> That works fine, but I don't want it to change to 50% on battery and to 100% when I plug in the cord, no matter what light conditions. If I need it, I'll turn it on.
BTW: where's the key to change keyboard backlight in gconf?

ciao,
Mario

---

### Post by bryonak on 2008-10-31
Well, looks like it's the rc.local then.
Anyone got a better (== more convenient) solution?

> **_mario_ said:**
> where's the key to change keyboard backlight in gconf?
apps -> gnome-power-manager -> keyboard

---

### Post by _mario_ on 2008-10-31
> **bryonak said:**
> 
apps -> gnome-power-manager -> keyboard
then it's the right place to change it. right now there's no GUI, but maybe in a future release.

ciao,
Mario

---

### Post by bryonak on 2008-10-31
Putting the pb_fnmode line into rc.local doesn't work, it stays at 1 when I check after logging into GNOME.
The same happens when I write it into xinitrc.
Does anyone know a root-script that could write to /sys/module/hid/parameters/pb_fnmode **after** the module is done with setting it to 1?
Making a custom suid script and launching it in the GNOME session seems too awkward for such a thing.

Currently I have two problems:
1. The fnmode is set to 1, so I have to change it manually. Script-workarounds don't work, nor does modprobe.d configuration.
Reconfiguring the initrd looks like too much hassle regarding future kernel updates.

2. After logging into GNOME, the keyboard light is at 100%. Pressing the button to turn it off isn't much work, but I'd like to have it at 0% and can't find any option for this in the gconf-editor (only for AC state changes), and apart from that I have no clue where one can modify this. Suggestions?

---

### Post by kosumi68 on 2008-10-31
> **bryonak said:**
> Putting the pb_fnmode line into rc.local doesn't work, it stays at 1 when I check after logging into GNOME.
The same happens when I write it into xinitrc.
Does anyone know a root-script that could write to /sys/module/hid/parameters/pb_fnmode **after** the module is done with setting it to 1?
Making a custom suid script and launching it in the GNOME session seems too awkward for such a thing.

Currently I have two problems:
1. The fnmode is set to 1, so I have to change it manually. Script-workarounds don't work, nor does modprobe.d configuration.
Reconfiguring the initrd looks like too much hassle regarding future kernel updates.

2. After logging into GNOME, the keyboard light is at 100%. Pressing the button to turn it off isn't much work, but I'd like to have it at 0% and can't find any option for this in the gconf-editor (only for AC state changes), and apart from that I have no clue where one can modify this. Suggestions?

1. Is the problem that ALT+F4 does not kill the window, or is it that the sys interface shows the wrong value? Keeping the pb_fnmode in /etc/modprobe.d/options works for me.

2. The gnome-power-manager keybord section has two options in my setup: onw for ac and one for battery. Did you upgrade to intrepid or install the system from an intrepid cd?

---

### Post by _mario_ on 2008-10-31
> **kosumi68 said:**
> 
2. The gnome-power-manager keybord section has two options in my setup: onw for ac and one for battery. Did you upgrade to intrepid or install the system from an intrepid cd?
i tried to follow, but what are you (and the previous poster) talking about?

the "On AC Power" tab, shows (besides others):
a checkbox "Dim display when idle"

the "On Battery Power" tab, shows (besides others):
a checkbox "Reduce backlight brightness"
a checkbox "Dim display when idle"

but no keyboard backlight. and btw: does anybody know what are these 2 options on the battery tab used for?

ciao,
Mario

---

### Post by bryonak on 2008-11-01
> **kosumi68 said:**
> 1. Is the problem that ALT+F4 does not kill the window, or is it that the sys interface shows the wrong value? Keeping the pb_fnmode in /etc/modprobe.d/options works for me.

After booting, Alt+F4 doesn't kill the window but lowers the volume instead, ignoring the Alt.
The same goes for all the F keys: Alt+F2 brightens the screen, Fn+Alt+F2 gives me the run prompt. I want it to be the other way around, because pressing Fn+F5 instead of just F5 to refresh bothers me.

The entry in /etc/modprobe.d/options worked before the kernel upgrade, now it seems to be ignored.
The hid interface shows 1 after booting, if I echo a 2 into it, the Fn modifier immediately starts working as I'd like it to. But I don't want to do this manually at each boot... and both rc.local and xinitrc seem to change it too early, as it's set to 1 again when I can check it.

> **kosumi68 said:**
> 
2. The gnome-power-manager keybord section has two options in my setup: onw for ac and one for battery. Did you upgrade to intrepid or install the system from an intrepid cd?
There's no mention of "keyboard" anywhere in my power manager (Preferences -> Power Management).
I upgraded from Hardy, so it might be that the responsible binary didn't get updated, though that would be a bad sign for the overall process.
Could you attach a screenshot of this entry?


I probably won't be able to answer today anymore, so see you tomorrow.
Thanks for your time guys!

---

### Post by kosumi68 on 2008-11-01
1. Sounds like your ramdisk is out of sync somehow. Try
```

sudo update-initramfs -u -v -k `uname -r`

```
then reboot

2. The settings refer to to the program gconf-editor.

---

### Post by bryonak on 2008-11-02
> **kosumi68 said:**
> 
sudo update-initramfs -u -v -k `uname -r`

Worked beautifuly, thanks. Now the option in modprobe.d/options gets parsed.


> **kosumi68 said:**
> 
The settings refer to to the program gconf-editor.
Yep, but those get "only" triggered when I plug in/out the power cord.
Before I enter my name/pw into the gdm login, they stay dark (and the backlight brightness file in the modules ramfs shows that too when I check from another tty), but 3-4 seconds after login, while GNOME is loading, they go to full brightness, no matter whether I'm on battery or AC.
Then removing/attaching the power cord changes them to the settings I entered in gconf.

It's not that big of a problem, though on Hardy they were set to 0 at login, so I clearly notice the difference now.

---

### Post by cyberdork33 on 2008-11-04
> **kosumi68 said:**
> 1. Sounds like your ramdisk is out of sync somehow. Try
```

sudo update-initramfs -u -v -k `uname -r`

```then reboot

2. The settings refer to to the program gconf-editor.
worked great for me after this!

---

### Post by bryonak on 2008-11-06
Well, 2. problem isn't solved yet, but the thread's main question is answered.
So I guess I'll mark this as solved and open a new thread for the keyboard backlight issue.

---

### Post by undoIT on 2009-05-30
Does anyone know how to get this working with a Macbook 5,1 in Jaunty? 

I tried adding the suggested line to /etc/modprobe.d/options, did the ramdisk trick and rebooted, but F1 and F2 are still controlling the brightness without the fn key pressed, thereby blocking the normal shortcuts for F keys.

---

### Post by cyberdork33 on 2009-05-30
> **undoIT said:**
> Does anyone know how to get this working with a Macbook 5,1 in Jaunty? 

I tried adding the suggested line to /etc/modprobe.d/options, did the ramdisk trick and rebooted, but F1 and F2 are still controlling the brightness without the fn key pressed, thereby blocking the normal shortcuts for F keys.
the module name changed in Jaunty:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

---

### Post by undoIT on 2009-06-06
> **cyberdork33 said:**
> the module name changed in Jaunty:
[https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard)

Thank you for the link, that works.

---

