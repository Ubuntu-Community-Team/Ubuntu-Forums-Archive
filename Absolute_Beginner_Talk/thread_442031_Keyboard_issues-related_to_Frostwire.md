---
title: "Keyboard issues-related to Frostwire?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-05-13
My keyboard no longer works correctly in ubuntu.  It works fine during the startup and I can use it in bios.  It won't type anything for a while but then it repeats the same key a bazillion times.  The only change to my system was the installation of Frostwire yesterday.

Dumb question-how do I uninstall it to see if that's really thje issue?  Or is there another problem?

I have a Labtec wireless keyboard/mouse.  (not USB)  The mopuse works just fine.

---

### Post by mejy on 2007-05-13
Try running 'xev | grep keycode' (copy and paste if necessary into the terminal), press some random keys and post the output.  Also, try poking round System -> Preferences -> Keyboard/Keyboard Shortcuts.

'sudo apt-get remove frostwire' should remove it (or maybe frost-wire etc.), but I seriously doubt that that could have any serious effect.  Does it work at the login screen?  If so, you're worst case scenario is to create a new user and copy over your documents etc.

---

### Post by bean77 on 2007-05-13
I've done the latter.  I'll see if I can get the keyboard working to do the first suggestion.

---

### Post by bean77 on 2007-05-13
state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 31 (keysym 0x69, i), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 45 (keysym 0x6b, k), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 45 (keysym 0x6b, k), same_screen YES,
    state 0x10, keycode 42 (keysym 0x67, g), same_screen YES,
    state 0x10, keycode 32 (keysym 0x6f, o), same_screen YES,
    state 0x10, keycode 31 (keysym 0x69, i), same_screen YES,
    state 0x10, keycode 27 (keysym 0x72, r), same_screen YES,
    state 0x10, keycode 32 (keysym 0x6f, o), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 42 (keysym 0x67, g), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 27 (keysym 0x72, r), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 31 (keysym 0x69, i), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 27 (keysym 0x72, r), same_screen YES,
    state 0x10, keycode 28 (keysym 0x74, t), same_screen YES,
    state 0x10, keycode 27 (keysym 0x72, r), same_screen YES,
    state 0x10, keycode 28 (keysym 0x74, t), same_screen YES,
    state 0x10, keycode 31 (keysym 0x69, i), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 28 (keysym 0x74, t), same_screen YES,
    state 0x10, keycode 44 (keysym 0x6a, j), same_screen YES,
    state 0x10, keycode 28 (keysym 0x74, t), same_screen YES,
    state 0x10, keycode 29 (keysym 0x79, y), same_screen YES,
    state 0x10, keycode 29 (keysym 0x79, y), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
    state 0x10, keycode 43 (keysym 0x68, h), same_screen YES,
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by qbanguy on 2007-05-17
I am having a similar issue.My keyword(PS2 port) works fine during startup and bios.However, When the Ubuntu loading screen comes up and starts loading, suddenly the keyword is lock or off or I dont know but it doesnt work. I can't log in or basically do nothing. The funny thing is that the mouse works fine using USB port and I tested out my other desktop USB keyboard and that seems to work fine. I try another PS2 port keyword and it has the same issue. Thanks in advance.

---

### Post by jouni on 2007-05-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/109027](https://bugs.launchpad.net/ubuntu/+bug/109027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I had a similar problem: my PS/2 keyboard worked in BIOS and Grub but not later. The problem occurred on kernel 2.6.20 but not on 2.6.17, and mysteriously went away after I tweaked a USB-related setting in BIOS: for some reason I had disabled USB 2.0 support, and when I turned that on, the keyboard worked again. In some thread it was suggested to disable USB keyboard support and USB mouse support in BIOS, but both were disabled all the time.

The attached Launchpad URL may or may not be related...

---

### Post by qbanguy on 2007-05-18
> **jouni said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/109027](https://bugs.launchpad.net/ubuntu/+bug/109027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

I looked at that bug information and tried out, unfortunately it didn't work. I still have the same issue. I also try other combinations like disable all usb ports in BIOS. - that didnt work. I enabled keyboard support and disconnect mouse. - didnt work. Enabled keyboard support with mouse connected. - didnt work. Finally, Enabled all USB and disble USB keyboard support w/ and w/out connected mouse - it didnt work. Its very strange this bug. I also went into kernel recovery console and the keyword did not work there either. If anyone have other suggestions please I'm open to try anything. :confused:

---

