---
title: "woops, i just crashed my x-server :("
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by spot-berlin on 2007-07-01
hi everybody,

i did a stupid thing - i crashed my x-server :(
how did i do it?
i tried to follow the instructions on this link:
[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)
unfortunately, i guess i got the part where it says "Under the screen section, add the following line:Option “RenderAccel” “true”." wrong.
 It did not specify where to put it, so i just entered it under the last "end of subsection" or something, hit the three buttons and gone was i and so was my x. :(

up to there, i guess i did everything right. that means that i did make a backup of my correct config settings. unfortunately, i have no idea how to get it back, as i dont have any graphical interaface what so ever, just textlines.

who can help? it would be really appreciated.

spot

---

### Post by evilghost on 2007-07-01
Login using your username/password.

```

sudo su
sudo apt-get install nano
nano -w /etc/X11/xorg.conf

[Remove the renderaccel option you added, save the file (CTRL-O) and exit (CTRL-X)]

/etc/init.d/gdm stop
/etc/init.d/gdm start

```

---

### Post by spot-berlin on 2007-07-01
i cant even make it to the login window :(

---

### Post by evilghost on 2007-07-01
Try using one of the virtual terminals.

CTRL-ALT-F2 all the way to F6.  F7 is usually the X session. :)

---

### Post by spot-berlin on 2007-07-01
my fault - when you said login i thought GUI. i figured out how to log in in the text mode.
i followed the steps
after the "nano -w/...." i get a list of commands (or something else) like "-m mouse". i guess it is just scrolling down too far and all i can read is the small print? how do i stop this?
I guess the problem is that i am not used to the very basics of text based user interface.
anyway, how to i delete the "evil line" in my config?

or is there maybe a way to just tell ubuntu to forget about the new config and replace it with the one i backed up?

---

### Post by evilghost on 2007-07-01
No problem regarding the command-line text-editor.

Try this instead of the nano stuff.

```

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
/etc/init.d/gdm stop
/etc/init.d/gdm start

```

I put RenderAccel in the "Device" section of my config, and this is acceptable according to NVIDIA, [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/README/appendix-b.html)

---

### Post by spot-berlin on 2007-07-01
phew, that solved it!

thanks mate, thank you so much!
i wish my mercedes-repair shop was as quick, competent and friendly :)

all the best from berlin!

---

### Post by evilghost on 2007-07-01
Always glad to help a fellow Ubuntu user :)

---

