---
title: "blank screen during bootup, afterwards normal"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by lila on 2008-01-03
Hello,
installed Gutsy a few days ago.  On the whole, working fine if a bit slow (think I might get a bit more RAM soon).  A few initial problems ironed out by reading other people's experiences (great tool these forums) and one by posting.
One last problem:  during boot up, the screen goes blank, until the login window.  Then it goes blank again, until the desktop appears.  With Breezy (which I had before) I could follow the whole boot up process because it was telling me what it was doing, and at certain points during the process one could get into the Bios.  Here, there is a little bit of Bios right at the beginning, but it's so fast that I can't read it before it disappears, so I don't know what key to hit to get in there.  Not that I feel like getting into the bios the whole time, but it would be nice to be able to, in case of problems.  And it's nice to be able to read what the computer is doing during boot up, I learn bits about it every time.

Any idea how I can get it to show?
Thanks!
Lila

---

### Post by philinux on 2008-01-03
Easy way.

Install and run startupmanager from synaptic.

Tick the box to show startup messages etc.

---

### Post by GSF1200S on 2008-01-03
> **philinux said:**
> Easy way.

Install and run startupmanager from synaptic.

Tick the box to show startup messages etc.

Note to self: do NOT do this if youre on KDE ;)


EDIT* reason: youll download many gnome libs just for this program. The OP could just turn off the bootsplash via  quiet splash as a boot parameter

---

### Post by lila on 2008-01-03
Thanks to both of you,
I'm on gnome, and it's working - sort of. I've now got quite a lot more bios than before, and a bit where I can get into it, and I made the delay longer to have a bit of time to read, but it still won't do that friendly thing breezy used to do with
 "now loading ...   ok" with the occasional "failed" which would tell you where the problem is.
I ticked everything that I could to "show during startup".
Does Gutsy not do this?
Lila

---

### Post by NilsE on 2008-01-03
In a terminal 

gksudo gedit  /boot/grub/menu.lst

and remove quiet from the boot/vmlinuz line and see if that does it for you.  Can always put it back or rename the backup file.

---

### Post by lila on 2008-01-03
> **NilsE said:**
> In a terminal 

gksudo gedit  /boot/grub/menu.lst

and remove quiet from the boot/vmlinuz line and see if that does it for you.  Can always put it back or rename the backup file.

... there is no mention of "quiet" anywhere.  There is something a bout a menu hidden by default, but I don't dare touch it without knowing what it is exactly.
Lila

---

### Post by NilsE on 2008-01-03
> **lila said:**
> ... there is no mention of "quiet" anywhere.  There is something a bout a menu hidden by default, but I don't dare touch it without knowing what it is exactly.
Lila
OK, then that is the most grub can control of the verbose boot stuff.

I would not touch the menu hidden thing.  That only determines whether you need to hit escape or not to see the grub menu or not.

---

### Post by Mazza558 on 2008-01-03
Try this:

```
sudo gedit /etc/usplash.conf
```

Change the X and Y resolution to match your monitor.

Then apply the changes:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

and restart.

---

### Post by pieterjanvu on 2008-01-05
If you want to see all the text in the console for the boot up you can remove "ro quiet splash" in the menu.lst after kernel line. 
sudo gedit /boot/grub/menu.lst 
Also remove quiet from bottom of the boot option

it should look something like this
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic [COLOR="Red"]ro quiet splash[/COLOR]
initrd		/boot/initrd.img-2.6.22-14-generic
[COLOR="Red"]quiet[/COLOR]

---

### Post by jimmyxx on 2008-01-05
> **Mazza558 said:**
> Try this:

```
sudo gedit /etc/usplash.conf
```

Change the X and Y resolution to match your monitor.

Then apply the changes:

```
sudo update-usplash-theme usplash-theme-ubuntu
```

and restart.

I'm on a ThinkPad T40 and was having the same problem described in this thread. Following your suggestion worked for me. The usplash.conf file was showing 1280x1024 resolution and my laptop only supports 1024x768

thanks! :guitar:

---

