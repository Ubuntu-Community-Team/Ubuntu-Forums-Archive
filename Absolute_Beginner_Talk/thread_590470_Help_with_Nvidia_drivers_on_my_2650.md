---
title: "Help with Nvidia drivers on my 2650"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Coolride on 2007-10-24
I found a link that has the fix, but i can't back in to my desktop because of a gargled screen.
If I hit ctrl-alt-f1 I can faintly see the terminal. My big problem is, if this is not enough, at the end of this post , the poster figured out you have to rename a file, and change a setting  to correct the problem with the motherboard and nvidia drivers. My problem is I'm just learning the ropes , and only have about 2 days on Linux, so I'm lost. On the second page of the post they figured it out, if someone could walk me threw it using my faint terminal screen, this would be a friggen miracle, if it could be done. I followed the Envy instructions of course, that's how I got to this point to begin with. Thanks for any takers.:lolflag:
[http://ubuntuforums.org/showthread.php?t=186294&highlight=2650&page=2](http://ubuntuforums.org/showthread.php?t=186294&highlight=2650&page=2)

---

### Post by jfinkels on 2007-10-25
The great thing about Linux is breaking your system, and then fixing it! Welcome :D

Well it isn't clear from the thread where the file is, but linux gives us plenty of tools to find files.

To build a searchable database of filenames, type the following at the command prompt:```
sudo slocate -u
```
This will create a database searchable with the 'slocate' command.

Once the program completes, you can search for any filename by typing:```
slocate sis-agp.ko
```

It should return this (if you are using Ubuntu 7.10 Gutsy Gibbon):```

/lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/sis-agp.ko

```

To rename that file, first type the following to change your current working directory:```
cd /lib/modules/2.6.22-14-generic/kernel/drivers/char/agp/
```
then rename the file using the 'mv' command (which moves or renames files):```
sudo mv sis-agp.ko sis-agp.ko.bak
```We could rename it anything really, but we choose to rename it to 'sis-agp.bak' to keep it as a backup (you will sometimes see backups as filenames ending in '.bak').

Now that that is renamed, it looks like you may need to add or modify an option in your xorg.conf.

The file '/etc/X11/xorg.conf' is the configuration file for the X server (the program in charge of graphical windowing systems on your computer). YOU SHOULD ALWAYS MAKE A BACKUP **BEFORE** EDITING YOUR XORG.CONF FILE by doing this:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

You can edit it using the 'nano' text editor by typing the following:```
sudo nano /etc/X11/xorg.conf
```

Under the section that says:```
Section "Device"
``` make sure that the driver is nvidia by making the "Driver" option look like this:```
Driver "nvidia"
```

Now it also seems like you should add the following option to this section:```
Option "NvAGP" "0"
```I don't really know what this does, and its not even very clear that you are supposed to add it to this section, but I believe this is correct.

Now save by pressing <Ctrl>+<O> and exit with <Ctrl>+<X>.

Now try to start the X window system by typing "startx", or you may try rebooting.

---

### Post by Coolride on 2007-10-25
Thanks for your time, I'm going to get on it see what I can do.:)

---

