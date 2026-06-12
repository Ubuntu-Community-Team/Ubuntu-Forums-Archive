---
title: "font replaced with boxes"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2007-12-24
HELP!
all of my gnome fonts(dialog boxes, loging windows, file names, title bars, etc...) have been replaced with boxes

i ran the command ```
sudo apt-get install ffmpeg sl-modem-daemon
```
and shortly after this problem occured
i have since uninstalled ffmpeg```
sudo apt-get remove ffmpeg
```, sl-modem-daemon```
sudo apt-get remove sl-modem-daemon
```, and all associated packages ```
sudo apt-get auto-remove
```

but the problem still persistes

i can read the terminal, but not too much else

ubuntu gutsy-clean installed about a week or two ago

---

### Post by erginemr on 2007-12-24
I had a similar issue when using Edgy Eft, force-installing a package for Feisty to it. During the process, I had force-updated:
```
libpango libfontconfig1 fontconfig
```
to get the same rectangular blocks you had.

It appears that the above packages and ffmpeg that you have uninstalled share the following packages which relate to system fonts:
```
libpango libfontconfig1 fontconfig libfreetype6 libimlib2
```

So, now that you cannot use the graphical Gnome system:
First, make sure that you do not use any Feisty repositories (assuming that your system is Edgy).
Then, login from a virtual terminal (with Ctrl+Alt+F1) and reinstall the same with:
```
sudo aptitude install libpango libfontconfig1 fontconfig libfreetype6 libimlib2
```

Reboot to see if there is any amendment. If not, you may try playing with your font cache:
```
cd ~
mv .fontconfig .fontconfig.bak
cd /var/cache
sudo mv fontconfig fontconfig.bak

```
Once again, reboot to see if there is any amendment.

These are all wild guesses, but still worth a try.

---

