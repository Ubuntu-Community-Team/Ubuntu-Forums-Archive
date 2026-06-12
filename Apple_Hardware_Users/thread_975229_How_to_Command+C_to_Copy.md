---
title: "How to Command+C to Copy"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by timchesonis on 2008-11-08
I have a Mac, and now I've switched over to Ubuntu.  I use the Command+C, Command+V (Copy and paste), all the time.  I hate using CTRL+C, CTRL+V, etc.  How do force Ubuntu to recognize my Command Key instead of the CTRL key when copying and pasting?

---

### Post by SaltySurfer on 2008-11-08
looks like keyboard re-mapping was covered here: [http://ubuntuforums.org/showthread.php?p=1943304](http://ubuntuforums.org/showthread.php?p=1943304)

---

### Post by timchesonis on 2008-11-08
> **SaltySurfer said:**
> looks like keyboard re-mapping was covered here: [http://ubuntuforums.org/showthread.php?p=1943304](http://ubuntuforums.org/showthread.php?p=1943304)

I honestly read this, and tried changing the compose key, but could not make sense of it.  I just want to make my Mac Command key the CTRL key.  In other words, any time Ubuntu requires me to use the CTRL key, I want it to use the Command key.  Simply to substitute the CTRL key for the Command key.

---

### Post by crapple on 2008-11-08
Try keyboard short cuts in preferences.

---

### Post by timchesonis on 2008-11-08
> **crapple said:**
> Try keyboard short cuts in preferences.

I looked there first.  There no "shortcut" available for the COPY command.

---

### Post by bryonak on 2008-11-09
The first thing that comes to mind is xbindkeys with xkbd.
This lets you map any key/button you can press on your computer with any other key/button/script/application, so it will work for sure. The drawback is that a bit of work is needed, for example finding out what the key combos are via 'xev'. If you don't feel uncomfortable with the terminal, that's the way to go.

The other solution is to open System -> Preferences -> Keyboard and there go to Layouts -> Other Options. This will let you change a lot of quirky things, and you can swap your ctrl and command keys completely.
But IMO this interface is quite bad, you have to make sense of it yourself... and it may not have the possibility for swapping the two keys for copy&paste only.

---

### Post by Jæd on 2008-11-10
The option to use appears to be:

"Alt / Win Key Behaviour"

"Control is mapped to the Win-keys"

---

### Post by cyberdork33 on 2008-11-10
> **Jæd said:**
> The option to use appears to be:

"Alt / Win Key Behaviour"

"Control is mapped to the Win-keys"
That sounds right. They should rename "Win-Key" to the "Super Key" as that is how it is really designated in Linux... (i.e. The command key and the Win key are seen as the same thing to Ubuntu).

---

### Post by stream303 on 2008-11-10
This is what works for me on my G5 PPC iMac running Intrepid..

Create a hidden file in your home directory, .Xmodmap

```
remove control = Control_L Control_R
clear mod4
keycode 115 = Super_L Super_L
keycode 116 = Super_R Super_R
add control = Super_L Super_R
```

Be careful with your R's and L's.  Then logout and back in, or reboot...

I went nuts with this a few years ago, and an emacs-guy gave me the tip for the clear mod4.  Part of the reason I use vi. :)

---

### Post by cyberdork33 on 2008-11-10
> **stream303 said:**
> I went nuts with this a few years ago, and an emacs-guy gave me the tip for the clear mod4.  Part of the reason I use vi. :)

I don't like either of them myself :)

---

### Post by bryonak on 2008-11-11
nano for the win... err let's return to the topic ;)

Have you tried any of these suggestions timchesonis?

---

### Post by timchesonis on 2008-11-14
> **stream303 said:**
> This is what works for me on my G5 PPC iMac running Intrepid..

Create a hidden file in your home directory, .Xmodmap

```
remove control = Control_L Control_R
clear mod4
keycode 115 = Super_L Super_L
keycode 116 = Super_R Super_R
add control = Super_L Super_R
```

Be careful with your R's and L's.  Then logout and back in, or reboot...

I went nuts with this a few years ago, and an emacs-guy gave me the tip for the clear mod4.  Part of the reason I use vi. :)

I have done as you have suggested above, however, it's not "copying", when I hold the Command key & C Key to copy, and I need to paste as well.

Can you modify the lines of code abave to allow for copying AND pasting? Ideally, Command Key + C, and Command Key + V

This would be so helpful.  Thanks for helping out this far.

---

### Post by _mario_ on 2008-11-14
> **timchesonis said:**
> I have done as you have suggested above, however, it's not "copying", when I hold the Command key & C Key to copy, and I need to paste as well.

Can you modify the lines of code abave to allow for copying AND pasting? Ideally, Command Key + C, and Command Key + V

This would be so helpful.  Thanks for helping out this far.
i think the proper way of doing so is:
```
!
! xmodmap script to swap left control & command keys
!
remove control   = Control_L
remove mod4      = Super_L Hyper_L
keysym Control_L = Super_L Hyper_L
keysym Super_L   = Control_L
add    control   = Control_L
add    mod4      = Super_L Hyper_L

! ***** end of source *****

```
(see man xmodmap.) this script completely swaps the left control and command key (for all uses not just copy and paste) without breaking compiz shortcuts.

simply put this code in a file called .xmodmap in your home directory (to be executed upon login) or call:
```
xmodmap .xmodmap
```

if you break your keyboard layout while playing around, you can use this command to revert back (the actual arguments might be different):
```
setxkbmap -layout de -variant mac_nodeadkeys
```

ciao,
Mario

---

### Post by timchesonis on 2008-11-14
Well, unfortunately, that didn't work.  When logging out and then logging back in, I lost some of my Gnome look and feel, plus when typing "test" in textpad, and holding the command key down while hitting the "C" key, and then letting go, and then holding the Command key down and hitting the "V" key, . . . all it did was bring my mouse cursor to the center of the screen.

---

### Post by hanzomon4 on 2008-11-15
It's not that hard, just go into system>preferences>keyboard.
Click layouts, highlight your layout and click more options. Then click alt/win behavior and select "control is mapped to the win-keys"

---

### Post by stream303 on 2008-11-15
> **timchesonis said:**
> Can you modify the lines of code abave to allow for copying AND pasting? Ideally, Command Key + C, and Command Key + V

Strange, it works for me.  However, I have only tried it in Gedit, Abiword, and OpenOffice.  Is it not working for you in these programs?

(I just tested and it isn't working in a terminal...)

I'll bet there are some more mods necessary, but I stopped when it was working in these programs.  Is the keyboard Apple oem, and are you running Intrepid?  I've only tested this in Intrepid...

---

### Post by _mario_ on 2008-11-15
> **timchesonis said:**
> Well, unfortunately, that didn't work.  When logging out and then logging back in, I lost some of my Gnome look and feel, plus when typing "test" in textpad, and holding the command key down while hitting the "C" key, and then letting go, and then holding the Command key down and hitting the "V" key, . . . all it did was bring my mouse cursor to the center of the screen.
i mentioned that it *completely* swaps those keys. that means you have to press Control+T for actions that formerly were Command+T, e.g. to launch a terminal from your window manager by keyboard shortcut. likewise Command+C is now Control+C, and so on. if the cursor now jumps to the middle of the screen (accessibility settings allow that) by pressing Command+V, there must have been a feature that does so by pressing Control+V before. did you fiddle around with keyboard and accessibility options and enabled something you (and we) don't expect. i agree with stream303. there is something really strange...

ciao,
Mario

---

### Post by stream303 on 2008-11-15
Right - command-T now brings up a new tab in Firefox like it's suppose to, etc.

I wonder if it is a keyboard issue - I'm using an American Apple usb keyboard - I wonder if his is International or third party which may need different keycodes etc.

Sure wish I was a keyboard expert - which I'm not unfortunately. :)

---

