---
title: "Ctrl-Alt-Delete equivalent for Ubuntu?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by 1.21 on 2006-06-06
I was just wondering if there was a Control-Alt-Delete equivalent for Linux and Ubuntu specifically? 

I apologize if this has been answered many times before. 

Thanks

---

### Post by durableapostle on 2006-06-06
Ctrl-Alt-Backspace restarts the x drive...  sort of a "light" restart. :)

---

### Post by aktiwers on 2006-06-06
Start Menu => System => Administration => System Monitor

Or install Automatix, it can make it appear when you hit CTRL + ALT + DELELTE
[http://www.ubuntuforums.org/showthread.php?t=177646&highlight=automatix+dapper](http://www.ubuntuforums.org/showthread.php?t=177646&highlight=automatix+dapper)

---

### Post by 1.21 on 2006-06-06
So if the system or an application freezes, there is no way of restarting Ubuntu without having to manually press the power button?

---

### Post by rjcube on 2006-06-06
[QUOTE=1.21]So if the system or an application freezes, there is no way of restarting Ubuntu without having to manually press the power button?[/QUOTE]

If the system freezes u can do ctrl-alt-backspace, it will restart to login screen. Like said before, a light restart.

If an application freezes just do a force quit, or use the system monitor and end the process or something.

---

### Post by durableapostle on 2006-06-06
ctrl-alt-backspace should restart the x drive.

As far as the windows-type system monitor, try k-menu, system, system monitor, then click on processes--you'll recognize what to do from there (in Kubuntu).

---

### Post by 1.21 on 2006-06-06
Thank you all for the quick replies and helpfulness.
I was expecting to get flamed, but to the contrary. This community really is extreamly helpful. Thank you.

---

### Post by rjcube on 2006-06-06
[QUOTE=1.21]Thank you all for the quick replies and helpfulness.
I was expecting to get flamed, but to the contrary. This community really is extreamly helpful. Thank you.[/QUOTE]

Yeah, ive figured that out that in the last few days. People here are prety helpful. Ive gotten lots of help since I got Ubuntu. Also, this question helped me out too, now im gonna install Automatix so system manager will work with Ctrl+alt+del.

---

### Post by Jucato on 2006-06-06
Linux is known for not crashing/freezing up when a single app crashes/freezes, although there are instances that it does. 

If the whole desktop freezes, you could restart it by restarting the X server (ctrl+alt+backspace)

If you'd like to kill just a single app or process, you can use the System Monitor to pick it out.

If a graphical application is causing you trouble and you want to kill it at once, you can do this:
- Open a Run application dialog box (press Alt+F2_
- type in xkill.
- your cursor becomes a skull with 2 bones, like a the pirate flag. Anything you left-click with this cursor will automatically get killed. (be careful not to click on your desktop). 
- to deactivate it without killing anything, right-click anywhere.

Hope that helps, too.

---

### Post by rjcube on 2006-06-06
[QUOTE=Fenyx]Linux is known for not crashing/freezing up when a single app crashes/freezes, although there are instances that it does. 

If the whole desktop freezes, you could restart it by restarting the X server (ctrl+alt+backspace)

If you'd like to kill just a single app or process, you can use the System Monitor to pick it out.

If a graphical application is causing you trouble and you want to kill it at once, you can do this:
- Open a Run application dialog box (press Alt+F2_
- type in xkill.
- your cursor becomes a skull with 2 bones, like a the pirate flag. Anything you left-click with this cursor will automatically get killed. (be careful not to click on your desktop). 
- to deactivate it without killing anything, right-click anywhere.

Hope that helps, too.[/QUOTE]

Thats a pretty neat tool. I shall use that if needed. Thanks.

---

### Post by MetalMusicAddict on 2006-06-06
Make CTRL+ALT+DELETE open up the gnome-system-monitor

From a terminal:
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
```
Then:
```
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

---

### Post by dvarsam on 2006-06-07
[QUOTE=MetalMusicAddict]Make CTRL+ALT+DELETE open up the gnome-system-monitor

From a terminal:
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
```
Then:
```
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```[/QUOTE]

The above combination (strangely enough), does NOT work!!!

I have tried it many times!!!

I perform a "sudo -i" & then type the above commands & they do NOT work!!!

I am running Ubuntu v6.06 Dapper!

Why does it NOT work?

Thanks.

P.S.> Even if I put these commands on a "bash" file & then run the fine with "sh test.sh", it still does NOT work!!!

---

### Post by uzi09 on 2006-06-07
i'm pretty sure this works in breezy as well, but i know it works for dapper. give this a try:

press ctrl+esc twice to bring up the system monitor (aka task manager)

---

### Post by dvarsam on 2006-06-07
[QUOTE=uzi09]I am pretty sure this works in Breezy as well, but I know it works for Dapper.
Give this a try:

press "Ctrl+Esc" twice to bring up the system monitor (aka task manager)[/QUOTE]

I tried pressing "Ctrl+Esc" twice & NO System Monitor or Task Manager opened!

Any ideas why it did not?

Thanks.

P.S.> I even tried using _both_ left & right "Ctrl" buttons!

---

### Post by uzi09 on 2006-06-07
guess it doesn't work in breezy then :D...sorry!

---

### Post by MetalMusicAddict on 2006-06-07
[QUOTE=dvarsam]The above combination (strangely enough), does NOT work!!![/QUOTE]
Are you running Compiz?

---

### Post by dvarsam on 2006-06-08
[QUOTE=MetalMusicAddict]Are you running Compiz?[/QUOTE]

What is "compiz"?

Under Synaptic it says "OpenGL composition manager"...

I do NOT understand what it really does, but the answer is:

 "NO, the package is NOT installed".

Why, should I install it?

What difference will this make?

Thanks.

---

### Post by MetalMusicAddict on 2006-06-09
No you dont need Compiz installed. Unless you want to play with all the new eye-candy effects you might see around the board. I asked because if it was, Compiz would control your keyboard shortcuts.

---

### Post by dvarsam on 2006-06-09
Dear "MetalMusicAddict",

Thanks for your reply!

[QUOTE=MetalMusicAddict]No you dont need Compiz installed. Unless you want to play with all the new eye-candy effects you might see around the board. I asked because if it was, Compiz would control your keyboard shortcuts.[/QUOTE]

So, If I can NOT get "Ctrl+Alt+Del" to work by typing these two lines at the Terminal:

> gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

IF I install the package "compiz", will I be able to setup "Ctrl+Alt"Del" to launch System Monitor (or Task Manager)?

Thanks.

---

### Post by MetalMusicAddict on 2006-06-09
Compiz is partly a window manager. Search around the forums for more detailed info. It takes a little work and good hardware to get it going.

---

### Post by dvarsam on 2006-06-09
Dear "MetalMusicAddict,

Thanks for your reply!

[QUOTE=MetalMusicAddict]Compiz is partly a window manager. Search around the forums for more detailed info. It takes a little work and good hardware to get it going.[/QUOTE]

Sorry man, but you are NOT answering my question...

I did NOT ask how hard it is to setup...

I asked whether it _can_ do what I am trying to achieve...

Can I setup a "Ctrl+Alt+Del" combination in the "compiz" package/program to be able to launch the System Monitor (or Task Manager)?

Thanks.

---

### Post by MetalMusicAddict on 2006-06-09
Short answer, YES.

---

