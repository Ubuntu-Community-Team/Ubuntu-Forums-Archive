---
title: "Root"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by ThRixXx on 2007-09-24
Hi i googled it but couldn't find anything help full..

Can anyone explain to me how to run as Root ? I have to run as "Root" to install the NVIDIA driver..

---

### Post by wolfen69 on 2007-09-24
```
sudo -s -H
```

---

### Post by Maestro23 on 2007-09-24
Root Sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ThRixXx on 2007-09-24
How do i not Run the "X" so that i can install my NVIDIA Driver ?

---

### Post by fedira on 2007-09-24
Is this helpful?
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04)

---

### Post by yabbadabbadont on 2007-09-24
Logout.  Hit Ctrl-Alt-F1.  Login at the text prompt.  Run:
```
sudo -i
```
Followed by:
```
/etc/init.d/gdm stop
```
Now run the Nvidia installer.

Type "reboot" to restart the machine.

Edit: Follow the guide linked to by fedira.  That is a better solution.

---

### Post by ThRixXx on 2007-09-24
> **yabbadabbadont said:**
> Logout.  Hit Ctrl-Alt-F1.  Login at the text prompt.  Run:
```
sudo -i
```
Followed by:
```
/etc/init.d/gdm stop
```
Now run the Nvidia installer.

Type "reboot" to restart the machine.

Edit: Follow the guide linked to by fedira.  That is a better solution.

After i typed the /etc/init... I cant type cd desktop cause it says "no such file or directory":(

---

### Post by ThRixXx on 2007-09-24
..... Help ....

---

### Post by sumguy231 on 2007-09-24
There is no desktop folder, it's called Desktop (File and folder names are case sensitive). But why do this the hard way? Read this guide and you won't even need to bother with any of this:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04)

---

### Post by ThRixXx on 2007-09-25
but i hafta do it this way, i wana !! PLease how i get it right ?

---

### Post by mcduck on 2007-09-25
> **ThRixXx said:**
> but i hafta do it this way, i wana !! PLease how i get it right ?

After you type 'sudo -i' you became root, and you are moved into root's home directory. So if you have the driver package on your own Desktop, you need to run cd /home/YOURUSERNAME/Desktop to move where the file is before you can run it. (Replace "YOURUSERNAME" with the actual user name)

---

### Post by phizikal on 2007-09-25
Or  go to System>  Preferencees> Main Menu.

Go to System Tools and add Root Terminal.

---

### Post by mcduck on 2007-09-25
> **phizikal said:**
> Or  go to System>  Preferencees> Main Menu.

Go to System Tools and add Root Terminal.

Even then he (she?) would still need to move into correct directory before running the command.. Besides the installer needs to be run outside of the graphical desktop so the root terminal is no use.

---

### Post by phizikal on 2007-09-25
> **mcduck said:**
> Even then he (she?) would still need to move into correct directory before running the command.. Besides the installer needs to be run outside of the graphical desktop so the root terminal is no use.

Well yeah, your right.

---

