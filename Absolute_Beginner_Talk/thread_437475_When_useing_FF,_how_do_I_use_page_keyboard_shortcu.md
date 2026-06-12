---
title: "When useing FF, how do I use page keyboard shortcuts?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by SlaughterDog on 2007-05-08
Let's say I were using Windows and IE here, I could just hit alt+s to submit this reply. Or on any webpage rigged with hotkeys. However, in Ubuntu and FF, that just opens my history menu. How do I enable the hotkeys?

---

### Post by Qchan on 2007-05-08
[b][color=darkred]
The hot keys in IE are different than Firefox. Alt S does nothing but open the history menu in both Linux and Windows. There is really nothing to enable here. Just realize that Firefox has different hot keys.

Here is a nice website with a list of hot keys for Firefox.
[http://www.cs.utexas.edu/users/s2s/latest/jaws1/src/hotkeys.html](http://www.cs.utexas.edu/users/s2s/latest/jaws1/src/hotkeys.html)
[/b][/color]

---

### Post by SlaughterDog on 2007-05-08
> **Qchan said:**
> [b][color=darkred]
The hot keys in IE are different than Firefox. Alt S does nothing but open the history menu in both Linux and Windows. There is really nothing to enable here. Just realize that Firefox has different hot keys.

Here is a nice website with a list of hot keys for Firefox.
[http://www.cs.utexas.edu/users/s2s/latest/jaws1/src/hotkeys.html](http://www.cs.utexas.edu/users/s2s/latest/jaws1/src/hotkeys.html)
[/b][/color]

Thing is, it's on the page where the hotkey is. Another reason why I like IE better.

---

### Post by mayamaniac on 2007-06-02
Didn't want to start another thread, so posting in this one.

Is there a way to edit the FF hotkeys? I like to make the backspace key as the BACK button. This is how it is in the windows version of Firefox. I realize that alt-left arrow is the Back keys but I prefer the backspace key.

---

### Post by SlaughterDog on 2007-06-04
> **mayamaniac said:**
> Didn't want to start another thread, so posting in this one.

Is there a way to edit the FF hotkeys? I like to make the backspace key as the BACK button. This is how it is in the windows version of Firefox. I realize that alt-left arrow is the Back keys but I prefer the backspace key.

And I'd like to make my mouse4 button a back button, so when you find out how to do that, if it's not posted here would you tell me via PM or something?

---

### Post by TS28 on 2007-06-04
> **SlaughterDog said:**
> And I'd like to make my mouse4 button a back button, so when you find out how to do that, if it's not posted here would you tell me via PM or something?

I'm wondering the same thing

---

### Post by lazyart on 2007-06-04
not a solution but an idea.  I've used the Mouse Gestures plugin for both Win and Lin.  To navigate backwards or forwards I hold the left button and gesture quickly left or right.

---

### Post by Songwind on 2007-06-05
> **SlaughterDog said:**
> And I'd like to make my mouse4 button a back button, so when you find out how to do that, if it's not posted here would you tell me via PM or something?

Making your 4th (and 5th, etc) mouse buttons show up require editing your xorg.conf file.

Here's an example from mine.  it works with all the buttons on my Logitech MX Laser

```
Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "Buttons" "7"
  option "CorePointer"
  option "Device" "/dev/input/mice"#/dev/input/mice
  option "Protocol" "explorerps/2"
  option "ZAxisMapping" "4 5"
  option "ButtonMapping" "1 2 3 6 7"
EndSection
```

Generally, scroll up/down are 4&5, then 6&7 are back/forward.  Once those are mapped in xorg.conf Firefox should recognize them right away.

---

### Post by SlaughterDog on 2007-06-06
It already recognizes them, but just uses one to scroll (as if I pressed the wheel in) and one to bring up a context menu (as if I right clicked).

I don't know how to edit this.
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```

I also have input devices on there for Wacom tablet, which I used a while ago on Windows before I even had Ubuntu installed. I haven't used it since though.

---

### Post by whistle on 2007-06-06
DISCLAIMER: I'm a Linux n00b.

To put that code in your xorg.conf

First, backup your configuration file```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then open it up in an editor```
gksudo gedit /etc/X11/xorg.conf
```

Change that part with your mouse (the whole section) to```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

Restart computer / restart X

Try it out... if your scroll wheel is doing what your side buttons are supposed to be doing and your side buttons are scrolling, replace the "ZAxisMapping" "4 5" with "ZAxisMapping" "6 7" and "ButtonMapping" "1 2 3 6 7" with "ButtonMapping" "1 2 3 4 5".

Hope this helps.

---

### Post by SlaughterDog on 2007-06-11
I'm going to reply to my origional post for anyone who has asked the same question, you can simply hold alt+shift+key.

---

