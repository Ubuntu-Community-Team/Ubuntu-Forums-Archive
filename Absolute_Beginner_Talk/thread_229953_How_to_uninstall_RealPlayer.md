---
title: "How to uninstall RealPlayer?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by woodlandjustin on 2006-08-05
I installed RealPlayer10GOLD from the realplayer site, and now I want to uninstall it. I installed it just by following their instructions. Now I tried to use Synaptic Package manager to uninstall it but using the search function, it cannot find RealPlayer, nor RealPlayer10GOLD. How then may I uninstall it?
Thank you
Justin

---

### Post by jordilin on 2006-08-05
You'll have to remove it manually. Realplayer only installs a binary file named realplay, its icons and some more, not a lot. Just type:
```
locate realplay
```
and delete its entries. You'll have to delete some of them with sudo privileges.

---

### Post by woodlandjustin on 2006-08-05
> **jordilin said:**
> You'll have to remove it manually. Realplayer only installs a binary file named realplay, its icons and some more, not a lot. Just type:
```
locate realplay
```
and delete its entries. You'll have to delete some of them with sudo privileges.

I undertand how to follow you instructions for locating it, but how do I "delete its entries"?
Thank you
Justin

---

### Post by jordilin on 2006-08-05
In Linux, open a Terminal (Applications->Accessories->Console (or Terminal)) and go with the command "cd" to each directory where the file is. Then, to remove it type:
```
sudo rm -f nameofthefile
```
if it's a directory
```
sudo rm -rf nameofthedirectory
```
sudo is necessary when you are not the owner, i.e you installed the realplayer with sudo privileges.

---

### Post by jis on 2006-09-09
Thanks, jordilin. If your instructions work, they should be linked to [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods) . 

The locate command outputs file names nicely. Could its output be piped somehow to rm command so that you would not have to delete each entry manually by separate command? Or could a shell script be used to do the job?

---

### Post by jis on 2006-10-07
Is it possible to uninstall RealPlayer10 this way:

Install the RealPlayer10 from .deb file as told in
[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

I suppose this overwrites the old installation. Does it?

Then you can uninstall RealPlayer10 using Ubuntu's package management system by 
```
sudo dpkg -r realplayer
```
or by using Synaptic.

I just installed the realplayer again and now I can see the version 10 in Synaptic. I checked that not all installed files contain word "realplay" so maybe it is not enough to delete the entries given by the locate command.

---

### Post by jis on 2006-10-09
I continued where I was and unistalled realplay by selecting "Mark for Complete Removal" in Synaptic. Synaptic did not complain, but obviously did something. However, I still have 'realplay' files in my system, see the attachment. I can even run the RealPlayer by typing /opt/realplay in the command line. Is there any efficient way to remove the realplayer?

BTW. [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods) has been updated.

---

### Post by jis on 2006-11-12
From [here]("https://bugs.helixcommunity.org/show_bug.cgi?id=5434"):
> If the released RealPlayer has been installed using the .bin file and not a .rpm or .deb, there is no uninstall feature. This is by design. The next version of the RealPlayer will include an uninstall script

However, I found *install.log* file at the installation directory. Maybe I could uninstall using the information in my *install.log*. I am going to ask this in helixcommunity.org since there is no Real customer support for Linux.

---

### Post by Literatka on 2007-02-19
I need help uninstalling it from my home directory but I can't get access to it.

---

### Post by enriquecm on 2007-02-19
> I need help uninstalling it from my home directory but I can't get access to it. 

NAUTILUS

Create new file:
```
/usr/share/applications/Nautilus&#8722;root.desktop
```

Add this and then save
```

[Desktop Entry]
Name=Examinador de Archivos (Root)
Comment=Navega por el sistema de ficheros con el examinador de archivos
Exec=gksudo "nautilus &#8722;&#8722;browser %U"
Icon=file&#8722;manager
Terminal=false
Type=Application
Categories=Application;System;

```

And then go to u Home folder :popcorn:

---

