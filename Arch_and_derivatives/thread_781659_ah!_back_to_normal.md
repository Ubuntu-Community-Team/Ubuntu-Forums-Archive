---
title: "ah! back to normal"
date: 2008-05-04
forum: Arch and derivatives
---

### Post by chucky chuckaluck on 2008-05-04
so, i went nuts installing, first, openbox and thunar, then a bunch of other stuff, including kdemod, and i was even thinking of looking at gnome. i was driving myself nuts. when i get in that state, i start trying to match everything up (when i say 'match', i mean make it all click together. i've been asked "you think that matches?" on more than one occassion). so now, i'm back to xmonad, xterm, terminal apps and only firefox and gimp, out of all those gui apps, remain. no more chasing down the sirens that nearly claimed ulysses.

---

### Post by finferflu on 2008-05-04
I know what you mean. In fact, I have been using Gnome for a couple of months after several months of heavy usage of tiling WMs (and now I'm back home, obviously). 
The problem is that most, if not all, the GUI apps are designed to fit well with floating WMs, and don't behave nicely in tiling WMs. So, you are almost bewitched by the apparent consistency in look and feel, everything seems to fit into place. But it's like a circular argument. 

I'm planning to start learning some programming, and I will try to give my contribution to the GUI interface, I have some confused ideas of what I want to achieve (see [thread](http://bbs.archlinux.org/viewtopic.php?id=42773)), but I believe it will all make much more sense when I sit down with the proper tools in hand.

---

### Post by Barrucadu on 2008-05-04
I've never actually tried a tiling wm, I would imagine it a bit difficult to get used to.

---

### Post by chucky chuckaluck on 2008-05-04
actually, i wasn't thinking so much about lining up the apps as i was thinking about 'the look'. you know, having everything support the overwhelming oddity of my wallpaper. there's always something wrong, like i installed the xfce-terminal just to get the right font (century schoolbook l looks retarded in xterm). 

barrucadu, tiling wm's do take a bit of getting used to, especially as most of them seem to be more keyboard driven. once i got used to them, they made so much more sense to me, particularly when working on a number of apps together. i use xmonad, but awesome is maybe the most popular (at least with uf members). aside from those two, i've enjoyed wmii and dwm (both xmonad and awesome started off as dwm clones and then expanded on their own, if i'm not mistaken). these four, btw, also have the option to use traditional floating mode.

---

### Post by Dr Small on 2008-05-04
Is there any good explanations or guides out there so I could learn to use wmii? I tried it, but I don't know any of the keyboard shortcuts, so I didn't get very far with it..

---

### Post by finferflu on 2008-05-04
There should be a tutorial as soon as you open it. But you can access it anytime by pressing "Alt + a" and selecting "welcome" from the menu. 

Apart from that, "man wmii" is quite comprehensive. wmii hasn't got that many keybindings or even functionalities. It only has what is essential, pure KISS :D

---

### Post by Dr Small on 2008-05-04
Ok, thanks there. That really helped me, and now I can move around in it. But I have 2 questions, if I may ask.

1) How do I close an already opened window.
Surely there must be an easier way to close a window without launching a terminal every time and killing the program.

2) How do you tile the windows in 4 squares?
Currently, I have only been able to tile them vertically, (all of them in a row, on top of each other) on flat on top of each other.

Having those answers would definately make it a better expirence :)


Edit:
I hate to double post, so I'll just edit it...
I went through the .wmii-3/ directory, and in the wmiirc file, I found the shortcut to close a window, and it is:
MODKEY-Shift-c

So, That is figured out. Also, I found out how to move the windows around into a square, so that is nice. :)

I added my own shortcut to launch firefox while I was there!

Dr Small

---

### Post by finferflu on 2008-05-04
Well, you have solved your problems, however, since we're talking about this, here is the shortcut list from the wmii manpage:

```

   DEFAULT KEY BINDINGS
   Moving Around
       Key                                                                Action
       Mod-h                                                              Move to a window to the left of the one currently focused
       Mod-l                                                              Move to a window to the right of the one currently focused
       Mod-j                                                              Move to the window below the one currently focused
       Mod-k                                                              Move to a window above the one currently focused
       Mod-space                                                          Toggle between the managed and floating layers
       Mod-t tag                                                          Move to the view of the given tag
       Mod-[0-9]                                                          Move to the view with the given number

   Moving Things Around
       Key                                                                Action
       Mod-Shift-h                                                        Move the current window window to a column on the left
       Mod-Shift-l                                                        Move the current window to a column on the right
       Mod-Shift-j                                                        Move the current window below the window beneath it.
       Mod-Shift-k                                                        Move the current window above the window above it.
       Mod-Shift-space                                                    Toggle the current window between the managed and floating layer
       Mod-Shift-t tag                                                    Move the current window to the view of the given tag
       Mod-Shift-[0-9]                                                    Move to the current window to the view with the given number

   Miscellaneous
       Key                                                                          Action
       Mod-m                                                                        Switch the current column to max mode
       Mod-s                                                                        Switch the current column to stack mode
       Mod-d                                                                        Switch the current column to default mode
       Mod-Shift-c                                                                  Kill the selected client
       Mod-p program                                                                Execute program
       Mod-a action                                                                 Execute the named action
       Mod-Enter                                                                    Execute an xterm

```

---

### Post by chucky chuckaluck on 2008-05-06
apparently, i can't control myself...

---

### Post by finferflu on 2008-05-06
Well, just throw your mouse out of the window, and if you use a laptop, cut the touchpad cable. That should help you stick with a tiling WM.

---

### Post by chucky chuckaluck on 2008-05-06
edit: purity has been restored. let us give thanks.

---

### Post by rjmdomingo2003 on 2008-05-07
> **chucky chuckaluck said:**
> edit: purity has been restored. let us give thanks.
Amen!

---

