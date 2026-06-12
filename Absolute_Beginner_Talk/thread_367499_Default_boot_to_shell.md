---
title: "Default boot to shell?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by dlreynolds on 2007-02-22
I'm wondering if there is a way to boot Ubuntu to the shell by default without starting x. I tried to google it, but could only find instructions to edit /etc/inittab. I cannot seem to track down that file though, any advice?

---

### Post by louis_nichols on 2007-02-22
Actually, there are several ways to do that, depending on your goal. The easiest way is, at boot time, to choose the recovery mode option. That will only give you a shell.

Another way is to create a separate entry in Grub to start the system in runlevel 1 (hm... I'm not sure at this point whether this wouldn't be identical to choosing the recovery mode, but I think it wouldn't). This is done by appending a 1 at the end of the boot parameters. Or you can do this at boot time, by editing the boot parameters, if you only need to do this once.

Another way, of course, is, if you never want to boot to the graphical desktop, to uninstall all graphicall apps.

---

### Post by Ben Sprinkle on 2007-02-22
In slackware, I opened a file in /etc/rc.d and changed the run level to 3 I belive, 4 is the x server?

---

### Post by louis_nichols on 2007-02-22
The default runlevel in Debian based distros, including Ubuntu, is 2. I know 6 is reboot and 0 is shutdown. I'm not sure about the particularities of the other runlevels.

I think there is a file in Ubuntu also that will allow you to set the default runlevel, but i'm not at my machine right now, to find it. I'm pretty sure there are applications that do the same thing. i'll search for them when I get home.

---

### Post by dlreynolds on 2007-02-22
Hello, I tried to do as you said and add a 1 to the boot parameters. That didn't seem to work.
Here is the relevant section of my /boot/grub/menu.lst :

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro splash 1
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot
 
I also tried adding the 1 to the initrd section, but that did not work either. I hope this is what you were referring to when you said boot parameters.

Anyway, this seems like it should be an easy thing to find out on the net, but I haven't come across anything that works for Ubuntu. Any more ideas?

---

### Post by louis_nichols on 2007-02-23
That's strange. I remember I used that method under Fedora and it worked. I guess it's because of the way the Ubuntu kernel is compiled... I don't have more ideas right now.

Isn't booting in recovery mode what you need?

---

### Post by dlreynolds on 2007-02-23
I guess that'll have to do. Thank you for your help.

---

