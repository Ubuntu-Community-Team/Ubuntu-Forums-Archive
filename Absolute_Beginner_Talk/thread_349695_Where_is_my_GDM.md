---
title: "Where is my GDM?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-01-30
I went through a bit of computer trauma in the last few days trying to upgrade my nVidia drivers.
Finally got things back to (more or less) normal today in that I was able to launch the Xserver and see the GUI.
However, for an entirely different reason, I rebooted earlier today and found that it booted only to a TTY1 screen.
Alt-F7 did not bring me back to the GUI.
Similarly
```
sudo /etc/init.d/gdm start
```
did not start anything and gave a message that the gdm command was not found.

I could get back to a (less than perfect) GUI using "startx" in TTY1.
Searching through the /etc/init.d/ folder, I find that indeed there is no gdm file.

I have tried the following code which I found in another thread
```
sudo apt-get update
sudo apt-get install Ubuntu-desktop
sudo /etc/init.d/gdm restart
```

Once again, the "command not found" message appears. Additionally, during the attempted install of Ubuntu-desktop, a message appears saying that the latest version is already installed.

Finally, I checked for gdm in Synaptic and it is marked there as being installed. Nevertheless, I marked it for re-installation. However, no change resulted in that I still cannot get gdm to start.
I did a complete check of the file system for gdm and came up with nothing.

Any ideas what I might be overlooking?

---

### Post by taurus on 2007-01-30
Try

```
sudo apt-get update
sudo apt-get install gdm ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by PaulFXH on 2007-01-30
Thanks for the quick reply.
I tried your suggestion but I get basically the same result as before.
The gdm install says that 
```
gdm is already the newest version.
Ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

The gdm start command again says that
```
command not found
```

This is so strange.

---

### Post by taurus on 2007-01-30
```
locate gdm
ps -A
```

---

### Post by PaulFXH on 2007-01-30
The locate gdm command shows that there are indeed very many gdm files and folders although I cannot tell if any of them, or which, are executable.

Do you want to see the list of files/folders?

The list shown by ps -A indicates that gdm is not running, only startx which is what I used to get to the GUI screen in Ubuntu.

---

### Post by Kevf on 2007-02-11
Same problem here, According to synaptic GDM is intalled, But I can't find it :confused:

---

