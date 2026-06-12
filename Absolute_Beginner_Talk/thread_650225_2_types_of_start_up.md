---
title: "2 types of start up"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by bornfree on 2007-12-26
Hi I just started using linux 
when i installed the Ubuntu Server 7.1 it was in commandline then i installed the desktop and it started booting up in GUI 
How can i choose to start up between commandline and GUI as and when i need? if not just commandline will do as i can use startx to launch the GUI(or do you call it gnome )

---

### Post by riven0 on 2007-12-26
Usually you just switch to one of the consoles: **Alt + CTRL + F1** or **Alt + CTRL + F2**, etc, etc, up to **Alt + CTRL + F7** which will switch back to the gui. Is that what you were asking? :confused:

---

### Post by LaRoza on 2007-12-26
> **bornfree said:**
> Hi I just started using linux 
when i installed the Ubuntu Server 7.1 it was in commandline then i installed the desktop and it started booting up in GUI 
How can i choose to start up between commandline and GUI as and when i need? if not just commandline will do as i can use startx to launch the GUI(or do you call it gnome )

This will move the file to your home directory (so you can put it back if you want). 

```

mv /etc/init.d/gdm ~/gdm

```

You might have to be root, and you might not like it. 

The command:

```

startx

```

Will start GNOME.

"sudo poweroff" shuts down the computer, which you will have to use if you use the CLI.

Do not run startx as root.

---

### Post by Hospadar on 2007-12-26
I think probably the best thing for you would be to remove gdm from your startup scripts.  offhand I found a couple threads about this
[http://ubuntuforums.org/showthread.php?t=349517](http://ubuntuforums.org/showthread.php?t=349517)
[http://ubuntuforums.org/showthread.php?t=262781](http://ubuntuforums.org/showthread.php?t=262781)
I think however that these might boot you straight into a gui after you login, I'm not sure.  There is however some nice info on getting rid of the bootup GUI if you want to see all the console output as you boot.

---

