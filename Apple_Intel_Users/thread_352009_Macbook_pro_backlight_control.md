---
title: "Macbook pro backlight control"
date: 2007-02-02
forum: Apple Intel Users
---

### Post by pauljwells on 2007-02-02
I read this post with interest...

[http://ubuntuforums.org/showthread.php?t=215801](http://ubuntuforums.org/showthread.php?t=215801)

Kudos to alexinfurs... but there is an easier way of doing this using Gnome's built-in keyboard bindings.

I can't test the Macbook 'backlight' program as I don't have one, but the gconf keybindings should still work.

For the Macbook Pro download the backlight.c and Makefile files from here

[http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/tools/backlight/](http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/tools/backlight/)

Save them both to an empty directory and cd to it in a terminal. Make sure that Makefile didn't get a .txt extension or anything to its name. Type 'make' && sudo make install' and you should get an executable 'backlight' installed in /usr/local/bin

Test that this works by typing 'backlight -10' in a terminal. Your screen sould get slightly darker.

Now open System/Preferences/Keyboad shortcuts, find the item for 'Launch help browser' and delete the binding (you can assign something like 'Control F1' if you like instead - just press the actual keys you want rather than typing) then close.

To assign custom commands to keys you can use gconf-editor. Just type 'gconf-editor' in a terminal and it will open a gui window. Go to the item apps/metacity/global_keybindings find run_command_1 and edit the value to be F1 (you have to type 'F1' rather than press the F1 key) and similarly for run_command_2 set the value to F2.

Next go to apps/metacity/keybding_comands, find command_1 and set the value to 'backlight -10' Set the value of comand_2 to 'backlight +10'

Close gconf-editor and you should be able to dim or brighten the screen by pressing F1 or F2! (you might have to log out and back in to apply the changes)

One last thing... you can set the startup brightness by adding the command 'backlight 120' (or a value between 10 and 240) to System/Preferences/Sessions/startup Programs


Enjoy!

---

### Post by ronocdh on 2007-04-02
Very handy advice, thanks! I believe it's very similar to the technique offered in this guide: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook).

I found your command for setting a default brightness most helpful! Sick of blinding myself, booting into Ubuntu in the middle of the night. ;)

---

### Post by Tribe on 2007-04-03
Hi,

Have you tried pommed ? I got backlight + keyboard light + apple remote working out of the box, the first two using the Fn keys.

BTW in a Feisty with kernel 2.6.20-13.

Bye.

---

