---
title: "How to startx Ubuntu without enterring GNOME login session"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-05-29
I donn't wanna startx GNOME when I startx UBUNTU, so how to configure it?
Thanks.

---

### Post by cskeide on 2006-05-29
Do you mean you don't want to start the x server at boot?```
sudo update-rc.d -f gdm remove
```

Or not start gnome-session when using startx?```
touch ~/.xsession
chmod +x ~/.xsession
```

---

### Post by mellibra on 2006-05-29
what does "sudo update-rc.d -f gdm remove" mean?

---

### Post by cskeide on 2006-05-29
update-rc.d is used to configure which services start at boot time. the command I gave you will remove gdm (GNOME display manager) from the startup. this means that when you start your computer, you will not be presented with the Gnome login screen.

---

### Post by mellibra on 2006-05-29
Is update-rc.d a file or a command? If it's a file, where is it?

---

### Post by steve.horsley on 2006-05-29
If you want to stop GDM (Gnome Desktop Manager) from running when Ubuntu starts, see below. This will of course leave you at a white-on-black text console after boot.

To stop GDM at boot:
**sudo rm /etc/rc2.d/S13gdm**

To restore GDM at boot:
**sudo ln -s ../init.d/gdm /etc/rc2.d/S13gdm**

What this is doing is deleting or recreating a link from the directory that contains the runlevel-2 services to the actual gdm start/stop script.
 
You may find it easier to install the bum package (System->Admnistration->Boot Up Manager) and use that to enable/disable the gdm service. Amusingly, the existing services utility (System->Administration->Services) cannot disable GDM, because as soon as you disable the service X gets killed and you don't have the option to save the changes.

---

### Post by cskeide on 2006-05-29
[QUOTE=mellibra]Is update-rc.d a file or a command? If it's a file, where is it?[/QUOTE]
It's a command.

---

### Post by nalmeth on 2006-05-29
What is it that you don't want? GDM? GNOME? BOTH?
Do you just want the command line? Or do are you looking for a different Desktop Environment?

---

