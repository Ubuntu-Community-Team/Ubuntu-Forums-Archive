---
title: "OK I give up on workspaces and window sizes"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by andyni on 2007-05-30
Here we are with Feisty installed on trusty old laptop. My last linux machine lasted a few months before I gave up and bought a new MS Windows machine. Basically I got sick of mucking around with it, installing new applications to do stuff, and being totally unable to find them in the application start menus or get advice on how to get the application to appear there so that it could actually be used.

Ubuntu is much more user-friendly and I now have a chance of finding the application I want to use. Today I actually did some real work with it, rather than just browsing around and reading The Fark.

I do have one serious issue, however. My last linux machine ran FVWM or similar, and had a virtual desktop size of something like twice the size of the monitor. This allowed me to view more than one app by scrolling the mouse off the edge of the monitor, and watch the workspace roll around underneath.

Is it possible to achieve this in Gnome? I'm again working on a small screen of only 800x600 resolution which I can't push any higher because it's the flat panel fitted to the laptop.

I've had a trawl around the forum and some other people seem to have the same issue as me, once in a while a window turns up that's bigger than the viewable area, and for some reason you can't resize it and get a scroll bar, and you can't move the top of the window off your screen to get to the options buttons etc at the bottom of the form. Leaves you with only one option of giving up and closing the window.

I suppose the other way to deal (this was also available on my previous Linux machine) was to allow the window to run accross the boundary between workspaces, so part of the window would be visible in one workspace and part in another. this doesn't seem to be included as default behaviour in Gnome either, and I can't find a way of making it happen.

Any ideas?

Sincerely
Mr. Count me as a complete noob.

---

### Post by jfinkels on 2007-05-30
> **andyni said:**
> Here we are with Feisty installed on trusty old laptop. My last linux machine lasted a few months before I gave up and bought a new MS Windows machine. Basically I got sick of mucking around with it, installing new applications to do stuff, and being totally unable to find them in the application start menus or get advice on how to get the application to appear there so that it could actually be used.

Ubuntu is much more user-friendly and I now have a chance of finding the application I want to use. Today I actually did some real work with it, rather than just browsing around and reading The Fark.

I do have one serious issue, however. My last linux machine ran FVWM or similar, and had a virtual desktop size of something like twice the size of the monitor. This allowed me to view more than one app by scrolling the mouse off the edge of the monitor, and watch the workspace roll around underneath.

Is it possible to achieve this in Gnome? I'm again working on a small screen of only 800x600 resolution which I can't push any higher because it's the flat panel fitted to the laptop.

I've had a trawl around the forum and some other people seem to have the same issue as me, once in a while a window turns up that's bigger than the viewable area, and for some reason you can't resize it and get a scroll bar, and you can't move the top of the window off your screen to get to the options buttons etc at the bottom of the form. Leaves you with only one option of giving up and closing the window.

I suppose the other way to deal (this was also available on my previous Linux machine) was to allow the window to run accross the boundary between workspaces, so part of the window would be visible in one workspace and part in another. this doesn't seem to be included as default behaviour in Gnome either, and I can't find a way of making it happen.

Any ideas?

Sincerely
Mr. Count me as a complete noob.

One solution to this problem is pressing and holding the <Alt> button while clicking and dragging anywhere in the area of the window to move it. This is one of the greatest things we have over Windows :). 

Although this may not be what you're looking for exactly, we do have virtual workspaces! Press <Ctrl>+<Alt> and <Left> or <Right> to switch workspaces. If the little applet isn't on your panel, right click on the panel, select "Add to Panel..." and choose "Workspace Switcher".

---

### Post by starcraft.man on 2007-05-30
I just checked and fvwm is in our repos... so I guess you can install it thusly:

```
sudo aptitude install fvwm
```

There is also a crystal version (fvwm-crystal) and Gnome one (fvwm-gnome). Pick whichever one you want.

If you don't want to use Terminal, System > Adminstration > Synaptic package manager > Search > fvwm

That should get you a list of the packages, pick the one you want, I assume you know which one you were using before.

That said, your on your own after that, I don't know how to use/configure it (yet, will try it another day) :).

Off I go, question has been answered I believe. Have fun with it :D.

Edit: Oh and in the odd case its not in the main repos and you don't find it, [follow this guide for adding the extra repos you need.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

