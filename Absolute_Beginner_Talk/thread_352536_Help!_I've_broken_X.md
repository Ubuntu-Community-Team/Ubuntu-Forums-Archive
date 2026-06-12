---
title: "Help! I've broken X"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-02-03
Hi.

This afternoon I thought I was being clever, trying to install the Nvidia legacy binary drivers.
Instead, I've totally broken X.  When I try to run Ubuntu, I get the option to view some error messages (none of which mean anything to me), and then the system boots in text-only mode - which isn't much help, as I don't yet know enough commands to do anything.

I suspect that I wrecked /etc/X11/xorg.conf.  

I was hoping that I'd be able to boot with the live CD, then run the command that generates a new one (as mentioned in the header of xorg.conf).  But when I boot with the CD, it won't let me into the actual hard drive, even when I try as root.

Is there any easy way to fix this, or am I just going to have to write off all my customisations and start from scratch by re-installing?

---

### Post by olejorgen on 2007-02-03
Login in text-only-mode and type:

sudo dpkg-reconfigure -phigh xserver-xorg

This will restore your xorg file to the default state. Take a backup first though

---

### Post by whitefort on 2007-02-03
>>sudo dpkg-reconfigure -phigh xserver-xorg<<

This fixed everything.  I am SO grateful to you.

The helpfulness of people in this forum is just amazing.  Thank you again!

---

### Post by olejorgen on 2007-02-03
No problem  :)

> I was hoping that I'd be able to boot with the live CD, then run the command that generates a new one
You almost got it yourself :P

---

