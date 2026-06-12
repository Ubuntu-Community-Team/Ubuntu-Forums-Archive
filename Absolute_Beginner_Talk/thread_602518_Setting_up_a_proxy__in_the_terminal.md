---
title: "Setting up a proxy  in the terminal"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Lavaeolus on 2007-11-04
Hello,
I deleted the packages alsa-base and alsa-utils, which accidentally also removed some other important packages, so now the graphical ubuntu won't boot anymore. I'm trying to redownload these using the shell, but to connect to the package-server i have to use a proxy. So how do I configure my proxy settings using the shell?

Also, how can i install/remove single packages, without affecting a bunch of other packages that seem to be linked to them?

---

### Post by meatpan on 2007-11-04
Can you post the commands you ran, and associated error messages?

---

### Post by DezSP on 2007-11-04
You can reinstall the neccessary packages from the LiveCD, though I'm unsure of how exactly you use it as a repo from the command-line, Google probably has the answers. Good luck!

---

### Post by Lavaeolus on 2007-11-04
I cant copy/paste them, because ubuntu won't boot in graphics mode and I can't get in the internet from there (because the proxy isn't configured), but here's what I did:
```
root@benno-laptop:~# apt-get install ubuntu-desktop
The following packages were automatically installed and are no longer needed:
[...] (if you need it i can type in alle the package names and categories, but it's just the standard messages)
The following NEW packages will be installed:
alsa-utils fast-user-switch-applet gdm gnome-games ubuntu-desktop
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 5016kB of archives.
After unpacking 24.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
0% [Connecting to archive.ubuntu.com]
```

It just stops there, because connection is impossible without using the proxy (i'm connecting to the internet my university's net)

---

### Post by Lavaeolus on 2007-11-04
I don't know how to access the Live-CD from the shell.

```

root@benno-laptop:~# cd /media
root@benno-laptop:/media#dir
cdrom cdrom0 hda1 hda5 hda6 hda7
root@benno-laptop:/media# dir cdrom -a
. ..
root@benno-laptop:/media#cd cdrom0 -a
. ..

```

Using google I can only find APTonCD, which, of course, I can't install without setting up my proxy.

---

