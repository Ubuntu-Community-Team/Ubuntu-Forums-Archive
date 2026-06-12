---
title: "Help!"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-06-28
Ok, I was changing my video driver from "nv" to "nvidia" in the file "/etc/X11/xorg.conf", I went to reboot and I got a ****load of errors. I restarted and threw in a live cd. I don't want to reinstall. Is there a way I can fix that? I don't have nothing backed up, please!

---

### Post by thornomad on 2007-06-28
Have you tried changing your xorg.conf file back to the way it was ?

---

### Post by overdrank on 2007-06-28
> **phizikal said:**
> Ok, I was changing my video driver from "nv" to "nvidia" in the file "/etc/X11/xorg.conf", I went to reboot and I got a ****load of errors. I restarted and threw in a live cd. I don't want to reinstall. Is there a way I can fix that? I don't have nothing backed up, please!

If it was the screen saying xorg errors then just click ok several times and get to the command prompt and login and then run*** sudo dpkg-reconfigure xserver-xorg*** and answer the question and if you dont know the answer then stick with the default answer given.

---

### Post by starcraft.man on 2007-06-28
> **phizikal said:**
> Ok, I was changing my video driver from "nv" to "nvidia" in the file "/etc/X11/xorg.conf", I went to reboot and I got a ******* of errors. I restarted and threw in a live cd. I don't want to reinstall. Is there a way I can fix that? I don't have nothing backed up, please!

First off DON'T CURSE!!! These are not adult forums, and there are plenty of minors around. We have no need for vulgar words.

1) Boot up computer (without live CD) at GRUB select the second option on list labelled (recovery mode).

2) When you finally get to the console type this in:

```
sudo nano /etc/X11/xorg.conf
```

That will open up the xorg in the nano CLI editor.

3) Use the arrows to navigate down to the driver section you changed, replace "nvidia" with "nv".

4) Ctrl + O will save the edits, push enter to overwrite the files (the dialogue will let you save it somewhere else if you like). Then push Ctrl + X to exit.

5) ```
sudo reboot
```

Alternatively: At step two put in:

```
sudo dpkg-reconfigure xserver-xorg
```

You will then be graphically prompted through steps to edit your xorg (make sure at video driver section you pick nv instead of nvidia), since you only changed one line the former is preferable. The latter really only should be if you really have no idea what you changed and what to make it new and clean again.
shitload
Don't panic or curse in future, all problems have solutions, they just haven't been found yet.

---

### Post by phizikal on 2007-06-28
Thanks so much you guys. It wasn't the "nv" i made an error in the line.

its all working now. thanks again. sorry about the panic.

---

