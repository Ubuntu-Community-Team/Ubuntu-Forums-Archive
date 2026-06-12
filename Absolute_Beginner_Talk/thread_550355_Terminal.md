---
title: "Terminal"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by ATiwolf on 2007-09-13
When I go to applications>assesories>terminalmy computer goes to some kinda fullscreen command prompt looking screen like the one u get when u first start up the computer. I have to re-login and all the stuff i had open prior to clicking terminal is gone.Fire fox says its closed unexpectedly and i get no Terminal window, which is lame.:(

---

### Post by diatribe on 2007-09-13
are you sure the terminal is not just starting maximized?  can you right-click with the mouse?  if not, have you tried hitting ctrl-alt-f7?

---

### Post by seabattle on 2007-09-13
Have you tried alt+F2 and tried running gnome-terminal out of that?

---

### Post by llamakc on 2007-09-13
What post below says. I responded to the responses and not the OP. Thanks bodhi.

---

### Post by bodhi.zazen on 2007-09-13
LOL

I think X is crashing on him (not sure though)

If so it is likely a corrupt file in your home directory.

You can test this hypothesis by making a new user and see if the behavior persists.

If it does not you can debug the first user or transition to the new user as you wish.

---

### Post by ATiwolf on 2007-09-13
I've tried alt f2 and stuff but i keep going to the black screen.It looks kinda like this
Blah blah blah blah [Ok]

Blah blah blah blah [Ok]

Blah blah blah blah [Ok]

Blah blah blah blah [Ok]
then i hit the log in screen
when i press f11 after that i get something like

Blah blah blah blah [Ok]

Blah blah blah blah [Ok]

Blah blah blah blah [Ok]
^$$@$

Kinda like when u press ctrl c or something in windows command line,
I just tried to run the update manager to see if installing updates might help but when i try to download the updates it  says its unable to get system lock orsomething and another package manager is open but im not running anything:confused:

---

### Post by ATiwolf on 2007-09-13
here's a picture of the screen after i blanks out:
[IMG]http://i101.photobucket.com/albums/m53/Atiwolf/screenage.jpg[/IMG]

***The ^[[23" is where i tried typing ctrl+alt+f7

---

### Post by llamakc on 2007-09-14
So, what did you do? Have you tried to enable Desktop Effects? Install a video kernel module (driver) for your card?

At that terminal prompt you could login as your username and run:

sudo dpkg-reconfigure xserver-xorg and reconfigure your xserver (the software that drives the GUI).

---

### Post by bodhi.zazen on 2007-09-14
Yep, dropping out of X alright ...

You can get to an alternate console with Ctrl-Alt-F2

log in

What were you playing with exactly ? does this problem happen with other users ? did you check you logs ?

---

### Post by ATiwolf on 2007-09-14
> **llamakc said:**
> So, what did you do? Have you tried to enable Desktop Effects? Install a video kernel module (driver) for your card?

At that terminal prompt you could login as your username and run:

sudo dpkg-reconfigure xserver-xorg and reconfigure your xserver (the software that drives the GUI).

First, i have know idea how to enable desktop mode.
Second, I am unsure of what GPU . I do know however that it's integrated. This computer was given to me with the hard drive wiped and i don't know how to check my hardware without using Xp.

[QUOTE=bodhi.zazen]You can get to an alternate console with Ctrl-Alt-F2

log in

What were you playing with exactly ? does this problem happen with other users ? did you check you logs ?[/QUOTE]

I haven't tried that command yet i will be sure to try it,thanks.
I also haven't set up a separate user account yet to see if i could fix it.I just reinstalled xubuntu altogether..but it didn't help.So i'll be trying that as well.:smile:
Thanks for all the great suggestions so far..ill get back with you in a while.

---

### Post by ATiwolf on 2007-09-14
WOW today must be my day!! That ctrl+alt+f2 thing worked...But once i got in i didn't know how to get out LOL; the Dos Command line "exit" apparently doesn't work in Linux:) Will i be able to run all commands in that fullscreen mode or am i only able to run certain commands in the Gui?

I also was able to install updates for xubuntu! I was so fixed on downloading and installing A firewall and other security software that it hadn't occurred to me that firestarter might be blocking linux from getting to the servers that run the updates. But in any case a reinstall fixed that little problem

---

### Post by Majorix on 2007-09-14
> **ATiwolf said:**
> But once i got in i didn't know how to get out LOL; the Dos Command line "exit" apparently doesn't work in Linux:)

You have to type
```
quit
```
instead.

---

### Post by Tyke91 on 2007-09-14
to check your hardware from a linux command prompt (shell), type

```
sudo lshw
```

---

### Post by ATiwolf on 2007-09-14
Thx guys

---

### Post by ElTimo on 2007-09-14
i figured it out! when you get into terminal, press f11. that's all!

(somebody may have said this already, but i dont care. i did my good deed for the day :-P)

---

