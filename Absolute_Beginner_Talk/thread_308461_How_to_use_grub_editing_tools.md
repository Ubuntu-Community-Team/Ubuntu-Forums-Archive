---
title: "How to use grub editing tools?"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-28
I'm having difficulties using the tools in which you edit grub with.  These are the directions I picked up from other ppls threads.
> 
Open a terminal, Applications -> Accessories -> Terminal, and type

Code:

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak gksudo /boot/grub/menu.lst**

Now, change the "default" value from "0" to whatever entry your Windows is on, usually 3--the fourth entry...
That cp and gksudo command didn't work at all for me even when I divided up the commands.  When typing gksudo /boot/grub/menu.lst it says something about not being a command :confused: then I tried a bunch of different variations to do this in terminal but instead I get a message saying, menu.lst is not a catalogue or something.

So instead of using gedit I thought of using nano instead
> Open a terminal and type

Code:

sudo nano -Bw /boot/grub/menu.lst
> It's safer to put the "Windows XP" partition first in the list, and leave '0' as default. That is, put windows entry before the statement

### BEGIN AUTOMAGIC KERNELS LIST

This way, if a system update inserts another kernel entry, grub will not boot the wrong partition by mistake.

And I got in...BUTT.  I can't use the mouse to scroll the sidebar and I can't highlight the texts by [Shift-down Arrow] instead it inserts some bunch of characters.
So I tries to exit by clicking and typing ^x and x but I can't make nano do what I want. :evil: 

[COLOR="Red"]My summarized **QUESTIONS**[/COLOR]
How the heck do you access the commands such as "Exit" at the bottom of the terminal :confused: 
And how the heck do I type the command line correctly in order to use Gedit instead?

---

### Post by xyz on 2006-11-28
Hi,
The ^ stands for the Ctrl character on your keyboard. For example, the exit shortcut on nano is ^X, so to exit nano you would hold down Ctrl and press x.
[Nano Documentation]("http://www.nano-editor.org/docs.php")

---

### Post by Bachstelze on 2006-11-28
And if you still want to use gedit as root, the correct command is 

```
gksudo gedit /path/to/file
```

---

### Post by Tomosaur on 2006-11-28
You may want to take a look at the link in my signature, it'll give you a GUI for editing Grub :)

However, if you still wish to use the command line, here are the commands (with a little explanation):

The following will make a backup of your existing grub config:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.BACKUP

```

The following will open your current config in a text editor:
```

gksudo gedit /boot/grub/menu.lst

```

Follow the instructions in that file to change your settings. Once you're finished, save and exit the text editor.

Now, depending on which settings you changed, you MAY need to type:
```

sudo update-grub

```
But that command is not always necessary. Next time you reboot your machine, grub should be changed to reflect whatever you altered in the config file.

---

### Post by jingo811 on 2006-11-28
tnx :mrgreen:

---

