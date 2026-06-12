---
title: "Safe Graphic Mode, HELP!"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2008-01-19
How do I do to go in safe graphic mode? Isn't there a key you have to push like in windows (F8 or something similar??)

I tried to install a driver for my video card and the screen is all messed up, can't see a thing. Now, I am really a noob at linux but I had a couple VERY important files that I have to recover.

PLEASE, help.

---

### Post by jleaker01z on 2008-01-19
Restore your old xorg.conf file

Boot up, then press ctrl-alt-f1 for a command prompt.   type in cd /etc/X11

Enter the command dir and look for the old xorg.conf file (probably xorg.conf.backup)

Enter sudo rm xorg.conf

Then enter sudo cp xorg.conf.backup xorg.conf

Then reboot and you should be back to the default video drivers.

---

### Post by fatality_uk on 2008-01-19
Reboot your PC with the LiveCD in and it will give you a GUi once again. From there you should be able to see your HD and files you need. Once you got them, come back and we can get your xconf sorted ;)

---

### Post by VoXoM on 2008-01-19
> **jleaker01z said:**
> Restore your old xorg.conf file

Boot up, then press ctrl-alt-f1 for a command prompt.   type in cd /etc/X11

Enter the command dir and look for the old xorg.conf file (probably xorg.conf.backup)

Enter sudo rm xorg.conf

Then enter sudo cp xorg.conf.backup xorg.conf

Then reboot and you should be back to the default video drivers.

I did like you said but when I tried this

```
sudo cp xorg.conf.backup xorg.conf
```

It said > cp: missing destination file operand after xorg.conf.backup(date)

So anyways I rebooted and now everything seems fine (except that I need to install a driver for my graphic card)

Did the xorg.conf file remade itself to default automatically? (stupid question I know)

Anyways thanks for the help :)

God bless you

---

