---
title: "Shorcuts &amp;window operations (max,move..) independent of environment &amp; window manager"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by calt129 on 2005-11-14
I was/am using a pretty powerful program under windows called [powerpro]("http://groups.yahoo.com/group/power-pro/"), which can use all imaginable kinds of keyboard/mouse shortcuts (it's very hard to describe this) and do various window manipulations/operations such as move, max, min, tile, bring-to-front/back, even send keys to or read text from these windows, etc; actually PowerPro can do muuuch more. A very similar tool for OSX is the [Butler]("http://www.petermaurer.de/nasi.php?section=butler&layout=default").

I'm wondering, is there a tool, preferably a **single** one, which can do such operations? I have no problem with scripting or programming, actually I'll have fun doing this but I neither want to combine thousands of different tools which I eventually wouldn't find under a different unix/linux system, nor I want to take bloated eye-candy stuff like gDesklets, Karamba, etc. A simple combo like $SOMETOOL plus (Perl|Python|PHP|...) for scripting is exactly what I want...

Is there any hope? :confused:

---

### Post by Kyral on 2005-11-14
XBindKeys may work (I know its universal accross the WMs), but as you said you don't mind scripting, so it might be best to write a custom job. But try XBindkeys (I think thats the program)

---

### Post by calt129 on 2005-11-14
What do you mean "custom job"? With which language and/or tool?

As for Xbindkeys, well it solves only the *problem* with keyboard shortcuts. What about the window operations and mouse actions?

---

### Post by Kvark on 2005-11-14
[Devil's Pie](http://ubuntuforums.org/showthread.php?t=75749) can do things like "place all windows with 'gimp' in the title on workspace 3 when they are opened" with Gnome's window manager Metacity but thats not exactly what you are looking for.

I use a window manager called Ratpoison. It uses tiles, in other words it runs the programs in full screen or split screen instead of in windows which means there are no panels, no menues, no desktop folder and no x in the corner of windows on the screen, just your programs. It is operated entirely with keyboard commands so it might be kinda similar to what you're looking for.

To give you an example of how ratpoison can be used I'll describe how my customized keyboard shortcuts to it are arranged... I set the windows keys to switch focus from the current window to Ratpoison so one of the windows keys is always pressed before a keyboard command to Ratpoison. I arranged the commands like this:

I hit the 5-key and it brings up window number 5 and the key 2 steps under the 5-key (happens to be the G-key) brings up window number 25, this way I can reach any of up to 40 windows within 2 keystrokes. Ctrl+F1 saves the current window arangement and F1 goes back to it, each F# key can hold a separate arrangement so I can also reach 12 window arrangements (it's like the workspaces in Gnome) with 2 keystrokes.

Shift+F opens a new Firefox window and Shift+X opens a new Xchat window and all my programs are on Shift+something. Ctrl+S splits the screen horizonatlly, Ctrl+Shift+S splits it vertically, Ctrl+K closes the current window, Ctrl+Shift+K kills the current window and all other window management commands are also on Ctrl+something.

---

### Post by calt129 on 2005-11-15
[QUOTE=Kvark][Devil's Pie](http://ubuntuforums.org/showthread.php?t=75749) can do things like "place all windows with 'gimp' in the title on workspace 3 when they are opened" with Gnome's window manager Metacity but thats not exactly what you are looking for.[/QUOTE]

Actually, Devil's Pie comes closer to my needs. It mimics the "Autorun" feature of PowerPro, that is, it responds to window-events (to some degree/fully?) on the desktop. I'll have a look at it. Thanks for the pointer :)

Do you know any program with which I can do stuff in my scripts like "move this window matching the title /[abc]+$/ to $xscreen-200 $yscreen-20 and resize it to 300x200". You know what I mean? I need a tool to communicate with the window-manager and/or X. I've heard about Perl-bindings for GTK, could I do such things with that?


[Quote=Kvark]I use a window manager called Ratpoison. It uses tiles, in other words it runs the programs in full screen or split screen instead of in windows which means there are no panels, no menues, no desktop folder and no x in the corner of windows on the screen, just your programs. It is operated entirely with keyboard commands so it might be kinda similar to what you're looking for.[/QUOTE]

I'd rather like the tool arrange the windows automatically, based on some rules, than do it myself. That's why Devil's Pie sounds nice.

But you might wanna have a look at ION and WMI window managers, they do more or less the same as Ratpoison, or maybe more. Found at [OSNews](http://www.osnews.com/story.php?news_id=6958).

---

### Post by Kvark on 2005-11-15
Ah, you want it done automatically based a set of rules instead of with keyboard commands. In that case Devil's Pie is exactly what you are looking for. The only possible flaw I can think of is if you want some features that devilspie doesn't have. But in that case you can grab devilpie's source code and add the features (and send your additions to devilspie's developers so others can use them too).

PS. I doubt GTK bindings are of any use here because GTK handels the stuff inside the windows like scrollbars, buttons and checkboxes.

---

### Post by calt129 on 2005-11-15
[QUOTE=Kvark]Ah, you want it done automatically based a set of rules instead of with keyboard commands. In that case Devil's Pie is exactly what you are looking for. The only possible flaw I can think of is if you want some features that devilspie doesn't have. But in that case you can grab devilpie's source code and add the features (and send your additions to devilspie's developers so others can use them too).[/Quote]

I've found this guide: [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749). DP does indeed **almost** everything what I want. I'll dig into this. Thanks again!

[Quote=Kvark]PS. I doubt GTK bindings are of any use here because GTK handels the stuff inside the windows like scrollbars, buttons and checkboxes.[/QUOTE]

I've also found this: [http://fvwm.org/documentation/manpages/unstable/FvwmPerl.php](http://fvwm.org/documentation/manpages/unstable/FvwmPerl.php), a Perl module for fvwm, looks damn good. This may sound stupid but can I use fvwm under a "Gnome session", i.e. using fvwm instead of metacity but keeping everything else? (Well eventually gnome-panel must go, too)

Well, I almost forgot. This newcomer [Mezzo/SymphonyOS](http://www.symphonyos.com/mezzo.html) seems to be based on Mozilla and Perl, i.e. one can use the Mozilla canvas and all that Mozilla stuff (DOM, JS, CSS, etc.) and script it with Perl. Sounds like heaven :)

---

### Post by Kvark on 2005-11-15
[FVWM's FAQ](http://www.fvwm.org/documentation/faq/#2.8) explains how to replace Metacity with FVWM in Gnome.

---

