---
title: "Sudo GUI"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-06-23
Hi all,

another crazy question for u all. I have changed te colour scheme of my Kubuntu. However, when i access something like say the network settings section and have to enter my password to gain admin level access it changes back to the default colour scheme. The same happens if i use:

sudo kate .....

so is ther a way that i can log in as root to the gui so i can change the admin colour scheme is this even possible?

niteblind

---

### Post by Mega Man X on 2006-06-23
What if you try:

```
sudo gnome-theme-manager
```

never tried it myself, but I think it should work ^_^

---

### Post by aysiu on 2006-06-23
Graphical applications should use either *gksudo* or *kdesu*, **not** *sudo*.

```
kdesu kate
``` ```
gksudo gnome-theme-manager
```

---

### Post by bruce89 on 2006-06-23
{rubbish}, forgot that is was kdesu in KDE.

---

### Post by niteblind on 2006-06-23
that doesnt really answer the question tho does it guys? I happily take onboard the kdesu comment i was just reading it in another post but how can i get root access to the appearances part of the kde front end?

niteblind

---

### Post by aysiu on 2006-06-23
```
sudo mv /root/.kde /root/.kde.backup
sudo ln -s ~/.kde /root/.kde
```

---

### Post by anodizer on 2006-06-23
Look at step 4 of this guide:
[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by aysiu on 2006-06-23
Am I the only one noticing that niteblind is using Kubuntu, not Ubuntu?

---

### Post by niteblind on 2006-06-23
okay i get the first line.... always a ggod idea to back up but what exactly will the second command do? will i be able to move around the GUI as if i were root?

niteblind

---

### Post by bruce89 on 2006-06-23
[QUOTE=aysiu]Am I the only one noticing that niteblind is using Kubuntu, not Ubuntu?[/QUOTE]
Sorry, I assumed wrongly, and I will never do it again.

---

### Post by niteblind on 2006-06-23
no worries mate it was the though that counts :D if gnome ever make colour scheming easy it may come in handy to know anyway

niteblind

---

### Post by niteblind on 2006-06-23
[QUOTE=aysiu]```
sudo mv /root/.kde /root/.kde.backup
sudo ln -s ~/.kde /root/.kde
```[/QUOTE]

Sorry guys this doesnt work there is no .kde file i am afraid. any other ideas

niteblind

---

### Post by aysiu on 2006-06-23
There is no .kde folder? That doesn't make any sense. Every time I've used Kubuntu, there's always a .kde folder. Are you retyping these commands or copying and pasting them?

It is possible that your styles and themes live in the .qt folder, but you still at least *have* a .kde folder. Can you post the output of these commands? ```
cd
ls -al
``` And could you also try this? ```
sudo mv /root/.qt /root/.qt.backup
sudo ln -s ~/.qt /root/.qt
```

---

### Post by niteblind on 2006-06-24
it looks like it is there but cannot be seen in konq with the hidden files shown

rw-r--r--  1 niteblind niteblind    24574 2006-06-24 11:42 .gtk_qt_engine_rc
-rw-r--r--  1 niteblind niteblind      287 2006-06-21 21:24 .gtkrc-2.0
-rw-------  1 niteblind niteblind      195 2006-06-24 11:20 .ICEauthority
drwx------  4 niteblind niteblind     4096 2006-06-21 21:24 .kde
-rw-------  1 niteblind niteblind      435 2006-06-22 00:28 .kderc
drwx------  3 niteblind niteblind     4096 2006-06-21 21:24 .local
drwxr-xr-x  3 niteblind niteblind     4096 2006-06-21 21:24 .mcop
drwx------  3 niteblind niteblind     4096 2006-06-21 21:35 .mozilla
drwxr-xr-x  2 niteblind niteblind     4096 2006-06-24 11:40 .qt
drwx------  3 niteblind niteblind     4096 2006-06-24 11:29 .Skype
-rw-r--r--  1 niteblind niteblind        0 2006-06-21 21:26 


also tried sudo ln -s ~/.qt /root/.qt
all that happened was that it dropped to the next prompt was something supposed to happen?

niteblind

---

### Post by aysiu on 2006-06-24
That's what's supposed to happen.

Basically, it's saying "Rename the .qt configuration folder in root to be the backup folder. Then create a symbolic link from niteblind's .qt configuration folder to root's so that when root launchers a .qt application, it'll share the same configuration."

Going to the next line means it worked.

I am surprised that .kde doesn't show even when you enable hidden folders/files in Konqueror, though.

---

### Post by niteblind on 2006-06-24
sorry mate still no change.
do u know the name of the file that controls he appearances section of system settings panel?

niteblind

---

### Post by raptros-v76 on 2006-06-24
kdesu kcontrol will allow you to fiddle around with the kde settings as root.

---

### Post by niteblind on 2006-06-24
WELL DONE THAT MAN!!!!!!!!!!!!

cheers matey that worked a treat and i am not longer going blind due to being dazzle by colour changes

thanks again

niteblind

---

