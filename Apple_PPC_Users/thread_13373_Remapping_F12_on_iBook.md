---
title: "Remapping F12 on iBook"
date: 2005-01-31
forum: Apple PPC Users
---

### Post by ewaldgroup on 2005-01-31
I have a 2001 iBook G3. I just installed Ubuntu on it. is there any way to keep OS X type keyboard shortcuts on Ubuntu so when i switch to Ubuntu from OS X i dont get completly confused? For example:

[INDENT]Apple Key -> W    =    Close Window[/INDENT] 
[INDENT]Apple Key -> M    =    Minimize Window[/INDENT] 
[INDENT]Apple Key -> C    =    Copy Text[/INDENT] 
[INDENT]Apple Key -> V    =    Paste Text[/INDENT] 

I installed powerprefs and got those keys working.
Is there any way to map "fn" Key F12 (right click) to something else? sugestions?
I would also like the power button to display the logout screen. Is this possible?

Thanks for your help.

-ewaldgroup

---

### Post by Viro on 2005-01-31
[QUOTE=ewaldgroup]I have a 2001 iBook G3. I just installed Ubuntu on it. is there any way to keep OS X type keyboard shortcuts on Ubuntu so when i switch to Ubuntu from OS X i dont get completly confused? For example:

[INDENT]Apple Key -> W    =    Close Window[/INDENT] 
[INDENT]Apple Key -> M    =    Minimize Window[/INDENT] 
[INDENT]Apple Key -> C    =    Copy Text[/INDENT] 
[INDENT]Apple Key -> V    =    Paste Text[/INDENT] 

I installed powerprefs and got those keys working.
Is there any way to map "fn" Key F12 (right click) to something else? sugestions?
I would also like the power button to display the logout screen. Is this possible?

Thanks for your help.

-ewaldgroup[/QUOTE]
 You could get Linux to treat the Apple key as if it were the ALT key. Just do the following. In the terminal. 
> 
sudo xmodmap -e 'keycode 115 = Alt_L'

sudo xmodmap -e 'add mod1 = Alt_L'

If that works, you can make the changes permanent, by editing the file /etc/X11/Xmodmap (by typing 'sudo gedit /etc/X11/Xmodmap' in the terminal. Add the following entries to that file.
> 
keycode 115 = Alt_L
add mod1 = Alt_L


That should work.

Don't know about the rest.

---

### Post by ewaldgroup on 2005-01-31
Is there any way to remap the ctrl key to say the apple key? Is there a list of the key codes that i can use to make my changes?

Thanks for your help.

-ewaldgroup

---

### Post by ewaldgroup on 2005-02-01
any ideas?

-ewaldgroup

---

### Post by ewaldgroup on 2005-02-01
[QUOTE=Viro]You could get Linux to treat the Apple key as if it were the ALT key. Just do the following. In the terminal. 

If that works, you can make the changes permanent, by editing the file /etc/X11/Xmodmap (by typing 'sudo gedit /etc/X11/Xmodmap' in the terminal. Add the following entries to that file.


That should work.

Don't know about the rest.[/QUOTE]

Didn't seem to work. as far as i can tell it didnt change anything. Someone else must have the same problem that I do please help! Once again I want the Ctrl key to be the right click emulator and the apple key to take the place of the ctrl key.

-ewaldgroup

---

### Post by Viro on 2005-02-01
[QUOTE=ewaldgroup]Didn't seem to work. as far as i can tell it didnt change anything. Someone else must have the same problem that I do please help! Once again I want the Ctrl key to be the right click emulator and the apple key to take the place of the ctrl key.

-ewaldgroup[/QUOTE]
 Did you log out and restart?

---

### Post by ewaldgroup on 2005-02-01
i did the first part but not the second, thinking that the first part would change it during the session and editing the text files would change it for future sessions. Was I wrong?

To answer your question, I did log out and restart, after reading your post. Nothing changed.

Is there any way that I could find out the keycodes for various keys, say the ctrl and power keys? the method mentioned here: [http://www.yellowdoglinux.com/support/solutions/ydl_general/mouse_buttons.shtml](http://www.yellowdoglinux.com/support/solutions/ydl_general/mouse_buttons.shtml)
 gave seemed to give me output, but i couldnt figure out how to stop it. it launched many firefox windows and took a good 3 min to recover from. i would encourage you to try it, but make sure you save important files beforehand.

Thanks for trying to help...  I just want the apple key to function like it does in osx, how can that be so hard???

Thanks,
ewaldgroup

---

### Post by Viro on 2005-02-01
I guess it's going to be hard. Ever tried getting the CTRL key to replace the Apple key on OS X? :)

You could download this app called Powerprefs. it allows you to change some key bindings to the volume control, eject key, etc. However, that is not of interest to you. What is of interest is that it shows the keycodes. And it doesn't crash. So you might want to have a go at that.

Sorry I'm not able to help much more though.

---

### Post by ewaldgroup on 2005-02-01
I downloaded and installed powerprefs. I never through of using it just to find the keycodes. that with the trick you sugested should work. I'll get back to you after i give it a try.

Thanks,
ewaldgroup

---

### Post by adamw on 2005-02-03
*You could download this app called Powerprefs. it allows you to change some key bindings to the volume control, eject key, etc. However, that is not of interest to you. What is of interest is that it shows the keycodes. And it doesn't crash. So you might want to have a go at that.* 
I tried installing powerprefs and instantly lost 90% of the keys on my keyboard (i.e. if you hit them nothing would happen).  Powerprefs is an insidious, insidious little app which caused my Mac to lose all notion of sanity.  I had to zap the PMU to get my normal keymappings back.  Bad program! Bad!

---

### Post by t.rei on 2005-02-03
I have no problems here with powerprefs... but as for keycodes:
 
 a) to generate a nice list of lots and lots of keycodes: run xkeycaps and select a keyboard like pc105 and then save to a file. read and search for what you need.
 
 If you want to find out about what keycode goes on what key currently: run xev from a teminal and press the key you want to find out about. Somewhere in all the output will be the keycode:
 
  ```
KeyRelease event, serial 29, synthetic NO, window 0x2a00001,
	root 0x41, subw 0x0, time 109099589, (500,509), root:(503,532),
	state 0x0, keycode 52 (keysym 0x79, y), same_screen YES,
	XLookupString gives 1 bytes: (79) "y"
``` 
 
 like this "y" key for me ;)

---

### Post by ewaldgroup on 2005-02-03
I did that. My other thread is here. please take a look:
[http://www.ubuntuforums.org/showthread.php?t=13640](http://www.ubuntuforums.org/showthread.php?t=13640)

ewaldgroup

---

