---
title: "USB flash disk + few minor things"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by kane77 on 2006-12-28
I'm quite happy with how xubuntu runs on dad's computer (it only has 128 megs of ram), BUT there seems to be some strange problem with front usb ports...

1.) When I plug in mouse they (usb ports) both work. But when I plug in the usb flash disk it just keep on flashing in 2 second intervals... When I plug in the usb disk into rear port xubuntu normally automounts it. It may have to do something with the fact that front ones are only usb1.0... (I used to get the message in windows that: "this drive can perform faster... blah, blah...")

2.) how do I add a keyboard layout in xfce (i want to have english+slovak and switch through them with some shortcut eg ctrl+shift or alt+shift)

3.) I want free cell.. (you know the game that was shipped with windows) my grandfather is addicted to it... I have it on my computer (I use gnome), but I dont have it in xfce...

---

### Post by angkor on 2006-12-28
I don't know the answer to your other questions since I don't use Xubuntu, but this package seems to include Freecell, haven't tried it though:

```
apt-cache show ace-of-penguins
Package: ace-of-penguins
Priority: optional
Section: universe/games

[..snip..]

 The package consists of the games Pegged, Minesweeper, Solitaire,
 Taipei (together with a level editor), Golf, Mastermind, Merlin and
** Freecell**.
```

To install:

```
sudo aptitude install ace-of-penguins
``` Or use Synaptic to install the package.

---

### Post by pseudonym on 2006-12-28
> **kane77 said:**
> 1.) When I plug in mouse they (usb ports) both work. But when I plug in the usb flash disk it just keep on flashing in 2 second intervals... When I plug in the usb disk into rear port xubuntu normally automounts it. It may have to do something with the fact that front ones are only usb1.0... (I used to get the message in windows that: "this drive can perform faster... blah, blah...")
It's not a speed issue - USB 2.0 is backwards compatible with USB 1.1. It's more likely to do with the USB header on the motherboard. I don't know why, but I've found the front USB ports problematic on a few machines. The situation is easily remedied by attaching a short USB extension cable to one of the rear ports so you can have easy access to at least one of them.

> **kane77 said:**
> 2.) how do I add a keyboard layout in xfce (i want to have english+slovak and switch through them with some shortcut eg ctrl+shift or alt+shift)
There is probably a gui way of doing this but i don't know it. I use German and English and what I do is edit /etc/X11/xorg.conf like so - ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,de"
        Option		"XkbOptions"	"grp:alt_shift_toggle"
``` After restarting X, you can then switch between layouts using alt+shift.

---

### Post by kane77 on 2006-12-28
thanx a lot...

but I have a feeling that gradfather wont like the ace_freecell... but I have a plan... I'm downloading the ubuntu cd and use it as a repository for installing gnome-games... will it work??

---

### Post by pseudonym on 2006-12-28
> **kane77 said:**
>  I'm downloading the ubuntu cd and use it as a repository for installing gnome-games... will it work??
If your grandfather's machine is not connected to the internet, why don't you set up a temporary network with a shared internet connection between his and yours, instead of downloading a whole new CD?...

---

