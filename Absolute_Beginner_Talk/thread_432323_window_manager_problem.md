---
title: "window manager problem"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2007-05-03
i am having a problem with gnome on feisty everything was fine then i cannot close or minimize the windows
when i go to preferences>windows i get this message "cannot start preferences application  ffor your window manager. window manager "uknown"has not registered a configuration list.

---

### Post by abu-fatu on 2007-05-04
any suggestions i re install ubuntudesktop thru synaptic still same problem

---

### Post by Metacarpal on 2007-05-05
Are you using any special visual add-ons like "Desktop Effects"/Compiz/Beryl?

If not, try this: press alt-F2 - this will open a "Run Application" box.  Type in:
```
metacity --replace
```

Based on the message you got:
> window manager "uknown"has not registered a configuration list
it sounds like you don't have a window manager running.  Restarting metacity as I indicated above should fix the problem.

If that takes care of it for you, go to your System menu > Preferences > Sessions
In there, under the "Session Options" tab, make sure that "Automatically save changes to session" is checked.

---

### Post by digitalramble on 2007-05-11
I've had this happen twice in the last two days now.  While metacity does fix it, why is this happening in the first place, anyone know?

---

### Post by dajashby on 2007-05-13
This has just happened to me on a pc that hasn't run ubuntu for a couple of weeks.  The metacity fix fixed it, so thanks for that.  Any further ideas on what the problem might be/have been?

---

### Post by QwUo173Hy on 2007-05-14
I also have this problem with 1 in 4 logins. I tried the Desktop Effects when I upgraded to Feisty. They didn't work and disabled itself. Ocassionally when I log in I have no window manager. It's a little annoying.

A (sloppy) way to fix this would be to go to System -> Preferences -> Sessions and add "metacity -replace" to the program list.

---

