---
title: "spacebar doesn't work in Gnome"
date: 2006-11-24
forum: Apple PPC Users
---

### Post by beanworks on 2006-11-24
Hi, I  hope someone can help, or point me where to get help.  I have 6.06 installed on a G4 Powerbook.  I also installed KDE.  Yesterday the spacebar stopped working in Gnome, but works fine at the login screen and in KDE (which I'm using now).

I downloaded and installed some updates while in KDE recently, but I don't remember if the spacebar stopped working before or after the updates.

Has anyone else had this happen? It doesn't work in Terminal, either, which is where I first discovered the spacebar wasn't working:  I kept getting errors for commands, then noticed it wasn't adding spaces between the terms

Is there something I can go to get the spacebar working again?  :(

---

### Post by K.Mandla on 2006-11-25
I don't know how you could manage this, but the xev command will poll the system and wait for keypresses, and show you what's been pressed. It's useful for setting up custom keyboard commands, but could be of use to you here. Start *xev* from a terminal and see if the keyboard is responding at all.

It might also be of use to reconfigure the xserver-xorg package.

```
sudo dpkg-reconfigure xserver-xorg
```
It's possible something got gummed up in there, and reconfiguring it would iron it out. A long shot, but an idea.

---

### Post by beanworks on 2006-11-25
Thanks for the help!  Before I try this:

> 
I don't know how you could manage this, but the xev command will poll the system and wait for keypresses, 

what I've been doing is running commands in the terminal while in KDE, then going to Gnome and using the up arrow to retrieve the command in the terminal there.

> It might also be of use to reconfigure the xserver-xorg package.

will it harm anything to do this in KDE first?

---

### Post by beanworks on 2006-11-25
Well, it's been an amusing morning.

I ran the xev in KDE and got:

```
KeyPress event, serial 28, synthetic NO, window 0x600001,
    root 0x44, subw 0x0, time 521855026, (510,-65), root:(514,4),
    state 0x0, keycode 65 (keysym 0x20, space), same_screen YES,
    XLookupString gives 1 bytes: (20) " "
    XmbLookupString gives 1 bytes: (20) " "
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x600001,
    root 0x44, subw 0x0, time 521855110, (510,-65), root:(514,4),
    state 0x0, keycode 65 (keysym 0x20, space), same_screen YES,
    XLookupString gives 1 bytes: (20) " "
```

Then I ran it in Gnome and noticed something about "sound" instead of "space" so I went to the keyboard shortcut preferences and found under Sound that ctrl+space is the shortcut for play/pause.  I also noticed that alt+space is the shortcut for the windows menu.  So I changed the play/pause shortcut to alt+p and the window menu shortcut to alt+w.  Then the spacebar looked like this in the xev:

```
KeyPress event, serial 26, synthetic NO, window 0x2600001,
    root 0x44, subw 0x0, time 521487589, (188,363), root:(193,412),
    state 0x0, keycode 65 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2600001,
    root 0x44, subw 0x0, time 521487699, (188,363), root:(193,412),
    state 0x0, keycode 65 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
```

So I tried to run the reconfig xserver command, but it wouldn't take the password.  Huh???  So I figured I'd type it out, and copy it and paste into the terminal.  Then I discovered the "p" key isn't working anymore (p is one of the letters in my password).](*,) So I went back to the keyboard shortcuts and changed the pause/play shortcut again to something that** isn't** in my password, and tried again.  No good.

O.K., back to KDE, type out the commands, save the file and go back to Gnome to paste them into the terminal.  It started the configuration, but I got stuck on identifying the PCI bus path.  I tried looking in the devices manager, but it doesn't include that level of detail (at least as far as I could find).  

Help?  :(

---

### Post by stalefries on 2006-11-28
It seems that your control key may be causing issues.

---

### Post by beanworks on 2006-12-01
I think Gnome's just broken.  I can't even get into it any more.

Maybe I should just reinstall it (Gnome)?  :-k

---

### Post by oldHat on 2008-02-22
Thanks to Beanworks!  I ran into the same problem in 6.10.  

The spacebar would work on an ascii terminal, but not in X/gnome.  Shift-space *did* work, though.

It just turned out to be a shortcut issue.

I opened "keyboard shortcuts" and found that the spacebar was a shortcut for pause.  After I changed the shortcut, my problems went away.

---

