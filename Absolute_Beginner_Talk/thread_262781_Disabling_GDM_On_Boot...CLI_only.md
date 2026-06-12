---
title: "Disabling GDM On Boot...CLI only"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by chrisfay on 2006-09-22
I have Dapper running Gnome and I want to boot directly to the command prompt without loading Gnome. I would then like to load Gnome from the cli if need be, use the desktop, then when finished I would like to get back to the cli without having to reboot. 

I do not want to use the virtual option to switch between the cli and desktop; I want to completely bypass loading the gnome session on startup to save on resources.

I have read a couple somewhat outdated docs which said to remove the rc.d entry for the gdm daemon using:

```
sudo update-rc.d -f gdm remove
```

..then create a .xinitrc file in my home directory containg one line:

```
exec gnome-session
```

...which would allow me to use 'startx' to start gnome when needed.

I was curious if this is the easiest way of going about this or if this is totally off.

---

### Post by b_martinez on 2006-09-22
The absolute quickest way to boot into cli is to edit the grub menu to read:

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro 3 quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

Notice the '3' between the 'ro' and 'quiet' on the kernel line?
Another way is to make runlevel 3 the default by editing the initrc.d runlevel. How to do that I do not know. Maybe one of the more knowledgeable members will explain that.
Bill

---

### Post by chrisfay on 2006-09-22
Thanks for the reply.....I'll look into editing grub.

Can anyone give some personal experience recommendations regarding the best way to do this? I would really like to be able to boot directly to the cli but am warry of editing too much to achieve it as I have some live servers running on the system.

---

### Post by jamesr316 on 2006-09-22
I would like to know this as well. 

I tried editing the /etc/inittab file ->

# The default runlevel
id:2:initdefault:

I changed the 2, to 3, and it still rebooted in Gnome. :mad:

---

### Post by bodhi.zazen on 2006-09-22
Easiest way is to:

[Disable GDM](http://ubuntuforums.org/showthread.php?t=254540&highlight=gdm#3)

Then in home/user_name/.bashrc add the line:```
alias gnome='gnome-session'
```

Log out and back in. To start gnome just type gnome at the CLI.

---

### Post by jamesr316 on 2006-09-22
I tried the info you provided in your linked post:

sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm

and rebooted, still boots up to Gnome. Checked to make sure I actually moved the file, and I did.

---

### Post by steve.horsley on 2006-09-22
> **jamesr316 said:**
> I tried the info you provided in your linked post:

sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm

and rebooted, still boots up to Gnome. Checked to make sure I actually moved the file, and I did.

Aha! But you edited your inittab to boot to runlevel 3 instead of 2. Either change inittab back to runlevel 2 as default, or change the gdm launcher in /etc/rc3.d/S13gdm to /etc/rc3.d/s13gdm.

I thought the runlevels were all the same in Ubuntu, but I just discovered that there are some differences. I don't know why that should be.

---

### Post by jamesr316 on 2006-09-22
EDIT: That did it :) 

Thank you all.

---

