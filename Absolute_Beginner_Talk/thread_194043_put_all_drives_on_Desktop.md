---
title: "put all drives on Desktop"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-06-10
I have just installed Xubuntu, and i want to make all my drives accessible from the desktop, in Ubuntu i did this by following the tutorial directly, but the tutorial gives an error on /ect/fstab now

i did find the drives as folders but i want to put them as drives on my desktop.
When i tried to drag and drop to put a shortcut on my desktop, it sorta worked, but when i renamed it from hda1 it gave errors saying some files dont exist

then i somehow got another shortcut to it on the desktop
and when i deleted the first shortcut it took a long time with lots of harddrive noises (that was scary)

(drives as folders and drives as drives refers to, in my experience, the icons.  because it seems like having them as folders means there is a copy)

---

### Post by aysiu on 2006-06-10
A command-line approach may help this, as I don't know how flexible XFCE is (as opposed to Gnome or KDE).

Let's say, for example, that you have a drive called /dev/hda5, and it's mounted at /media/hda5, but you want it to show up on your desktop as /music. ```
ln -s /media/hda5 ~/Desktop/music
``` would put a shortcut to it on the desktop.

---

### Post by notquitehere188 on 2006-06-10
it works, thanks.
no hard drive picture but good enough

---

### Post by dralaroc on 2006-06-10
Ditto on the thanks Aysiu, worked like a champ!

---

### Post by Muzzled on 2006-07-21
For some reason it kills the desktop managing when I do that command and I get a black wallpapper. Whenever I go to Applications/Settings/Desktop Settings/ the "Allow Xfce to manage the desktop" option is always unchecked no matter if I check it or not then it goes back to normal when I delete the link. I can browse the link just fine when in ~/Desktop/music though...

The command I did is:
```
sudo ln -s /mnt/music ~/Desktop/music
```

Any idea?

Thanks.

---

