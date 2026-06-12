---
title: "Can someone explain to me the interaction of Linux conventions?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by bocmaxima on 2006-07-10
I just spent some time in Wikipedia, which helped for some things, but not others. How do the parts of Linux work together?

The Kernel interacts with the hardware, the Shell interacts with the Kernel, and the Xserver controls Gnome which is GUI commands for the shell?

Is there something more brief than Wikipedia to explain this stuff, like a glossary?

Then how does Xgl and Compiz work? With the Xserver or Gnome, or both?

Maybe these are stupid questions, but would definately help me.

---

### Post by Zimmer on 2006-07-10
[http://www.linuxnewbieguide.org/](http://www.linuxnewbieguide.org/)
Good place for reliable info...
and the Tuxfiles link in my sig for some helpful tutorials etc...
(No idea of the Xgl/compiz relationship,myself. Still a Breezy user.

---

### Post by Crosbie on 2006-07-10
Xgl is a type of X server - like X.org, Xfree86 etc.  Compiz sits atop Xgl and just displays windows etc on the screen - replacing Metacity I think.  Gnome controls a range of things - file browsing programs, the icon set you use, and so on.

I have Xgl - Compiz - Gnome on my current Ubuntu setup, and it's very whizzy and pretty.

---

### Post by wylfing on 2006-07-10
These aren't really "Linux conventions." Windows has the same parts: a kernel, a shell, a window manager, etc. It used to be easier to understand this about DOS/Windows years ago. For example, everyone used to understand that your shell was COMMAND.COM.

But anyway, here is a rough idea of the major pieces.

[LIST]
[*]The kernel is like the foundation. Everything builds on top of that.
[*]A shell is simply a command interpreter, so that when you type "ls" in a terminal it does something sensible. (Actually shells do a bit more, but that's pretty good for a simple explanation.) 
[*]X Windows provides a graphical environment, but sticks to fairly primitive functionality, e.g., this is a mouse click, this is a cursor. 
[*]More sophisticated GUI work is handled by what are called windowing managers such as Metacity, IceWM, etc. These provide functionality like desktops, icons, and window controls (i.e., the minimize/maximize/close buttons).
[*]A step above that are "desktop environments" like Gnome and KDE. These are full-fledged workspaces that integrate printing, windowing, networking, etc.
[*]Very new stuff like Xgl and Compiz are new ways of handling X and windowing managers to provide fun things like wobbly windows and transparency.
[/LIST]

---

### Post by bocmaxima on 2006-07-10
> **wylfing said:**
> These aren't really "Linux conventions." Windows has the same parts: a kernel, a shell, a window manager, etc. It used to be easier to understand this about DOS/Windows years ago. For example, everyone used to understand that your shell was COMMAND.COM.

But anyway, here is a rough idea of the major pieces.

[LIST]
[*]The kernel is like the foundation. Everything builds on top of that.
[*]A shell is simply a command interpreter, so that when you type "ls" in a terminal it does something sensible. (Actually shells do a bit more, but that's pretty good for a simple explanation.) 
[*]X Windows provides a graphical environment, but sticks to fairly primitive functionality, e.g., this is a mouse click, this is a cursor. 
[*]More sophisticated GUI work is handled by what are called windowing managers such as Metacity, IceWM, etc. These provide functionality like desktops, icons, and window controls (i.e., the minimize/maximize/close buttons).
[*]A step above that are "desktop environments" like Gnome and KDE. These are full-fledged workspaces that integrate printing, windowing, networking, etc.
[*]Very new stuff like Xgl and Compiz are new ways of handling X and windowing managers to provide fun things like wobbly windows and transparency.
[/LIST]


Thanks, I guess I was unclear from X on up, the Kernel and Shell I knew...but it still seems weird. Like, you can have X, then Metacity or IceWM, then Kde or Gnome, then Xgl and Compiz? Or is Xgl a different X?

How do they work together?

Maybe Wikipedia is better to answer this stuff, heh

> [http://www.linuxnewbieguide.org/](http://www.linuxnewbieguide.org/)
Good place for reliable info...
and the Tuxfiles link in my sig for some helpful tutorials etc...
(No idea of the Xgl/compiz relationship,myself. Still a Breezy user.


Heh, I knew most of that stuff, about how to install and such. Im already running Dapper and can do a decent amount of things. I am just wondering what is what and how it all inter-relates because I would like to have Xgl and Compiz running on here, and I like Gnome, but I just dont know whats what etc.

---

### Post by wylfing on 2006-07-10
If you have "stock" Ubuntu, then you are running X, Metacity, and Gnome. Gnome uses Metacity as its windowing manager. You can switch out Metacity for other WMs if you want -- some people prefer other managers.

Xgl is a variety of X server. Just like Metacity, you can swap out the standard X server (which is the Xorg server) for a different one that provides different functionality, in this case OpenGL-driven fancy graphics. So Xgl is a replacement for Xorg.

---

### Post by bocmaxima on 2006-07-11
> **wylfing said:**
> If you have "stock" Ubuntu, then you are running X, Metacity, and Gnome. Gnome uses Metacity as its windowing manager. You can switch out Metacity for other WMs if you want -- some people prefer other managers.

Xgl is a variety of X server. Just like Metacity, you can swap out the standard X server (which is the Xorg server) for a different one that provides different functionality, in this case OpenGL-driven fancy graphics. So Xgl is a replacement for Xorg.

Cool. What is the benefit of switching out window managers? It seems kinda low level, so if one works, they all might suffice, right?

---

### Post by wylfing on 2006-07-11
You get different windowing behavior with different managers. For example, one of the things people often don't like about Metacity is that there is no way to move a window around without displaying the contents all the time. Some people (like me) would rather drag the wireframe around and then have the window snap to the new position. (This isn't enough of a grievance to make me switch WMs though.)

Examples of other WM differences: what happens to windows when you minimize them (or *iconify* as it happens in some WMs), the presence of a dock, left/right/middle clicking the desktop (the menus that appear differ quite a bit), additional windowing controls (e.g., "pinning"), and the visual styles you can achieve.

Switching WMs is kind of advanced, not so much because it's hard to achieve but because you need to be willing to relearn how to use your on-screen widgets. Making the switch (on Ubuntu anyway) is no harder than installing the WM packages and running update-alternatives.

---

### Post by mcduck on 2006-07-11
XGL is a different X that uses your 3D card to draw graphics with OpenGL. After all, your graphics card handles graphics much better than your CPU does..

Compiz is a window manager (replacing Metacity) that uses OpenGL to do all cool things with your desktop.

---

