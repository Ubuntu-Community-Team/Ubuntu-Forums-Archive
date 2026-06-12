---
title: "gedit doesn't display anything...."
date: 2005-06-25
forum: Absolute Beginner Talk
---

### Post by TristanMike on 2005-06-25
Hi, could someone give me a hand.  My gedit has stopped displaying the contents.  I'm installing my nvidia drivers and I'm at this point:

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

so when I hit enter, gedit opens and nothing is displayed.  I've been having this problem when running from the terminal but if I were to open it via places--computer etc. I can see it, any suggestions?

TristanMike

EDIT: I did, infact, install my drivers based on the blank file....but I did see this before.  Has anyone experienced this?

---

### Post by Xian on 2005-06-25
[QUOTE=TristanMike]Hi, could someone give me a hand.  My gedit has stopped displaying the contents.  I'm installing my nvidia drivers and I'm at this point:

sudo gedit /usr/share/applications/NVIDIA-Settings.desktop[/QUOTE]
That command works fine on my system.
Are you sure the file has any contents?

Check it with nano as well to verify:
```
sudo nano -w /usr/share/applications/NVIDIA-Settings.desktop
```

---

### Post by TristanMike on 2005-06-25
Thanx for the quick reply,
Now that I look at it, I don't think that it did have contents....still trying to work out the kinks in my greater understand of Linux/terminal/filesystem, but I did notice yesterday, that gedit did the same thing, will try nano as a second opinion, didn't know about it, Thanx
TristanMike

---

### Post by Xian on 2005-06-25
These are the contents of that file on my system:

```
[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;
```

---

### Post by TristanMike on 2005-06-25
Nope, it's there now....hmmm...weird.  Maybe I jumped the gun there, but I could have sworn when I opened up a file to edit with gedit yesterday, it wasn't there.  I had to go to the actual location, copy the file to my desktop, edit it there, and move it back.  Maybe I need to get more sleep or something.  Sorry if I wasted your time.
Thanx
TristanMike

---

