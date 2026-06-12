---
title: "Alt Gr key not working!"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2007-09-14
Argh! I've read the other posts concerning the same matter, but nothing works :(
I think it might have something to do when I reconfigured my xserver earlier.

I've tried checking under keyboard preferences - Layout options:

"Press right Alt key to choose 3rd level"
"Press left Alt key to choose 3rd level"
"Alt and Meta are on the Alt keys (default)"

but I only get this error:

[B]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70200000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd[/B]

Anyone got a helping hand?

Thanks in advance

Urk

---

### Post by Daveth on 2007-09-14
bumped into this the other day!

[http://www.zolved.com/synapse/view_content/28017/Fix_your_right_Alt_key_in_Ubuntu](http://www.zolved.com/synapse/view_content/28017/Fix_your_right_Alt_key_in_Ubuntu)

---

### Post by urk_nono on 2007-09-16
I've already tried this. Anyone else? :s

---

### Post by j0lliyo on 2007-09-17
Got the same problem on a Fujitsu-Siemens Amilo la 1703

---

### Post by Didando on 2007-09-22
I'm not sure if I understand "Alt Gr key" but from the other responses I take it that you are trying to get your right Alt key to work like the left Alt key.  This caused much frustration for me as well.  I finally got it.  I hope this works for you.

Start the keyboard properties dialog ... (I use the terminal since I run KDE and the KDE dialog did not help me)

danny:~$ gnome-keyboard-properties

Then under the Layout Options tab and "Third Level Choosers" _DESELECT_ any that may be selected.  (Click to remove any check marks). Do _NOT_ check any others unless you need a Third Level Chooser of course.

I had tried selecting the Win key etc as other howto's suggest but nothing worked.  I never tried until recently to just deselect it.

<< REVISION >>
The above fix did not persist.  I then did the following and the fix became persistant.

sudo <<your favorite text editor>> /etc/X11/xorg.conf

find the lines that read: 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"**lv3:ralt_switch**"
EndSection

and delete **lv3:ralt_switch**.  Leave the quotes in place so that the line looks like:

	Option		"XkbOptions"	""

Save and exit.

Restart X by logging out and Alt-Ctl Backspace or rebooting. Your Right Alt key should now work as expected.

---

### Post by urk_nono on 2007-09-27
You da man, Didando!

@@@@@

---

