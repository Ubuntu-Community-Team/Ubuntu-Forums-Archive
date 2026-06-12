---
title: "WPA Gui"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-06-28
Has anyone ever tried the WPA Supplicant GUI?  It is a GUI (obviously :D ) that scans for your wireless LAN and allows graphical configuration of the wpa_supplicant.conf file.  So you can set your WPA encryption key, etc.

Anyhow, everytime I load it, it says that it cannot find the wpa_supplicant.conf file (or whatever it's called).  Do I need to create it (wpa_supplicant is installed)?

---

### Post by Maggot on 2006-06-28
Never knew there was a GUI for WPA Supplicant.  I always had a wpa_supplicant.conf in /etc but just checked and its nowhere to be found yet my wireless works. :-k 

One thing I've notice with ubuntu and wireless....it's a pain to configure and get working. When I do get it working I have no idea how I did it because I tried so many things. hahahaha.

What's the package name of this GUI anyways?

edit: Just had a thought...maybe because I'm using Gnome network manager the conf file doesn't exist?

---

### Post by ubuntuuser on 2006-06-28
```
sudo apt-get install wpagui
```

---

### Post by Maggot on 2006-06-28
I just quickly installed it and get the same problem. I have wpa_supplicant installed but I'm not going to mess with it because its working ;)

---

