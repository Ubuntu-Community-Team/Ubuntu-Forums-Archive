---
title: "How to reset my keyboard settings?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by stfu on 2006-06-10
I totally screwed up my keyboard settings while trying to get my super(win) key shortcuts to work. Now my alt gr and alt keys as well as other keys are in wrong position. I ran xbindkeys which didn't help me out with the original problem, but got me a bunch of new ones. Keyboard shortcuts settings now only show shortcut setting for Desktop and Sound. 
I also install Compiz + Xgl. Don't know if that has something to do with keyboard settings.

---

### Post by dvarsam on 2006-06-10
How about selecting from the Menu:

> System\Preferences\Keyboard Shortcuts

You can set some of your Shortcuts from there!

---

### Post by patrick295767 on 2006-06-10
Additional information:
==
I am using absolutely allll keys of my keyboard via fvwm desktop
(fvwm is highly customizable desktop) you can create your own key shortcuts or progrs to be started
  
For extra keys that are multimedia ... extended ... I used/installed : 
  keytouch
  
Greetz

---

### Post by stfu on 2006-06-10
[QUOTE=dvarsam]How about selecting from the Menu:



You can set some of your Shortcuts from there![/QUOTE]
Yes, but as I said, it only shows up Desktop and Sound settings. It used to show a lot more until I did something. Now I want to reset things and start over.

---

### Post by richbarna on 2006-06-10
I had the same problem when I installed compiz, I think (judging by peoples posts) that it is a common problem.
I have since done a fresh install, but what I did before was to do a terminal login and use startx to get to a normal non-xgl/compiz desktop.

---

### Post by stfu on 2006-06-10
Ok, I think I pretty much solved this. Like said, it's because of compiz.
Here's the guide.

[https://wiki.ubuntu.com/Lkraider/XmodMap?highlight=%28xmodmap%29](https://wiki.ubuntu.com/Lkraider/XmodMap?highlight=%28xmodmap%29)

Then make sure you start xmodmap /usr/share/xmodmap/xmodmap.<youlanguage> on start.

My shortcut settings are still messed up, but I guess I can configure them through gconf-editor.

---

### Post by dvarsam on 2006-06-11
I like this thread!

However, It seems half-complete (in my opinion)...

To have a nice "final/complete" version for this, let me add these few lines:


**_How To Set "Ctrl+Alt+Del" launch "System Monitor"_**:

Here is an how to set "Ctrl+Alt+Del"to launch the "System Monitor" under Gnome.


**Part A &#8211; Automatic Way**:

1.Launch a Terminal window (from Menu, select "Applications\Accessories\Terminal"), & type (or copy/paste):

    gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

2. Then, type:

    gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

This should set you strait.


_Note_: Sometimes the above method does NOT work (this happened to me!), & you need to do this _Manually_ (for this, see "**Part B**")! 


**Part B &#8211; Manual Way**:

1. On your Keyboard, press "Alt-F2" 

2. Type "gconf-editor"

3. Go to "apps\metacity\global_keybindings"

4. Under "run_command_1", click under the column named "Value" & type "<Control><Alt>Delete"

5. Go to "apps\metacity\keybinding_commands"

6. Under "command_1", click under the column named "Value" & type "gnome-system-monitor"

7. Close the open window

You should be now set & can test your "Ctrl+Alt+Del" added shortcut!


_Note_: You could also create a shortcut for "xkill" to kill any offending application by just clicking on it.

---

