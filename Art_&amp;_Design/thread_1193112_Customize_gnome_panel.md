---
title: "Customize gnome panel"
date: 2009-06-21
forum: Art &amp; Design
---

### Post by murollubi on 2009-06-21
Hello all!!
I am trying to change customize my gnome panel, I want it unexpanded, but I would like not to see any button on the edge. I mean, I don't want hide buttons, or arrows. Does anybody know how can I do?
thanks everyone

---

### Post by mhgsys on 2009-06-21
Right click a panel, Choose properties.
It's all there in the General tab.

---

### Post by Sand &amp; Mercury on 2009-06-21
Everyone's tried this and it's just really difficult. Thne best you can do to get a decent "not expanded" look is to keep the panel set to expanded, move all your items closer to the middle, and fire up GIMP and make a background for the panel where the sides are transparent. This does the most convincing job, but having your tray icons near the side can sometimes push items 'off' the panel. Unfortunately though, that's about the best you can do.

---

### Post by Giant Speck on 2009-06-21
> **murollubi said:**
> Hello all!!
I am trying to change customize my gnome panel, I want it unexpanded, but I would like not to see any button on the edge. I mean, I don't want hide buttons, or arrows. Does anybody know how can I do?
thanks everyone

There's really no way to remove those buttons because if they weren't there and your panel was completely filled up with applets, you wouldn't be able to right-click the panel and go to properties because you'd end up clicking on an applet.

What you can do, though, is use a panel background image that gives the illusion that your panel is unexpanded.

Here is an example:

[[IMG]http://img154.imageshack.us/img154/6823/screenshot33.th.png[/IMG]](http://img154.imageshack.us/img154/6823/screenshot33.png)

The panel background image is transparent on the sides to make it look as though the panel isn't expanded all the way.

---

### Post by murollubi on 2009-06-21
Hello all again.
First of all give all of you many thanks for your help. I know I am trying to do something difficult (but I can't understand why Gnome developers haven't solved this issue).
If you see the picture of my desktop you will see I have two panels beside the central AWN dock...I just would like to erase those ugly gray buttons on the edge of the panels.

---

### Post by Sand &amp; Mercury on 2009-06-21
> **murollubi said:**
> Hello all again.
First of all give all of you many thanks for your help. I know I am trying to do something difficult (but I can't understand why Gnome developers haven't solved this issue).
If you see the picture of my desktop you will see I have two panels beside the central AWN dock...I just would like to erase those ugly gray buttons on the edge of the panels.

1. Move all the applets onto one panel.
2. Set the panel to expand.
3. Move the left side applets to the left, right side applets to the right.
4. Set panel to solid colour, 100% transparent.
5. ???
6. Profit

If you're running compiz, you'll still have the problem of shadows on your invisible panel; you can fix it like so. Start ccsm, go to Window Decoration. There's a setting there for 'Shadow windows'; usually it's set to 'any'. Change it so it says this instead:

(any) & ! (type=Dock)

Done and dusted.

---

