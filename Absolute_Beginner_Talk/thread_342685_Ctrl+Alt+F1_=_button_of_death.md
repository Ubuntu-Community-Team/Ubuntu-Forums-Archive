---
title: "Ctrl+Alt+F1 = button of death"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by geo_bio on 2007-01-20
I sometimes press ctrl+alt+f1 on accident, or for whatever other reason since it's similar to other keyboard shortcuts.

However, when I do, it comes up with something like the terminal in full screen. I can't exit from it, and I can't resture the GUI (graphic user interface). When that black screen of death (lookalike) shows up, I've been forced to push the power button.

If I do enter the terminal in full screen via ctrl+alt+f1, is there a way to exit that and** restore it back to normal so I can do everything as usual**? And is there a way to** turn the shortcut off**?

ANSWER: To restore it, press Ctrl+Alt+F7. Thanks everyone!

---

### Post by konst88 on 2007-01-20
ctrl+alt+f7 returns to GUI.

---

### Post by mcduck on 2007-01-20
Well, it's possible to turn virtual terminals off, but there's really no need. You can juts hit Ctrl-Alt-F7 to get back to your desktop :)

---

### Post by BigBob on 2007-01-20
> **geo_bio said:**
> I sometimes press ctrl+alt+f1 on accident, or for whatever other reason since it's similar to other keyboard shortcuts.

However, when I do, it comes up with something like the terminal in full screen. I can't exit from it, and I can't resture the GUI (graphic user interface). When that black screen of death (lookalike) shows up, I've been forced to push the power button.

If I do enter the terminal in full screen via ctrl+alt+f1, is there a way to exit that and** restore it back to normal so I can do everything as usual**? And is there a way to** turn the shortcut off**?

edit your /etc/X11/xorg.conf and use :

Option "DontVTSwitch"

A++

---

### Post by konst88 on 2007-01-20
I think it is important to leave this shortcuts on, in any case of GUI failure, you still can do some things to restore it.

---

### Post by geo_bio on 2007-01-20
Thanks for you help!

---

### Post by grogger13 on 2007-02-22
why don't i get a terminal window, i just get a bunch of colored lines and cant do anything up i go back to GUI

---

### Post by nereid on 2007-02-22
@grogger13
Sure you can. Just log yourself in and then your in a normal terminal, just full screen.

---

### Post by cantormath on 2007-02-22
> **BigBob said:**
> edit your /etc/X11/xorg.conf and use :

Option "DontVTSwitch"

A++

dont do this, just hit ctrl+alt+F7

---

### Post by highneko on 2007-02-22
> **geo_bio said:**
> I sometimes press ctrl+alt+f1 on accident, or for whatever other reason since it's similar to other keyboard shortcuts.

However, when I do, it comes up with something like the terminal in full screen. I can't exit from it, and I can't resture the GUI (graphic user interface). When that black screen of death (lookalike) shows up, I've been forced to push the power button.

If I do enter the terminal in full screen via ctrl+alt+f1, is there a way to exit that and** restore it back to normal so I can do everything as usual**? And is there a way to** turn the shortcut off**?

ANSWER: To restore it, press Ctrl+Alt+F7. Thanks everyone!

Also, you could shutdown from a terminal instead of turning off the power with:
[COLOR="DimGray"]# To shutdown[/COLOR]
sudo shutdown -h now
[COLOR="DimGray"]# To reboot:[/COLOR]
sudo shutdown -r now

---

### Post by cantormath on 2007-02-22
> **highneko said:**
> Also, you could shutdown from a terminal instead of turning off the power with:
[COLOR="DimGray"]# To shutdown[/COLOR]
sudo shutdown -h now
[COLOR="DimGray"]# To reboot:[/COLOR]
sudo shutdown -r now

or
```
sudo poweroff
```

---

### Post by grogger13 on 2007-02-22
I dont think i spelled it out right.

I dont get a blank screen i get a kind of scramlbed screen and the only thing i can do his hit atl+ctrl+F7 to get back into GUI

---

### Post by nereid on 2007-02-22
I think you output is a little bit garbled, if I'm right you could still log in. Just type your username, press return, type in your password, press return again. Then you should be logged in. To get rid of the garbled output the *reset* command should do the trick.

---

### Post by mcduck on 2007-02-22
> **grogger13 said:**
> I dont think i spelled it out right.

I dont get a blank screen i get a kind of scramlbed screen and the only thing i can do his hit atl+ctrl+F7 to get back into GUI
What display card do you have & what resolution are you using? I had to add 'vga=792' to my kernel line in /boot/grub/menu.lst to make my laptop use 1024x768 resolution when not in X, otherwise I got just colored mess when accessing VT's. (I have Mobility Radeon X1600)

---

### Post by dondos on 2008-01-02
> I dont get a blank screen i get a kind of scramlbed screen and the only thing i can do his hit atl+ctrl+F7 to get back into GUI
This is an known bug of version 7.10. You can see more in [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910). The only trick that worked for me, was to add "vga=0" in the kernel line of menu.lst. At least, this gave me a good old 80x25 virtual terminal (even though the fonts look ugly on an LCD flat panel). The value "vga=775" (=1280x1024, 256 colors) worked fine on versions 5.04 and 6.10 (I have a Matrox G550 display adapter).

---

### Post by ~LoKe on 2008-01-02
> **cantormath said:**
> or
```
sudo poweroff
```

Is there anything wrong with...
```
sudo halt
```?

---

### Post by LaRoza on 2008-01-02
@OP In Ubuntu Ctrl + Alt +F1-6 are virtual terminals. F7 gets you back. They are handy to have around.

---

### Post by ~LoKe on 2008-01-02
> **LaRoza said:**
> @OP In Ubuntu Ctrl + Alt +F1-6 are virtual terminals. F7 gets you back. They are handy to have around.

I think 3-6 are mostly useless.  It's rare for me to use any more than two virtual terminals.  I remember you could remove them in Feisty with nano /etc/inittab or something similar, but now that's blank.

---

