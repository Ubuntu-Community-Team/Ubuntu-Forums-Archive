---
title: "apple keyboard for ubuntu"
date: 2009-09-15
forum: Apple Hardware Users
---

### Post by cste04 on 2009-09-15
Hi,
I have bought an apple keyboard, which I want to use with ubuntu. Is it possible to get the keyboard to work in ubuntu as it would on a mac? 

I have tried changing the keyboard layout from default to macBook. I still cant use the function or apple key.

Best Regards
Carsten Steffensen

---

### Post by Aizawa on 2009-09-15
That's strange; I bought an apple keyboard just today, plugged it in, switched my keyboard layout in Preferences - Keyboard... And everything works.

---

### Post by gwydionwaters on 2009-09-16
mine works as well, although i am using a mac. either way, i have Model set to MacBook/MacBookPro and layout as USA Macintosh. hope that helps

---

### Post by soebbi on 2009-09-17
I'm having the same problem. You can switch the basic layout to mac (although e.g. the left alt key isn't treated like an alt-gr like it is on a mac, so you can't use it to write an @), but still the shortcuts aren't similar to a mac. And me (and i think the thread starter) don't want to get used to two different sets of shortcuts.

e.g.
cmd-tab instead of ctrl-tab for window switching.
cmd-c, cmd-x, cmd-v, cmd-a instead of ctrl-c, ctrl-x, ctrl-v, etc...

So, instead of only having the keys do what they're having printed on them, i (and i think the thread started) want to use the same shortcuts on Ubuntu as on MacOS.

You can configure this partly (the cmd-key has the name "meta" or "super" on Ubuntu), but can't be done completly - as far as i know. The problem is IMHO that the cmd-key has on MacOS some functions, that on Ubuntu are split to two keys (e.g. cmd-tab and cmd-x on MacOS is alt-tab and ctrl-x on Ubuntu). So you can't just flip some keycodes, you have to configure new shortcuts in the preferences. But this often fails, since these only work on Gnome/GTK-apps, and not on e.g. kde or even Java-apps.

Does anyone have the same problem and found a good solution to use the same shortcuts on MacOS and Linux using an Apple-keyboard?

Woah, long post! :) Thanks for reading, and thanks even more if you have a solution to this!

Cheers,
Soebbi

---

### Post by Jobis on 2009-09-18
it works fine for me - except that the < key and § key have switched places. What can I do about that?

---

### Post by Jobis on 2009-09-21
In case anyone is curious, these commands worked for me:

xmodmap -e "keycode 49 = less greater less greater bar brokenbar"
xmodmap -e "keycode 94 = section onehalf section onehalf paragraph threequarters"

I figured out the keycodes using xev (run the command "xev"), so if the above commands do not work, try finding the correct keycodes using xev. If you feel you have screwed up your xmodmap, restart X. You can restart X by, for example, rebooting your computer.

---

### Post by _mario_ on 2009-09-22
> **soebbi said:**
> I'm having the same problem. ...


the Alt key is always different, since Windows/Linux software distinguishes Alt to input menu commands and AltGr to type alternate symbols. on an Apple keyboard the left Alt key is Alt, while the right Alt key is AltGr. you cannot easily change this be behavior and probably won't like to.

with respect to shortcuts using the Apple command key, Linux typically uses the control key for shortcuts (ctrl-c, ...), while the Apple key (which is indeed the Windows key in Linux) is unused. however it is possible to completely swap those keys. for instructions, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1006952").

ciao,
Mario

---

### Post by RVB Pïxels on 2010-03-12
Hi, 
First of all I would like to say hello to the community....
I'm new here and to (Linux) Ubuntu 9.10 and I'm really having problems finding how/why I can't use the '@' on an Apple Pro Keyboard. I only get a tiny number  [SIZE=3]²
[/SIZE]
Some details :
French Language
Karmic 9.1O image 2.6.14
Not updated to the latest because I lose all sound and even when I previously did the '@' still didn't work.

Keyboard Preferences :
France autre (other)
France Apple-Macintosh

When I installed it from the alternate CD it worked fine and I havn't updated anything.
I do get the XKB bug window which I've seen around on the web, Here's mine below.

Error activating XKB configuration.
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


rvb@ubuntu-rvb:~$ xprop -root 
rvb@ubuntu-rvb:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "fr", "oss", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "fr", "oss", "lv3:ralt_switch"
rvb@ubuntu-rvb:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [fr    oss,fr    mac]
 options = [lv3    lv3:ralt_switch,grp    grp:alts_toggle]
 model = macintosh


If anyone can point me in the right direction I would be more than grateful.

Best regards,
RVB Pixels

---

### Post by linuxopjemac on 2010-03-12
I chose Macintosh US and in Layout you can set left Alt key for 3rd level. This is how I got my @ sign to work.

---

### Post by RVB Pïxels on 2010-03-12
Thanks linuxopjemac !! @t l@st I don't need to copy @nd p@ste these [SIZE=5]@[/SIZE] 
It was the "3rd level" that got me onto it.

Best regards,
RVB Pixels

---

