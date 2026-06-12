---
title: "Booting server version Ubuntu 6.06"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by jagannath on 2006-06-08
On my standalone desktop PC, I have made the mistake of installing the server version of Ubuntu 6.06. Being an absolute newbie, I do not know how to proceed with the booting. After inputting the username and password I get the command line with the ~$ sign. What command should I give here to proceed further to load the Linux. 

Thanks for any help.

Jagannath:confused:

---

### Post by verbatim210 on 2006-06-08
are you trying to get into the ubuntu GUI?

---

### Post by mostwanted on 2006-06-08
The server version doesn't come with a GUI but with lots of server tools insetad; you should have downloaded the regular version. You can install the GUI from the regular Ubuntu if you input this command:
```

sudo aptitude install ubuntu-desktop
```

It will ask for your password. After it's done downloading and installing, reboot the computer by typing

```
sudo reboot
```

Then it should log into Gnome.

---

### Post by jagannath on 2006-06-08
If I were to use this code: sudo aptitude install ubuntu-desktop, I need to be connected to the Internet in order to download the GUI, right? 
Can I download the GUI through my Win98 OS and install it??
Otherwise, is there a way to uninstall the server version and install the regular version. Of course, without affecting the Win 98 OS??

Please advise,

Thanks,
Jagannath

---

### Post by mostwanted on 2006-06-08
Download the regular ISO and reinstall.

---

### Post by jagannath on 2006-06-08
Will do that. Thanks.
Wonder if there is a way to uninstall the server version, though?

---

### Post by taurus on 2006-06-08
When you install the desktop version, it will erase your drive so no need to uninstall the server version first!!!  Just a waste of time anyway.  So, make sure you tell the installer to format your drive as ext3 first.

---

### Post by jagannath on 2006-06-08
[QUOTE=taurus]When you install the desktop version, it will erase your drive so no need to uninstall the server version first!!!  Just a waste of time anyway.  So, make sure you tell the installer to format your drive as ext3 first.[/QUOTE]
Thanks. But the problem is that the server version is on one of the partitions and I have Win 98 also residing beside it. I'd ideally like to keep the Win98 also, at least till I get the hang of Ubuntu Linux and am able to configure my modem to connect to the internet thru Ubuntu Linux !?

Is there a way out, please?

Thanks,

---

