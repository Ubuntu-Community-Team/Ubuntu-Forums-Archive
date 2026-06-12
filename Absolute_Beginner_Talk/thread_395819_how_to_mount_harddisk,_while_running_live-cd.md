---
title: "how to mount harddisk, while running live-cd??"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by c174 on 2007-03-28
I'm trying to recover my system, so I run Ubuntu from the live-cd. However, I cannot acces my harddisk! Can I mount the harddisk in some way, or how can I proceed??

Please help!!!

---

### Post by mac.ryan on 2007-03-28
I don't have a liveCD with me to try myself, but I suppose it would be enough to open a terminal and type:

```

mount /dev/sd.... /mymountpoint

```Replace "..." with the proper hd partition you want to mount
And "mymountpoint" with the directory you want to be your mount point

If you have doubts about your HD partitions, issue the command:

```

ls /dev/sd*

```and you will see the list.

Should the first command fail saying something like "you don't have permission" or similar just add "sudo " in front of the line.

[COLOR=Red]EDIT:[/COLOR] if your machine is a bit older, you might have "hd..." instead of "sd....", so just replace where appropriate in the above commands.

---

### Post by c174 on 2007-03-28
Thanks man! I'm amazed.... I realize that I didn't put the mount point, when I tried to mount earlier. I then got the message "mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab". So I thought somethink else was wrong :)

Well, unfornutanely I have just started playing around with repartitioning (as part of a fresh install, trying to keep old data). That didn't go to well... Currently, a complete scan is being carried out, so I can't do anything I suppose.

Or is it safe to kill is scan??

oh, well...

---

### Post by mac.ryan on 2007-03-28
Well, see if it works when the scan is over... If you get in trouble with file and directory permissions (like "you don't have the right to..."), you might consider issuing all the commands as rooot, rather than as normal user. (I assume you are aware of the fact while being logged as root you can **really** mess up things, if you make mistakes...)

In order to open a root shell, you can either select "root terminal" (if present in the menus) or alterantively type:

```
sudo -i
```

from within a regular terminal.

Best luck!

---

### Post by louieb on 2007-03-28
The Ubuntu live CD is not the easiest to use in a rescue. 
Knoppix auto mounts hard drive partitions read only and has a icon on the desktop for each partition  its very good for copying stuff off.
Puppy list your hard drive partitions and one click will open the file manager. and you have read/write permissions and root access. Its really nice for tweaking configuration files.

---

### Post by c174 on 2007-03-30
Thanks to everybody!

I learned elsewhere that it should also be possible to mount a disk using the "System administration" menu.

Well, the reason I need this, was to correct errors on my system. Finally, I have simply done a complete reinstall...

Thanks again :)

---

