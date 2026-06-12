---
title: "Window Managers, Keyboard Layout, Updates,..."
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by excogitation on 2008-03-07
Some questions (hope I'm right here):


4. Window Managers...
- There's only one at a time possible, right?
- Standard is metacity, right?

Compiz messes up more - my keyboard layout now is English instead of German
and there's a lot missing in the lower taskbar, doubleclicking the titlebar rolls the window up
instead of maximizing it,...
7. Is that normal? How can I fix that?

10. My CPU runs at 800MHz most the time (Dothan 1,86GHz), the CPU Temperature
is at 49*C but the Fan is running all the time - how can I change that?



Some data you may be interested in... or not...
metacity ->compiz
> compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

I will supply you with whatever information you need gladly,
keep in mind I've just startet with Ubuntu.

--------------------------------------------------------------------------------------------------------------------------------------------------
If you run into as many problems - from the start - consider reinstalling 
- at least now that I reinstalled I have a lot less problems.
So if no one tells me... I'll just keep reading and reading and...

[SOLVED]
1. I installed Hardy Heron Alpha 5. Does it automatically update to Alpha 6 and the versions to come (Update Manager)?
Yes
2. Where can I check what version I'm currently running?
uname -a display's kernel version

3. What type of pictures does GRUB display correctly (tried 256 colors, greyscale, indexed)?
xpm image/x-xpixmap

I wanted to try the cube feature and all different kinds of useless gimmicks and installed
Compiz and XGL.
Now it seems somewhat unstable - I loose the titlebars every once in a while.
5. Is it right to fix it like this: "Alt+F2 -> compiz"?
If it happens once - yes - if it happens every time you login or every xx-xx minutes - there's something wrong.
6. Should I uninstall metacity?
...why would you want to install compiz in the first place?

8. When I find myself in the console (Strg+Alt+F1?) how do I get the UI back?
Strg+Alt+F7 + wait a few seconds
(if you only have a blinking "_" there might be sth else wrong - don't know yet)

9. Is there a way to tell my graphics card (Ati Radeon Mobile X700) to use
powerplay or just use slower clocksettings? (aticonfig --set-powerstate 1 results in  Segmentation fault (core dumped))
If the fglxr driver is installed correctly - the aticonfig --set-powerstate command works.
No powerplay - yet.

11. Is there a tool to undervolt my laptop or should I refrain from that for the time being (new to Ubuntu)?
[lower CPU voltage](http://wiki.ubuntuusers.de/Prozessorspannung_absenken)

12. What does Emerald do? sth. like Windowblinds in the Windows' world?
Yes

---

### Post by ugm6hr on 2008-03-07
I can't help with all those questions, but might give a big hint...

If you have only just started with Ubuntu, I would strongly advise you to use a stable release (i.e. Gutsy / 7.10) rather than Hardy.  You will find it difficult to learn anything with an unstable system, since it will never be clear whether the problems you are having are a result of software instability, hardware incompatibility or human error.

If you decide to persevere with Hardy, it should update all the way up to the actual release and beyond.

---

### Post by Thingymebob on 2008-03-07
grub needs an xpm wrapped in a gz archive normally these are 16 colours only. 

Strg+alt+F7 to return to the gui

---

### Post by excogitation on 2008-03-08
Thanks to both of you.

I just thought I wouldn't use Ubuntu all that much so I figured I could wait for the final of Hardy Heron, but now I seem to rather like it an I don't want to make a clean install because it seems to work just fine. It's just that I have to get used to the way of doing thing in linux.

I'll give xpm in gz a try.

Strg + Alt + F7 definitely helps :-)

---

### Post by ugm6hr on 2008-03-08
> **excogitation said:**
> I just thought I wouldn't use Ubuntu all that much so I figured I could wait for the final of Hardy Heron, but now I seem to rather like it an I don't want to make a clean install because it seems to work just fine. It's just that I have to get used to the way of doing thing in linux.


In that case, welcome :)

This is worth keeping an eye on for problems: [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)

As for the Window Manager question...  I thought Compiz was now the default, but ATI cards don't work with Compiz unless they have the latest drivers or XGL.  Hence they default back to metacity / Gnome default.

And yes, one at a time only (I can't think why you would want more than one - it would just get confusing).

Uninstalling metacity won't do anything (I think).

Compiz instability is a known issue, and it may be worse in Hardy (as alpha release)...

---

