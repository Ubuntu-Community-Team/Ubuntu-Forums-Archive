---
title: "couple of questions! + 1"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by pascalosti on 2007-07-04
How do I uninstall Warcraft 3 from wine? (doesnt work from applications/ wine)

Is there  a ctrl alt delete  similar to windows when a programs gets hung up. currenty I log out if that happens.

and question 3
when I installed i partitioned  30 or 40 gigs in fat32 for windows in the future, turns out i wont be using that space. Can I somehow add this space to my current space or just another partion I can use from Ubuntu

---

### Post by kamakura on 2007-07-04
I don't know the answer to question 1, however I can help with number 2.

 
There are a couple of ways to kill an application.  Most of the time you can right-click the application on the task bar and click close.  You will get a message regarding the application not responding and you can stop the application from that message.  

A second (and slightly more difficult option) is to end it from the command line interface.  First you need to find the process number using the ps -e command.  If you know the name of the process, you can type the following:

ps -e | grep <application_name>

If you don't know the name, use ps -e and look through the results to find the correct process.  Once you find the process for the application, you will need to know the process number (the first column).  Then you will type the following command on the command prompt:

kill -9 <process_number>

---

### Post by atria on 2007-07-04
For qn1, if the uninstallation sequence doesn't work, you'll have to delete the warcraft III directory manually.

By default win32 programs installed using wine are installed to /home/<youruser>/.wine/c_drive

You will want to browse into that directory to remove warcraft III. This method of uninstallation is not exactly recommended though since the wine registry is not properly cleaned. You might want to just remove the entire /home/<youruser>/.wine directory and reconfigure wine by using winecfg instead. This ensures a clean wine installation.

Hope that helps

---

### Post by coolen on 2007-07-04
> **pascalosti said:**
> How do I uninstall Warcraft 3 from wine? (doesnt work from applications/ wine)

Is there  a ctrl alt delete  similar to windows when a programs gets hung up. currenty I log out if that happens.

and question 3
when I installed i partitioned  30 or 40 gigs in fat32 for windows in the future, turns out i wont be using that space. Can I somehow add this space to my current space or just another partion I can use from Ubuntu

As an alternative to the ps command mentioned, hit Alt+F2, type xkill. Your cursor should change to a skull and crossbones...then click on the application you wish to close.

If you do want to go the ps route, though, try it without the -9 switch first. This option tells the kernel to kill the application immediately. The application may not truly be hung. It could be stuck in a loop. If it's written well, it'll take an interrupt signal (the default of the kill command) and clean up after itself before closing.
If that doesn't work, then use -9.

Oh, and System -> Administration -> System Monitor has the ability to term/kill processes. You could configure the shortcut through gconf:
```
gconf-editor
```
apps -> metacity -> keybinding_commands

You need to put the shortcut in manually, but voila! You can use this space for pretty much any command you want (if you use a compositing window manager, these options are probably more obvious. Compiz even copied it over for me).

---

### Post by coolen on 2007-07-04
> **pascalosti said:**
> How do I uninstall Warcraft 3 from wine? (doesnt work from applications/ wine)

Is there  a ctrl alt delete  similar to windows when a programs gets hung up. currenty I log out if that happens.

and question 3
when I installed i partitioned  30 or 40 gigs in fat32 for windows in the future, turns out i wont be using that space. Can I somehow add this space to my current space or just another partion I can use from Ubuntu

For your final question, you can use GParted. Download it from the repos. Reformat the partition as ext3, and use it however you want. Setting is up as /home might take a little work (you could mount and move from the LiveCD, then manually edit the fstab).
If it's at the beginning of the drive, you won't be able to expand your root partition back into that free space. You can only expand forward.

---

