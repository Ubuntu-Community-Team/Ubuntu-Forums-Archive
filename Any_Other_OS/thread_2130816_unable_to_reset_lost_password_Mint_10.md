---
title: "unable to reset lost password Mint 10"
date: 2013-03-30
forum: Any Other OS
---

### Post by ekflet on 2013-03-30
Following the instructions in **[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)** for a dual boot setup, I selected*** recovery*** ***mode***, then located ***Drop to root shell prompt*** and pressed 'Enter'. Instead of getting to a point where I could enter [SIZE=4][FONT=book antiqua]mount -o rw,remount /[/FONT][/SIZE], I got the following: **"Give root password for maintenance (or type Control-D to continue)"**  I obviously don't have the password, and Control-D just took me back to the Recovery Menu.  I am a Linux newbie, and will appreciate any help... thanks,

---

### Post by sudodus on 2013-03-30
Welcome to the Ubuntu Forums :-)

Do you have encrypted home? You can check that when you boot from a live CD/DVD/USB drive, for example the linux mint install drive.

---

### Post by ekflet on 2013-03-30
How would I change the boot sequence (e.g., to CD) if I choose ubuntu rather than Windows at the dual boot menu?

---

### Post by Perfect Storm on 2013-03-30
Moved to Other OS/Distro Talk.

---

### Post by sudodus on 2013-03-30
Boot sequence between drives:

Use a hot key to get into the BIOS menu system and change the boot sequence (before starting grub or any operating system), or use another hot key to get a menu to choose drive to boot from .  These hot keys are often shown one second at the very first boot splash screen at boot.

If you post the computer brand and model, someone might recognize it and tell you about those hot keys. (It can be F9, F10, F12, ESC, Del, ...)

Boot sequence within the internal drive(s):

In a dual boot system with Ubuntu (or Mint which is based on Ubuntu) you can choose which system to boot at the grub menu (where you also have the recovery mode). It is possible to change the default system to boot by changing the GRUB_DEFAULT setting in the file [SIZE=3][FONT=courier new]/etc/default/grub[/FONT][/SIZE]. 0 (zero) points at the first choice line in the grub menu, 1 (one) at the second choice line ... Make this active by the command
```
sudo update-grub
```

---

### Post by ekflet on 2013-03-30
Thanks very much, I'll try your suggestions.  (I do not believe I have an encrypted home.)

---

### Post by sudodus on 2013-03-30
> **ekflet said:**
> Following the instructions in **[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)** for a dual boot setup, I selected*** recovery*** ***mode***, then located ***Drop to root shell prompt*** and pressed 'Enter'. Instead of getting to a point where I could enter [SIZE=4][FONT=book antiqua]mount -o rw,remount /[/FONT][/SIZE], I got the following: **"Give root password for maintenance (or type Control-D to continue)"**  I obviously don't have the password, and Control-D just took me back to the Recovery Menu.  I am a Linux newbie, and will appreciate any help... thanks,

When I do this (drop to root shell prompt), the menu moves one step upwards and at the bottom of the screen there is a line with the root prompt
```
root@computername:~#
```
And I can enter commands like it is described in the psychocats link. But I run Ubuntu 12.04, and this seems to be different in Mint 10, which is another distro and quite old (probably passed end of life). Maybe you have better luck asking for help at the Linux Mint forums.

---

### Post by ekflet on 2013-04-06
Thanks for your  response.  I've been buried with other stuff, but am _very_ appreciative, and will try your suggestions first chance I get. Sorry I didn't thank you right away.

---

