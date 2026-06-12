---
title: "Mouse Button Emulation"
date: 2004-12-25
forum: Apple PPC Users
---

### Post by naventus on 2004-12-25
So I went through the old threads and basically the suggestion was to use f11 or f12. I was wondering if anyone had successfully gotten ctrl-click to work (I'm on an ibook g4). Sources through google all seem to point that mouseemu can do this, but looking at the config file (/etc/default/mouseemu), it doesn't seem to be able to do so. Does anyone know of a way to set it up to be ctrl-click? I don't want to use f11/f12 =\. 

Also, mouseemu won't load anymore for some reason. It did before, but now it can't find uinput even though the module is loaded. I'm thinking some broken symlink... Any help for either problem?

---

### Post by Ptero-4 on 2004-12-28
[QUOTE=naventus]So I went through the old threads and basically the suggestion was to use f11 or f12. I was wondering if anyone had successfully gotten ctrl-click to work (I'm on an ibook g4). Sources through google all seem to point that mouseemu can do this, but looking at the config file (/etc/default/mouseemu), it doesn't seem to be able to do so. Does anyone know of a way to set it up to be ctrl-click? I don't want to use f11/f12 =\. 

Also, mouseemu won't load anymore for some reason. It did before, but now it can't find uinput even though the module is loaded. I'm thinking some broken symlink... Any help for either problem?[/QUOTE]
 To set up ctrl-click go to /etc and as root open sysctl.conf. in the line dev/mac_hid/mouse_button3_keycode change the 88 (F12) with 29 (ctrl), save it, run sysctl -p, and your done.

---

### Post by Laf on 2004-12-29
> **To set up ctrl-click go to /etc and as root open sysctl.conf. in the line dev/mac_hid/mouse_button3_keycode change the 88 (F12) with 29 (ctrl), save it, run sysctl -p, and your done.**

I've tested.

In fact it works... NOT ! ;o) It just replace the "Ctrl" by the left-click not "ctrl+click".

What we would like is :
Click = left click
Ctrl+Click = Right Click
Alt (or Apple)+Click = Middle Click

---

### Post by adamw on 2005-01-27
**>To set up ctrl-click go to /etc and as root open sysctl.conf. in the line dev/mac_hid/mouse_button3_keycode change the 88 (F12) with 29 (ctrl), save it, run sysctl -p, and your done.**
I don't see how this will do any good.  I need that control key continually to do command-line shortcuts and epiphany shortcuts, not to mention cut and paste.  Too bad the F12 key isn't a little easier to reach.  Maybe I'll eventually get the hang of it.

---

### Post by adamw on 2005-02-03
I tried this tip I found in the ubuntu bugzilla site.  This maps the middle mousebutton and the right mousebutton to fn-option and fn-command (on a powerbook or ibook):
(change in /etc/sysctl.conf as root):

dev.mac_hid.mouse_button3_keycode=126
dev.mac_hid.mouse_button2_keycode=100

---

### Post by ewaldgroup on 2005-02-05
Check out my thread. I successfully remapped the Ctrl key to the apple key. make sure that you get it back to stock before you do it though.

[http://ubuntuforums.org/showthread.php?t=13640](http://ubuntuforums.org/showthread.php?t=13640)

-ewaldgroup

---

### Post by adamw on 2005-02-07
[I]Check out my thread. I successfully remapped the Ctrl key to the apple key. make sure that you get it back to stock before you do it though.

[http://ubuntuforums.org/showthread.php?t=13640](http://ubuntuforums.org/showthread.php?t=13640)

-ewaldgroup[/I] 

Thanks, but I like my command and control keys where they are.  I use the command-line about nine hours a day on mac os x and linux, and that means I need the control key to be consistently in the same place to keep my sanity.

---

### Post by t.rei on 2005-02-07
hm... I still havent found a way to get those Ctrl+Mouse things to work. Is anyone here getting smewhere? I would like it to work like that. So far I just use fn+alt to do a right click in case I dont have a mouse attached.

---

### Post by jnoreiko on 2005-02-09
[QUOTE=naventus]I was wondering if anyone had successfully gotten ctrl-click to work (I'm on an ibook g4).[/QUOTE]

This is something that should work on a basic install. :(

---

### Post by adamw on 2005-02-10
Yes, it should.  There is a bug open for this in bugzilla.ubuntu.com:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=5895](https://bugzilla.ubuntu.com/show_bug.cgi?id=5895)

Perhaps if more Mac hardware users speak up, it will be in the Hoary release. But I'm starting to like hitting fn-Command instead of control-click, especially when I'm drinking coffee and only have one hand free.

---

