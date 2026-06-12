---
title: "Sound &amp; keyboard"
date: 2006-06-22
forum: Apple PPC Users
---

### Post by Nesmontu on 2006-06-22
Hello everyone,
I have an eMac G4 dual booting Tiger and Dapper. Mostly everything works fine, but there's two things that are bugging me.
*The keyboard: there's apparently no layout for a Belgian mac keyboard. I got a custom keyboard file, but I don't know how to make it work (pretty new to linux...) What I've done so far is, I copied it to "/etc/X11/xkb/symbols/macintosh_vndr" (which I thought was the right location). What I need to know is what to put in my xorg.conf?
Right now it says (the keymap is called fr, not be as you might expect)

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh_vndr"
	Option		"XkbLayout"	"fr"
EndSection
```

*Sound: I do have it, but it's acting strangely. Music, game sounds, etc. play very very quietly, while system sounds are on normal volume. So, when I'm listening to music I have to turn the volume up fully if I want to hear anything; and then a system sound plays and blows my boxes #-o

Any and all ideas on either of these issues are greatly appreciated...

---

### Post by mooreted on 2006-06-25
Open up a terminal and type "sudo cp /etc/X11/xorg.conf xorg.bak" (always good to back up script files before messing with them)

Open up a terminal and type "sudo vi /etc/X11/xorg.conf"

Scroll down to where you see "InputDevice"

Press the "I" key to enter input mode.

Change the values to match the custom config shown in your post.

Press the ESC key to exit insert mode

type ":w" and press RETURN (this writes the file to the drive)

type ":q:" and press RETURN to quit vi

Restart the X server or reboot.

Can't guarantee your custom config will work.

---

### Post by BoneKracker on 2006-06-27
Nesmontu,

Which is the case:

a) You have already edited your xorg.conf file with the code you listed, but it's not working

b) You are wondering how to get that code into your xorg.conf file.


I think mooreted answered (b).  Just want to make sure you weren't asking (a).

---

