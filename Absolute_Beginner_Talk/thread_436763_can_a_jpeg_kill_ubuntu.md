---
title: "can a jpeg kill ubuntu"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by kman14 on 2007-05-08
i was dragging a jpeg file (thumb nail) on my desk top and accidentally let it go over the menu panel/bar at the top of my screen.
the picture disappeared then the computer froze and i couldn't do anything but turn the power on and off.
when it restarted it i was able to type my  login but then it would freeze again and not bring up the desktop.
sometimes it tries to load - doesn't and then goes back and asks for my login again and then would freeze again etc etc.

any help with how to fix this would be great.

i'm using feisty and haven't had any problems with it.

---

### Post by insane_alien on 2007-05-08
hmm, i can't recreate the problem. anything more you can tell us?

---

### Post by mcduck on 2007-05-08
You can just drag&drop image files to panels to use them as panel backgrounds. Perhaps the image is so big that the panel now freezes trying to open it as background, and that's causing your problem..

---

### Post by kman14 on 2007-05-08
mcduck, that makes sense - i have no idea how to fix it though.
is there a way that i can delete the image using the terminal or starting in recovery mode?

thanks.

---

### Post by mcduck on 2007-05-08
> **kman14 said:**
> mcduck, that makes sense - i have no idea how to fix it though.
is there a way that i can delete the image using the terminal or starting in recovery mode?

thanks.

I think you could try to browse to directory where the image is and rename it or something. Just hit Ctrl-Alt-F1 and log in to get to the command line. then, assuming the image is on your desktop, move there with 'cd Desktop', then check the name of the image by running 'ls', and finally rename the image with 'mv oldname newname' (replace the oldname with the name of your image, and newname with just some new name).

Also the panel background could be changed using gconftool-2, although the hard thing is that every panel has it's own name so I can't just give you the exact command to change the panel's background. however, if you run ```
gconftool-2 -R /apps/panel/toplevels
``` to check what is the right name for the panel (look for the panel that actually has image key set to something..), you can then set the panel to use GTK background instead of image by running this: ```
gconftool-2 --type string --set /apps/panel/toplevels/PANEL NAME HERE/background/type "gtk"
``` (use the name for the panel you got with the first command).

If that's not enough, also reset the background image setting: ```
gconftool-2 -u /apps/panel/toplevels/PANEL NAME HERE/background/image
```

---

### Post by kman14 on 2007-05-09
thanks mcduck

it's all good now.

thanks for the help.

---

