---
title: "[SOLVED] I lost the cube!"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by jjfourtwenty on 2007-10-20
Sorry in advance for this post, I am totally new to ubuntu.
After installing Gutsy and having a play with compiz (yeah I was lured in by the eye candy) I have managed to loose the cube. The last thing I did was to enable the desktop plane and it stated certain plugins would be disabled that are used by the cube. I can't seem to find a a way to enable this plugins once again and I would like the cube back!

any help greatly appreciated.

---

### Post by Pumalite on 2007-10-20
There is another thread in the Forum. It might help:
[http://ubuntuforums.org/showthread.php?t=583131](http://ubuntuforums.org/showthread.php?t=583131)

---

### Post by jjfourtwenty on 2007-10-20
sorry this didn't quite have the right answer. Is it possible to totally remove compiz and start again? also I have just noticed that it will unfold but not go to the rotating cube.

---

### Post by llamakc on 2007-10-20
There's no reason to remove it. Run from the menu SYSTEM | PREFERENCES | ADVANCED DESKTOP EFFECTS SETTINGS.

Uncheck Desktop Plane and check Desktop Cube. If you don't see ADVANCED DESKTOP EFFECTS SETTINGS in your menu, make sure that you have compizconfig-settings-manager installed (in Synaptic or the commandline with apt).

---

### Post by jjfourtwenty on 2007-10-21
Thanks for your help but I do have the cube enabled/checked and window plane is unchecked. 

any other ideas?

---

### Post by overdrank on 2007-10-21
> **jjfourtwenty said:**
> Thanks for your help but I do have the cube enabled/checked and window plane is unchecked. 

any other ideas?

HI and maybe this will help
[http://ubuntuforums.org/showthread.php?p=3560500#post3560500](http://ubuntuforums.org/showthread.php?p=3560500#post3560500)
Good luck!

---

### Post by jjfourtwenty on 2007-10-21
sorry this didn't help either, Its not that I have a flat cube, it's that the cube just wont appear. I cant get the desktops to switch with the standard switcher either. all I can do is unfold the cube with ctrl, Alt and Down.

---

### Post by natman on 2007-10-21
I had the same problem, and did the following, system preference go back to normal effects, them back into custum compiz, see if that works, if not uncheck everything in the visuals, and recheck one at a time, making sure you have enough desktops to merit a full cube

---

### Post by ronmarley1 on 2007-10-21
Also, make sure the Rotate Cube plugin is checked.

---

### Post by llamakc on 2007-10-21
In CompizConfig Settings Manager go to the GENERAL OPTIONS.

Make sure on Desktop Size, you have:

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1

---

### Post by jjfourtwenty on 2007-10-21
sorry still not working. I have the right desktop settings. just cant get the damn cube to appear or rotate also the binding I had for the cube to rotate has disappeared

---

### Post by llamakc on 2007-10-21
Weird. I'm assuming you've tried logging out/in, right? I can give you what my key-bindings are if you'd like. If I were you I would create a second user and try logging in as them to see if it works.

---

### Post by jjfourtwenty on 2007-10-21
Well I had the key bindings set to Ctrl Alt Drag to move the cube (prob a useless combo). I will go try the new user thing right away.

Also I would like to say how great it is to have such support, I really appreciate the community support of all the forum members who are trying to help me out. Even though at times ubuntu can be frustrating in relation to windows, the open source community and cause help me to persevere!

---

### Post by jjfourtwenty on 2007-10-21
Well this is embarrassing, Just hit the middle button on my mouse and hey presto it all works, seems that when I restored the defaults it reset my bindings or something. Anyway I have learnt lots more about compiz and love ubuntu even more!

---

