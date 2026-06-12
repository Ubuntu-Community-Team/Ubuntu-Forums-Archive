---
title: "Cant use the letter 'd' in terminal."
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by embee on 2006-10-28
Hi,

For some reason the letter 'd' doesnt work in my terminal. I cant type with my keyboard and cut and pasting

```
sudo vim /etc/X11/xorg.conf
```
ends up like
```
suo vim /etc/X11/xorg.conf
```

A capital 'D' works though. 

The only editing I've done to this fairly fresh install is some minor tweaking of mouse settings and trying to shut the system beep up.

Regards-

---

### Post by jamyskis on 2006-10-28
Can you type a d in OpenOffice or gedit? It could be that you have a shortcut set in gconf bound to the d key (not SHIFT+D) for whatever reason.

---

### Post by embee on 2006-10-28
No problems in OpenOffice or Firefox.

The crappy thing about this is that I cant edit any files or confs either because my root password has a 'd' in it.

---

### Post by JayTee on 2006-10-28
If you can type a d in OpenOffice have you tried pasting to the terminal from there? Does it strip the letter d out of the pasted string? If you go into System|Preferences|Keyboard what does it show for Keyboard model and Keyboard  layouts? Does it match yours? If it doesn't match your model of keyboard try changing the keyboard model to one that closely matches it or use the Generic one for the number of keys you have i.e. Generic 101, Generic 104 or 105 and make sure the checkbox in the Keyboard layouts is checked. When I setup XGL with Beryl it reset this and deselected my Keyboard layout.

---

### Post by embee on 2006-10-28
Yep, it sure does.

---

### Post by JayTee on 2006-10-28
If you go into System|Preferences|Keyboard what does it show for Keyboard model and Keyboard layouts? Does it match yours? If it doesn't match your model of keyboard try changing the keyboard model to one that closely matches it or use the Generic one for the number of keys you have i.e. Generic 101, Generic 104 or 105 and make sure the checkbox in the Keyboard layouts is checked. When I setup XGL with Beryl it reset this and deselected my Keyboard layout.

---

### Post by embee on 2006-10-28
Thanks for the tips, JT, but unfortunately it didn't work. I have a 105 keyboard, and that was what I started out with. I did try other layouts aswell though, but they didnt work either.

I have changed my root password now so I can edit configs if necessary.

---

### Post by embee on 2006-10-28
So I tried to remember all the changes I had done. 

I had added and/or uncommented

```
# do not bell on tab-completion
# set bell-style visible
``` in [FONT="Courier New"]/etc/inputrc[/FONT]

Why did one of those (or both) screw everything up?

---

### Post by JayTee on 2006-10-28
I honestly don't know why that would screw it up. Does commenting it out again or commenting anything you added and then hitting Ctrl-Alt-Backspace to restart your X-Server restore the keyboard to normal functionality?

---

### Post by embee on 2006-10-28
I did some troubleshooting and it was definately ```
do not bell on tab-completion
``` that gave me a hard time while enabled.

---

### Post by JayTee on 2006-10-28
Glad you got it sorted out. Weird how that broke it! Then again there are so many things to learn about this OS and all it's intricacies that I think I'll still be a noob a decade from now. :D  But then that's part of the fun for me.

---

