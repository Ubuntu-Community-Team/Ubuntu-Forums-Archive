---
title: "Ubuntu with more 'sparse' GUI options?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by N Clement on 2007-04-16
Ubuntu is pretty.  I just want to get that out of the way right now.

However, I am wondering about the possibilty of a 'less is more' attitude to gui on Ubuntu.  I have a few questions pertaining to this thought:

1)  How can I make it so that the normal boot up looks like the recovery console boot up.  Is that the only difference with the recovery console--that it has no gui?

2)  What is the deal with <ctl> <alt> <f1> through <f7>?  Is this a good way to just have a command line interface with no grapical interface?

3)  What other good modifications would encourage me to use the command line more?

Thanks for any suggestions (a url to a suggestion is just as good as a suggestion:) )

---

### Post by BarfBag on 2007-04-16
> **N Clement said:**
> Ubuntu is pretty.  I just want to get that out of the way right now.

However, I am wondering about the possibilty of a 'less is more' attitude to gui on Ubuntu.  I have a few questions pertaining to this thought:

1)  How can I make it so that the normal boot up looks like the recovery console boot up.  Is that the only difference with the recovery console--that it has no gui?

2)  What is the deal with <ctl> <alt> <f1> through <f7>?  Is this a good way to just have a command line interface with no grapical interface?

3)  What other good modifications would encourage me to use the command line more?

Thanks for any suggestions (a url to a suggestion is just as good as a suggestion:) )

1.  Yes and yes.  I'm not sure how to turn off splashy, though.

2.  Those are called virtual terminals.  They're basically a way to bypass the GUI if something goes wrong, or if you have to do something outside of xorg.

3.  With a distro like Ubuntu, it's not necessary to use the command line as much.  If you want to, I suggest trying out Arch.  That's what I use.

---

### Post by computerease on 2007-04-16
In the 5 series, Ubuntu server installed with no activated GUI.  You could install it and use it but it wasn't there by default (or, at least, such was my install experience).  Don't know if it is taht way in 6.x.  Ctrl-Alt-F1 gets one to a terminal that will bypass a locked desktop and gain an orderly shutdown.  My question has been the key call to move back to the GUI (Gnome in my case).  I should know (read remember that), but damned if I do.

---

### Post by N Clement on 2007-04-17
Can anyone tell me how to get the boot/shutdown sequences to put their output on the screen rather than have the splash screens?  What are the exact definitions/purposes of all the virtual terminals?

---

### Post by bodhi.zazen on 2007-04-17
The virtual terminals (F1-7) are there for your convenience, you need 1 minimum. You can disable the others if you like. They do not consume much in the way of resources and are secure in that they need a password to log in.

---

### Post by mcduck on 2007-04-17
> **N Clement said:**
> Can anyone tell me how to get the boot/shutdown sequences to put their output on the screen rather than have the splash screens?

You need to edit /boot/grub/menu.lst:

1. hit alt-f2 and run 'gksudo gedit /boot/grub/menu.lst' to open it for editing as root
2. find the line "# defoptions=quiet splash" and remove both "guiet" and "splash"
3. find the actual kernel boot line, "kernel  /boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash", and remove "quiet" and "splash" again.
(If you want, you can increase the console resolution by adding "vga=792" to both these lines. It will make your console use 1024x768 with 24bit colors.)

---

### Post by kerry_s on 2007-04-17
If you really want to learn, you should try doing a custom install. A custom install starts with the base system(command-line) and you build it up from there with everything you want on your system.

net installer-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by BarfBag on 2007-04-17
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by N Clement on 2007-04-17
> **mcduck said:**
> You need to edit /boot/grub/menu.lst:
(If you want, you can increase the console resolution by adding "vga=792" to both these lines. It will make your console use 1024x768 with 24bit colors.)

Any way to make it 1280 by 800???

---

