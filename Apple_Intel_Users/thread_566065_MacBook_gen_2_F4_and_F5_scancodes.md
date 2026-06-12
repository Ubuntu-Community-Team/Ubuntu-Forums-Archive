---
title: "MacBook gen 2 F4 and F5 scancodes?"
date: 2007-10-03
forum: Apple Intel Users
---

### Post by doublemeat on 2007-10-03
Hello, I've searched for hours on this and have found no solution.  I have remapped my function keys (MacBook non-pro gen 2), so that they work without pressing Fn also.  (Yes I tried pommed and after following instructions diligently more than once, could not get it to work.)  At this point I can do without the hardware control that I lose by directly mapping scancodes via xmodmap.

Here is a portion of a script that remaps the keys.  (There is a good reason I do this laboriously one call to xmodmap at a time, but that is beyond the scope of this question.)
```

		xmodmap -e 'keycode 101 = F1'    # 101 / 67
		xmodmap -e 'keycode 212 = F2'    # 212 / 68
		xmodmap -e 'keycode 160 = F3'    # 160 / 69
#		xmodmap -e 'keycode  = F4'    # ? / 70
#		xmodmap -e 'keycode  = F5'     # ? / 71
		xmodmap -e 'keycode 77 = F6'     # 77  / 72
		xmodmap -e 'keycode 214 = F7'    # 214 / 73
		xmodmap -e 'keycode 215 = F8'    # 215 / 74
		xmodmap -e 'keycode 216 = F9'    # 216 / 75
		xmodmap -e 'keycode 217 = F10'   # 217 / --

```
As you can see, I don't know what the scancodes are for F4 and F5.  I got the original values from some post on this forum, but F4-6 were not correct for my MacBook (I self-discovered the scancode for F6 because that key does not have an overriding hardware function and thus creates a useful event in xev).  Also, the scancode values are not predictable because they jump around from F1 to F10.  (And the values are not logical extensions from the scancode values above or below.)  

Short of trying every value between 0 and 255 (if it is even limited to that), does anyone happen to know what they are?  Many thanks?

BTW, once I get this resolved I'll post my entire keymapping scheme, but here's what I have so far.  Everything works flawlessly save for aformentioned F4/F5 keys (and of course hardware control for the other keys).  This goes in a bash script:
```

	## remap certain Apple MacBook keys (Feisty Fawn...should work on any Ubuntu or other distro release)

		## Feisty MacBook: swap L Option and L Command keys
		xmodmap -e 'clear Mod1'
		xmodmap -e 'keycode 115 = Alt_L Meta_L'  # left Command becomes  left Alt
		xmodmap -e 'keycode 64 = Super_L'        # left Alt becomes  left Command
		xmodmap -e 'add Mod1 = Alt_L Meta_L'

		## Feisty MacBook: selecting "MacBook" keyboard in keyboard setup for some reason maps grave/tilde key to </>; this fixes it
		xmodmap -e 'keycode 49 = grave asciitilde'

		## Feisty MacBook: map bottom enter key to context-sensitive menu key
		xmodmap -e 'keycode 108 = Menu'

		## Feisty MacBook: fix function keys (unfortunate but tolerable side-effect--this also disables use of fn+hardware control)
		xmodmap -e 'keycode 101 = F1'    # 101 / 67
		xmodmap -e 'keycode 212 = F2'    # 212 / 68
		xmodmap -e 'keycode 160 = F3'    # 160 / 69
#		xmodmap -e 'keycode  = F4'    # ?   / 70
#		xmodmap -e 'keycode  = F5'     # ?   / 71
		xmodmap -e 'keycode 77 = F6'     # 77  / 72
		xmodmap -e 'keycode 214 = F7'    # 214 / 73
		xmodmap -e 'keycode 215 = F8'    # 215 / 74
		xmodmap -e 'keycode 216 = F9'    # 216 / 75
		xmodmap -e 'keycode 217 = F10'   # 217 / --

		## Feisty MacBook: swap backspace ("delete") and delete (fn+"delete")
		## 20071001: this is impossible to mentally adjust to, going back to normal by rem'ing these out
		#xmodmap -e 'keycode 22 = Delete'
		#xmodmap -e 'keycode 107 = BackSpace'

```
Thanks!

---

### Post by knathraak on 2007-10-04
This isn't really the answer to your question, but it may help.  I never bothered with remapping the Fn keys to get them to behave as Fn keys.  Instead, I changed the parameters that the hid kernel module gets loaded with.  I followed these instructions:
[http://ubuntu-tutorials.com/2007/06/03/remapping-the-function-key-behavior-on-macbook-macbook-pro/](http://ubuntu-tutorials.com/2007/06/03/remapping-the-function-key-behavior-on-macbook-macbook-pro/)
Which essentially tell you to create /etc/modprobe.d/function, containing the line
options hid pb_fnmode=2

Hope this helps.

---

### Post by doublemeat on 2007-10-04
> **knathraak said:**
> This isn't really the answer to your question, but it may help.  I never bothered with remapping the Fn keys to get them to behave as Fn keys.  Instead, I changed the parameters that the hid kernel module gets loaded with.  I followed these instructions:
[http://ubuntu-tutorials.com/2007/06/03/remapping-the-function-key-behavior-on-macbook-macbook-pro/](http://ubuntu-tutorials.com/2007/06/03/remapping-the-function-key-behavior-on-macbook-macbook-pro/)
Which essentially tell you to create /etc/modprobe.d/function, containing the line
options hid pb_fnmode=2

Thanks, I did try that.  I followed the steps multiple times verbatim, from more than one "howto" source.  Never got it to work, and I have no idea why, nor enough knowledge of Linux yet to figure out where or why it's not working.  For now, I've got all the Fn keys working except for F4 and F5.  Figuring those two out seems a more surmountable challenge than getting the pb_fnmode thing (or pommed which I believe also does that as part of it's function) to work.  At the very least, I can undertake the tedious chore of trying everything between 1 and 255 (assuming that somewhere it is limited to 8 bits or otherwise to 255, and I don't have to go up to 65,535!)

Thank you though.

---

