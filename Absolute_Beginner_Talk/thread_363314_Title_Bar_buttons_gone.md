---
title: "Title Bar buttons gone"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by tny5357 on 2007-02-16
ok, i installed ubuntu, but i have one problem, i dont have a title bar, where the minimize, maximize and close (x) buttons are, my friend installed ubuntu from the same exact cd and he has the title bar and all the buttons, any help on how to fix this would be greatly appreciated, thx

---

### Post by xpod on 2007-02-16
DO you mean your panel with your windows list and shutdown button etc???
Right click on a panel then "add to panel" and add whatever you`ve lost and anything else you fancy

EDIT:Or are you talking about any app you have open that has missing title bars??

---

### Post by tny5357 on 2007-02-17
anything i open has missing title bar


(sry i meant to say i dont have a title bar in my first post)

---

### Post by mr.v. on 2007-02-17
open a terminal and type 
```
metacity
```
and see if they appear
metacity is the windowmanager for gnome. If it fails to load, that would explain a bit. See if it gives you an error message or not.

---

### Post by tny5357 on 2007-02-17
sry, i didnt mention this earlier, im running beryl and i have title bars in gnome but not in beryl

---

### Post by Spike-X on 2007-02-17
I had this happen a few days ago. Now, let's see if'n I remember how to fix heem...


FIRST!! Backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_<<date ie 20070213>>
```

Then, edit your xorg.conf file:

```
gksudo gedit /etc/X11/xorg.conf
```

In the "Device" section, add the lines:

Option "AddARGBGLXVisuals" "True"
	Option "TripleBuffer" "true"

Save and close. Ctrl-Alt-Backspace to restart Xserver.

---

### Post by tny5357 on 2007-02-17
thanks man, that got it fixed

---

### Post by Tim T on 2007-02-20
> **Spike-X said:**
> I had this happen a few days ago. Now, let's see if'n I remember how to fix heem...


FIRST!! Backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_<<date ie 20070213>>
```

Then, edit your xorg.conf file:

```
gksudo gedit /etc/X11/xorg.conf
```

In the "Device" section, add the lines:

Option "AddARGBGLXVisuals" "True"
	Option "TripleBuffer" "true"

Save and close. Ctrl-Alt-Backspace to restart Xserver.
Yet another helpful user! THX, this has been bugging me for days.

---

### Post by ByeByeM$ on 2007-03-08
I have the same problem but that fix didn't work for me.

---

### Post by spyckotic on 2007-03-17
Just wanted to say thanks, this helped me out.

---

### Post by strumica on 2007-08-28
That didn't work for me, any more ideas how to fix that?

---

### Post by irishbandit on 2007-10-06
Worked thank-you!!!

---

### Post by sevenearths on 2008-02-27
I've tried a lot of these xorg.conf fixes and they still haven't worked for me. On my computer thought it is just the sub windows (things like System > Preference > Appearance windows) that dont have the title bars

Its really annoying because there is a really nice applet that lets you do quick web searches but I can close it down when its open (DeskBar)

---

### Post by sevenearths on 2008-02-29
> **Spike-X said:**
> I had this happen a few days ago. Now, let's see if'n I remember how to fix heem...


FIRST!! Backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_<<date ie 20070213>>
```

Then, edit your xorg.conf file:

```
gksudo gedit /etc/X11/xorg.conf
```

In the "Device" section, add the lines:

Option "AddARGBGLXVisuals" "True"
	Option "TripleBuffer" "true"

Save and close. Ctrl-Alt-Backspace to restart Xserver.

I tried the above but I still can't see the titebar on some windows (DeskBar & System > Preferences > Appearance - as examples).

Any other ideas?

---

### Post by generic_idea_machine on 2008-03-21
System --> Preferences ---> **GL Desktop**

---

### Post by sevenearths on 2008-03-22
> **generic_idea_machine said:**
> System --> Preferences ---> **GL Desktop**

Can't find it! The only thing I've got with desktop in the title is 'remote desktop' :(

---

### Post by sevenearths on 2008-03-22
> **Spike-X said:**
> I had this happen a few days ago. Now, let's see if'n I remember how to fix heem...


FIRST!! Backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_<<date ie 20070213>>
```

Then, edit your xorg.conf file:

```
gksudo gedit /etc/X11/xorg.conf
```

In the "Device" section, add the lines:

Option "AddARGBGLXVisuals" "True"
	Option "TripleBuffer" "true"

Save and close. Ctrl-Alt-Backspace to restart Xserver.

must be the limited spec of my ati that stops this from working :(

---

### Post by ma65p on 2008-04-10
The title bars disappear on me after I installed Compiz (awesome software!!). But after messing around, ubuntu works again. So you can try this, 

open terminal
type 'metacity --replace' (note: there're a space and two dashes before 'replace', not one dash)

I'm not sure what this does but it resets my desktop and all visual effects, so the title bars appear again. You might have to reset your appearance setting.

Cheeer!!!

---

### Post by Kekk0 on 2008-06-03
> **mr.v. said:**
> open a terminal and type 
```
metacity
```
and see if they appear
metacity is the windowmanager for gnome. If it fails to load, that would explain a bit. See if it gives you an error message or not.


Thanks, it worked! :D

---

### Post by aznpower8 on 2008-06-03
i had the same problem as all of you, and yes the replacing the metacity, or turning the effects to none works, but i dont like it, so after some experimenting, i found that normal effects still has a title bar, so i looked for what was different between normal effects and extra and i found that normal has window decorations. so in the end, you just need to turn on window decorations

---

