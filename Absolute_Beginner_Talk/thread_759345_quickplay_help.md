---
title: "quickplay help"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-04-19
well i have a hp dv1000 and the quickplay buttons are really usefull but there is a problem.. when i click for the music nothing happens, when i click on the dvd rythmbox opens up.. i would want to be able to open amarok.. i dont use rythmbox.. and if possible make it with the respective buttons.
thx

---

### Post by felicity on 2008-04-19
I use Xmodmap to map the keycodes of those media keys to keys ubuntu will understand, then I use openbox to map the new keys to commands I want them to execute (but you can use the default window manager and Keyboard Shortcuts instead). 

First install xmodmap if it isn't installed already:

```
sudo apt-get install xmodmap
```

Then create a .Xmodmap file in your home directory.

Here is what my .Xmodmap file looks like:

```

keycode 236 = XF86Mail
keycode 178 = XF86WWW
keycode 230 = XF86LaunchA
keycode 162 = XF86AudioPlay
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume
keycode 160 = XF86AudioMute
keycode 237 = XF86LaunchC
keycode 235 = XF86PowerOff
keycode 161 = XF86Calculator
```

You need to add your media key codes and the XF86 keys you want to map them to.

If you aren't sure of the keycodes for the media keys you have, start xev in a terminal

```
xev
```

then type the media key you want to find the keycode for, and look for the keycode xev produces in the terminal. You may want to make a note of the keycode for each media key you press so you don't forget it later.

Once you know which keycode goes to which media key you can make your .Xmodmap file like the example above; here's a list of the common media keys you might want to map the keycodes to, but you can also add others if needed with XF86LaunchA, XF86LaunchB, etc...:

```
XF86ModeLock
XF86Standby
XF86AudioLowerVolume
XF86AudioMute
XF86AudioRaiseVolume
XF86AudioPlay
XF86AudioStop
XF86AudioPrev
XF86AudioNext
XF86HomePage
XF86Mail
XF86Start
XF86SplitScreen
XF86Support
XF86Away
XF86Messenger
XF86WebCam
XF86MailForward
XF86Pictures
XF86Music
```

Then just go into the System, Preferences, Keyboard Shortcuts menu and use the XF86Whatever code you mapped to the media key you want to assign a command to execute. If you want to map commands that aren't in the keyboard shortcuts box, you'll have to add them as extras in the Configuration Editor instead (for instance I use XF86LaunchA to open a text file).

---

### Post by patchido on 2008-04-21
> **felicity said:**
> I use Xmodmap to map the keycodes of those media keys to keys ubuntu will understand, then I use openbox to map the new keys to commands I want them to execute (but you can use the default window manager and Keyboard Shortcuts instead). 

First install xmodmap if it isn't installed already:

```
sudo apt-get install xmodmap
```

Then create a .Xmodmap file in your home directory.

Here is what my .Xmodmap file looks like:

```

keycode 236 = XF86Mail
keycode 178 = XF86WWW
keycode 230 = XF86LaunchA
keycode 162 = XF86AudioPlay
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume
keycode 160 = XF86AudioMute
keycode 237 = XF86LaunchC
keycode 235 = XF86PowerOff
keycode 161 = XF86Calculator
```

You need to add your media key codes and the XF86 keys you want to map them to.

If you aren't sure of the keycodes for the media keys you have, start xev in a terminal

```
xev
```

then type the media key you want to find the keycode for, and look for the keycode xev produces in the terminal. You may want to make a note of the keycode for each media key you press so you don't forget it later.

Once you know which keycode goes to which media key you can make your .Xmodmap file like the example above; here's a list of the common media keys you might want to map the keycodes to, but you can also add others if needed with XF86LaunchA, XF86LaunchB, etc...:

```
XF86ModeLock
XF86Standby
XF86AudioLowerVolume
XF86AudioMute
XF86AudioRaiseVolume
XF86AudioPlay
XF86AudioStop
XF86AudioPrev
XF86AudioNext
XF86HomePage
XF86Mail
XF86Start
XF86SplitScreen
XF86Support
XF86Away
XF86Messenger
XF86WebCam
XF86MailForward
XF86Pictures
XF86Music
```

Then just go into the System, Preferences, Keyboard Shortcuts menu and use the XF86Whatever code you mapped to the media key you want to assign a command to execute. If you want to map commands that aren't in the keyboard shortcuts box, you'll have to add them as extras in the Configuration Editor instead (for instance I use XF86LaunchA to open a text file).

it seems that is what i need.. but that is way too advanced for me....

---

