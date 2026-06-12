---
title: "Installation of 7.04"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by kwlam on 2007-07-15
I have installed ubuntu 7.04 and I have several problems and I would be grateful ifsomebody can help.

1. I have installed the gstreamer plugins. I can play the wmv and quicktime for the websites. However, when I play the quicktime (trailer from websites), there is no sound. What is the problem and how to fix i?

2. I can listen to the internet radio with realplayer. How to play it with WMP?

3. I inserted the dvd into the cdrom. Totem plays it automatically. However, if I stop it and then click "play the dvd title (something like that)" it doesn't work. Is it due to a bug in the ubuntu?

4. I want to use the special desktop effect. I can use the 'wobble' effect. How to use the 'workspace in a cube" and what is it?

5. I have installed windows XP and ubuntu in the same computer. I want to use the windows xp as default in the grub. How to make it? Also, in the grub menu, the ubuntu and ubuntu recovery were duplicated, what is the problem and how to fix it?

Thanks.

Regards,
KW Lam

---

### Post by freebird54 on 2007-07-15
I'm rerady to crash for the night - but here's a couple of helpers...

4. If you have 4 workspaces, the system (Compiz) can map them on a cube so you can spin between them rather than click down on the lower taskbar.  <ctrl><alt>left-mouse-button I think it is :)

5.  Probably you don't have duplicates - probably the version of the kernel differs in what APPEAR to be duplicates.  The last digits are kernel releases.

One way of changing settings in Grub is to use [GrubEd](http://www.ubuntuforums.org/showthread.php?t=228104).  Or you can directly edit it yourself - doing this (I'm using the terminal commands for easy cut and paste for you).

First make backup

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup070715
```

then, load the config file into an editor

```
gksudo gedit /boot/grub/menu.lst
```

then look for this:
```

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default         0**

```

and change it to what you need (maybe 3? can't see your file! just guessing but try it) - changing ONLY where it is** BOLD**  Keep in mind that the number will have to be the one referring to the choice you want to default to (0=first, 1=second etc)

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default         3**
```


then look for blocks of entries like this:

```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,3)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
```
### BEGIN AUTOMAGIC KERNELS LIST


and eliminate them if you don't want to see them when booting. (highlight and delete).  [B]Make sure to leave at least the newest one, and a rtecovery console option!
[/B]

Another thing you might consider doing is moving the XP entry )the ENTIRE BLOCK!) AHEAD of the others, then you don't need to change the default boot number.  if you do this - you MUST PUT IT AHEAD OF A LINE READING LIKE THIS:

```
### BEGIN AUTOMAGIC KERNELS LIST
```

If you mess up, you can recover the backup file you made earlier with

```
sudo cp  /boot/grub/menu.lst.backup070715 /boot/grub/menu.
```lst

Hope that helps...

---

