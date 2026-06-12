---
title: "Can you use text editor to change system files instead of terminal"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by tc101 on 2007-01-10
I am reading instructions about changing the /etc/pmount.allow file.  Here are the instructions:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

They say to make the change by opening the terminal window and entering the command 
gksudo gedit /etc/pmount.allow and then making changes, using terminal

I notice I can open the pmount.allow file by going to it with Nautilus file browser and clicking on it.  It is then opened in text editor.  It seems that it would be easier to edit it there.  Is there any reason not to do it that way?

---

### Post by Tomosaur on 2007-01-10
Yes - it won't allow you to save it. Currently, nautilus is unable to open files as root (ie, with write permissions on system files). You can run nautilus using gksudo, then select your file that way, but it's easier just to open gedit with sudo, as you described above.

---

### Post by taurus on 2007-01-10
Yes, because you can't save the changes since you don't have permission to write to it.  If you want to use nautilus, then you need to run it with

```
gksudo nautilus
```

---

### Post by G Morgan on 2007-01-10
You could link to a text editor on your panel then edit its properties and alter the command to add gksudo to the front. If you do so it will launch a root mode text editor. I don't recommend this though, you should stick with the normal terminal method in all honesty.

---

### Post by tc101 on 2007-01-10
Thanks for the info everybody.  I will stick with the terminal.  Maybe in a future release where you can just save from the text editor without any extra steps I will do it that way.

---

### Post by szf on 2007-01-10
Learn the terminal and you won't regret it... Experiment with bash command completion (on by default, IIRC), try activating vi or emacs (your choice) on the command line and open up a world of pragmatic administration opportunities.

---

### Post by RRS on 2007-01-10
There's a script to "open as administrator" from the right click menu.

I can't remember the installation "how to" but I'm sure I found it here in the forums.

Anyway, mine's in;
/home/"username"/.gnome2/nautilus-scripts

Here's the actual script copied from my folder;
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gksudo "gnome-open $uri" &
done
```

I can't remember if I had to do anything besides putting the script into the folder to enable it but I'm sure the instructions are here in the forums somewhere. 

Hope this serves you're purposes, I don't use it often but occasionally find it quite handy.

---

### Post by Pobega on 2007-01-10
I normally use alt+f2 to run applications, having pointless terminal windows is a bit annoying. Or you can do

> <command> && nohup

But note, if you do that any programs opened from that terminal session will die with that terminal.

---

### Post by tc101 on 2007-01-10
> I normally use alt+f2 to run applications, having pointless terminal windows is a bit annoying. Or you can do

Is there a list of short cuts like that somewhere?

---

### Post by migla on 2007-01-10
Here's some various key-combos:
[http://ubuntuforums.org/showthread.php?t=23708](http://ubuntuforums.org/showthread.php?t=23708)

---

