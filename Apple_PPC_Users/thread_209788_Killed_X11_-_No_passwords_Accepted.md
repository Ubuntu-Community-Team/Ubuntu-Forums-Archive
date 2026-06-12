---
title: "Killed X11 - No passwords Accepted"
date: 2006-07-05
forum: Apple PPC Users
---

### Post by applemacmad on 2006-07-05
I had been tweaking the X11 settings, and I broke it, so I cannot boot into the GUI, but I can get access to terminal at the login bit (no GUI either)
I know the command to restore the backup of /etc/X11/xorg.conf, but when I type it in, and asks me for my password, it doesn't accept it.
I am completely 100% I have the right password! Is there some sort of Admin or root password I am not aware off?
Someone please help - I currently have no Ubuntu :(

---

### Post by taurus on 2006-07-05
To write to /etc, you need to belong to groups adm & admin.  Check to see if you belong to any of those two groups by typing from a prompt
```

id

```
Then, just copy the old one over as
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```
Otherwise, reconfigure your X again with
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by tseliot on 2006-07-05
[QUOTE=applemacmad]I had been tweaking the X11 settings, and I broke it, so I cannot boot into the GUI, but I can get access to terminal at the login bit (no GUI either)
I know the command to restore the backup of /etc/X11/xorg.conf, but when I type it in, and asks me for my password, it doesn't accept it.
I am completely 100% I have the right password! Is there some sort of Admin or root password I am not aware off?
Someone please help - I currently have no Ubuntu :([/QUOTE]
Change your password:
Boot in Recovery Mode (Select it from the grub menu as soon as you turn on your computer)

Then type:
```
passwd your_username
```

(of course replace your_username with your username)

then type your new password.

restore the backup of your xorg.conf from there.

Then restart your computer by typing:
```
reboot

```

---

### Post by linear on 2006-07-05
[quote=tseliot]Boot in Recovery Mode (Select it from the grub menu as soon as you turn on your computer)[/quote]
Macs use yaboot, not grub, so there is no "Recovery Mode" selection.

---

