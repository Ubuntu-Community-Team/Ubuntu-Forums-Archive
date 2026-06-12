---
title: "Lockup Issues"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Sonthun on 2007-09-27
Under Windows I'm used to being able to ctrl-alt-delete when an app locks up my machine.  When something locks up my Feisty Ubuntu, I just have to wait around until the machine reboots itself or hit the hard reset button.  Is there some way for me to deal with this in the OS?  Should I be using another method?

Thanks.

---

### Post by CaptainInsaneO on 2007-09-27
You need to do the following to bind Ctrl+Alt+Del

First make sure system monitor is installed:```
sudo apt-get install gnome-system-monitor
```

Then, type these commands into terminal:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

That's all you need.

Edit: I'm not sure how to make it work in Compiz if you're running it, sorry. :(

---

### Post by overdrank on 2007-09-27
> **Sonthun said:**
> Under Windows I'm used to being able to ctrl-alt-delete when an app locks up my machine.  When something locks up my Feisty Ubuntu, I just have to wait around until the machine reboots itself or hit the hard reset button.  Is there some way for me to deal with this in the OS?  Should I be using another method?

Thanks.

Hi if you right click on your top panel (or bottom whichever you prefer) you can add Force quit to the panel and this will assist you. Hope this helps good luck!

---

### Post by ddrichardson on 2007-09-27
Apps shouldn't be locking up your machine. Is this just a single application or X as a whole. If it's X then does CTRL-ALT-Backspace kill the server?

Are there any log messages concerning the lockups?

---

### Post by P235 on 2007-09-27
Hi, there are a few options available to you when your PC freezes with Linux.  First, if Linux has not become absolutely frozen try installing htop and run the program when you notice an application freezing.  You will likely find htop to be more visually appealing than top.  

Second, you can restart your x-session with ctrl-alt-backspace.  

Third, you can hit alt-prt sc/sys rq-r, s, e, i , u, b, to reboot your computer safely (see [System Requests]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#System_requests_.28What_to_do_if_your_system_is_unresponsive.29") under ubuntuguide.org and [this]("http://ubuntuforums.org/showthread.php?t=315404") ubuntuforum thread).  

Be careful not to hard boot your Linux computer (i.e. pulling the power) as that will cause a number of difficulties down the line.  When one pulls the power on a Linux computer often, fsck is likely necessary to clean up the mess.  Should you need to restart your Linux computer try your best to use the third option.  If you find that your Linux computer freezes often in a predictable manner the problem may rest with the hardware (RAM possibly).  

To test your RAM you can access the memtest which comes with Ubuntu by restarting your PC.  I recommend running the memtest every 10 or so minutes a few times rather than running a single memtest from start to finish.  If an error does occur, something is wrong with the RAM.

---

### Post by teknosexual on 2007-09-27
> **CaptainInsaneO said:**
> Then, type these commands into terminal:

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

Thanks for those commands, Works great!

---

### Post by CaptainInsaneO on 2007-09-27
Glad I could help!

---

### Post by Sonthun on 2007-10-11
Sorry, I haven't replied yet, but I guess I forgot to subscribe to the thread so I didn't realize there had been replies.

Thanks for the commands.  I will try implementing all of those.

ddrichardson - The system has been relatively unstable as a whole.  Part of that is because I am trying to run mythtv, but it also freezes trying to use Xine or sometimes when using a text editor.  I've run memtest and didn't get any errors from it.  It's a brand new sytem: AMD 64 Dual Core 6000,  MSI NX8500GT (Nvidia) videocard, ECS Motherboard, 2GB Corsair Ram.  Most of the time when it locks up I can move the mouse, but can't click on anything.  Sometimes it will come back, othertimes I'll leave it for eight hours and it won't come back.  Ctrl - Alt - Backspace won't do anything.  I'm thinking of trying to custom compile a kernel with CFS to see if that helps some of the problems.  I kind of want to learn how to compile a kernel.

---

### Post by coolen on 2007-10-11
When binding Ctrl+Alt+Del to System Monitor, Compiz should honour your preference and add it to its own. Handy little feature I discovered when I got rid of click to focus :)

---

