---
title: "More macromedia flash help - trying to uninstall"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2008-02-24
I recently downloaded something that broke flashplayer. It wont work on my browser (Opera 9.25)

I have read some of the other posts, and decided to remove and reinstall flashplayer.
I used apt-get to remove it (I think it worked).

Opera properties point toward flashppayer being in /usr/lib/flash-plugin


When I navigate to the /usr/lib folder, I find a flash-plugin folder, containing 2 files that I need to remove:
libflashplayer.so
setup.

The readme file also in that folder has the following istructions:

Uninstallation instructions
---------------------------

Manual uninstallation (for users who installed the plugin via Install script):
   o Delete libflashplayer.so binary and flashplayer.xpt file in 
   directory /home/<user>/.mozilla/plugins/

Problem is: I cannot remove these files as the properties shows them owned by root.
I have tried to navigate to them in terminal, but cant seem to do it (terminal is new to me)
so my questions:
how can I delete these files?
If I must log on as root to do so, how can I do that (and I know that's a dangerous question!!)
how do I navigate to these files in terminal. (my most inane question but - why not??):confused:

Thanks!

---

### Post by bazzawill on 2008-02-24
Ok to navigate in a terminal use the ```
cd /usr/lib/flash-plugin
``` and to delete them as root type ```
sudo rm libflashplayer.so
``` one handy part of the terminal is it's tab completions so you don't need to type the whole file you can just type a part and press tab to get the rest to come up as for logging in as root the sudo command handles that for you so you only have root access when you type sudo in front of the command

---

### Post by 3pinner on 2008-02-24
thank you!
I dont know what I was doing wrong, but that did it.
Now to see if the reinstall works.

---

