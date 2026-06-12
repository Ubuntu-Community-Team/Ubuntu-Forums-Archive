---
title: "how do i repair broken dependencies"
date: 2012-05-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mattgeb84 on 2012-05-22
ubuntu 12.04 running xfce
i cant install kdenlive because of broken dependencies, when i open synaptic and click fix broken packages the apply marked changes option is whited out how do i fix these broken dependencies

---

### Post by roelforg on 2012-05-22
Run
```

sudo apt-get update
sudo apt-get install -f

```
(yes, without any package in the command, just copy and paste)
This will fix any dependency problems.

---

### Post by sikander3786 on 2012-05-22
And if you encounter any errors, please post the complete output from the 'apt-get install -f' command.

---

### Post by mattgeb84 on 2012-05-22
thank you so far so good kdenlive has been installed im just messing around with it for now to see if everything still works right.
thank you again

can i use this command whenever ubuntu complains of broken dependencies ??

---

### Post by mattgeb84 on 2012-05-22
ohh one very weird thing after it was installed kdenlive does not show up in the multimedia category or any category in the xfce app pull down menu i had to launch it from the terminal ??

---

### Post by sikander3786 on 2012-05-23
Don't know why the shortcut isn't showing up. As a workaround, run this in your Terminal:

```
echo "[Desktop Entry]
Name=Kdenlive
Exec=/usr/local/bin/kdenlive
Icon=kdenlive
Terminal=false
Type=Application
StartupNotify=true" | sudo tee ~/.local/share/applications/kdenlive.desktop
```

Now open up your home directory, press 'Ctrl + H' to see hidden files, navigate to '.local/share/applications' and drag and drop the newly created 'kdenlive.desktop' file to your Unity Launcher.

Or for having a shortcut at your desktop, you can follow this one as well:

[http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html](http://www.tuxgarage.com/2011/10/creating-desktop-launchers-in-11-10.html)

And yes, you can run that 'apt-get install -f' command whenever you find some broken packages on your system. But that shouldn't happen too often. :)

---

### Post by anaconda on 2012-05-23
> **mattgeb84 said:**
> 
can i use this command whenever ubuntu complains of broken dependencies ??

You can try. It wont solve all dependency issues though.

---

