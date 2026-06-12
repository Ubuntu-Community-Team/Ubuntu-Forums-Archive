---
title: "[SOLVED] Wifi Help w/ Drivers Loading"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Promaster91 on 2008-03-24
Hi I recently installed the madwifi drivers for my computer. The drivers work great however when I reboot my computer, the drivers don't start up. I have to go to the terminal to type in these commands.
```

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

```
Is there anyway I can make it so that these commands are loaded on startup? Thanks. :)

---

### Post by joshrobinson on 2008-03-24
```
sudo gedit /etc/modules
```

---

### Post by Promaster91 on 2008-03-24
That didn't work... I even tried to run the commands in sessions. Anybody else have any ideas.

---

### Post by joshrobinson on 2008-03-24
you just add the names of the modules (the drivers)
without the sudo modprobe command, so you just want to add the following to the list

ath_pci
wlan_scan_sta

then save and close

---

### Post by Ptero-4 on 2008-03-24
> **Promaster91 said:**
> That didn't work... I even tried to run the commands in sessions. Anybody else have any ideas.

press alt-f2 to bring the run dialog, then type gksudo gedit in it. You will see a password dialog box, input your password, then a text editor will appear, insert the names of the two modules each one followed by a new line (what you get when you press the "enter" key in a text document), save and exit the text editor.

---

### Post by Promaster91 on 2008-03-24
Wow, I am a complete idot. I use // (Java) to coment out lines instead of # (C, i guess??). Thanks joshrobinson my wifi works now.

---

