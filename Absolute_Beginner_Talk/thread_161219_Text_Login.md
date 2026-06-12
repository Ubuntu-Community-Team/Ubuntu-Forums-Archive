---
title: "Text Login"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by utab on 2006-04-16
dear all,

Could anyone tell me how to change to the text login in Ubuntu??

I tried with the initdefault line set to 3 in /etc/inittab file but no use still the graphical login??

Thx.

---

### Post by trent dillman on 2006-04-16
Install sysv-rc-conf and turn off gdm at all runlevels.

```
sudo apt-get install sysv-rc-conf
```

---

### Post by djbon2112 on 2008-01-30
HELP! I did what you said, but now my Ubuntu install is completely text-only! I tried undoing what I'd done by re-enabling GDM with that command again, but it's still text-only! What can I do to reverse this? I want my system to boot and logon as text-only, but start GNOME as soon as I log on. With GDM disabled as you said it just stayed as text, and I don't know the command to start GNOME. Now after re-enabling them, it's still text only but boot seems to hang.

---

### Post by Rocket2DMn on 2008-01-30
If you're in runlevel 3, you need to be in 5, so try running
```
init 5
```
If GUI doesn't appear, do CTRL+ALT+F7 (this is the TTY with GUI).

---

### Post by djbon2112 on 2008-01-30
Alright, I was in Windows and when I booted back into Ubuntu everything is fine (I guess it took a couple reboots for it to re-read whatever file was changed)!

But I still want a text boot/log in...


Here's what the command given gives me (ignoring the other rows) with default values:

```
       1        2        3        4         5         0        6        S

GDM            [X]      [X]      [X]       [X]


```

What should I uncheck to have a logon-as-text but GUI right when I log on? (I had tried disabling all of them before).

And on the sidenote, how do I make the boot text-only as well (no bootscreen)? Do I just remove the "quiet" flag in the /boot/grub/menu.lst file under the Ubuntu entry? My current entry looks like this:

```
title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=add5b54e-ccfb-46f6-ba6f-78fa80564a20 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet
```

---

### Post by Rocket2DMn on 2008-01-30
Removing the quiet flat will get rid of the splash screen with the progress bar and just show you the text during the boot sequence (which is what you want), but you will still be at the gdm login screen.
I don't think you can do a text login then get dropped into a GUI.  What you probably CAN do though is disable X from starting automatically, then login at the terminal and type "startx" to open the GUI.
Why do you want a text login anyway if you're going straight to a GUI?

---

### Post by djbon2112 on 2008-01-30
It's not so much that I WANT a text logon, it's that there isn't a logon screen I've seen that I like. I want something really simple, like the "Happy GNOME" logon screen but minus the entire bottom part and with a black background, or the Human one without the Ubuntu logo and again a black background. Pretty much, the "Lock screen" dialog. This just seemed easier, but I guess it isn't.

---

### Post by Rocket2DMn on 2008-01-30
Try going to System->Administration->Login Window and hitting the Local tab.  There you can select styles and themes for the login window.  I've never tried most of these myself, but Plain style may be what you want (or you can customize one yourself).

---

### Post by djbon2112 on 2008-01-30
> **Rocket2DMn said:**
> Try going to System->Administration->Login Window and hitting the Local tab.  There you can select styles and themes for the login window.  I've never tried most of these myself, but Plain style may be what you want (or you can customize one yourself).

The plain one is a little ugly (text is much too big for my taste and I don't like the colour scheme. I'd like to make my own, or customize the plain one, but I've got no idea where to start (this is what I'd prefer anyways).

---

### Post by Rocket2DMn on 2008-01-30
[http://www.gnome-look.org/](http://www.gnome-look.org/) has some cool themes as well as login screens (when the site works anyway).

---

### Post by djbon2112 on 2008-01-30
Perfect. I was looking for a site like that early (it was like art.gnome.com or something that someone linked to) and I couldn't find any download links! Found one I love on the second page :p Thanks a lot!

---

