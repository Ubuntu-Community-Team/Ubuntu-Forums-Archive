---
title: "Change over questions - From Kubuntu to Ubuntu"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-08-21
I've been using kubuntu for sever months now. A new PC has joined the family, and I descided ubuntu would be fun to try out. Because this is a Networking learning machine (I plan to put Windows Server 03 on it too) I went with Ubuntu Server. Problem is, I think maybe I got to comfortable in kubuntu and KDE

what is the ubuntu version of?

k->System Settings

Ksysguard

Kpersonlizer

Konqueror

K3b

Also, I'm used to "Settings" -> "Configure" for almost every window app. How do I configure things like the terminal?

Thanks

---

### Post by Ek0nomik on 2007-08-21
> **ant2ne said:**
> I've been using kubuntu for sever months now. A new PC has joined the family, and I descided ubuntu would be fun to try out. Because this is a Networking learning machine (I plan to put Windows Server 03 on it too) I went with Ubuntu Server. Problem is, I think maybe I got to comfortable in kubuntu and KDE

what is the ubuntu version of?

k->System Settings

Ksysguard

Kpersonlizer

Konqueror

K3b

Also, I'm used to "Settings" -> "Configure" for almost every window app. How do I configure things like the terminal?

Thanks

Ubuntu Server edition doesn't have a graphical interface.

Anways, some replicas:

k->System Settings - This is a control center for KDE, and so I'm not sure what would replace this in Gnome.

Ksysguard - **Gnome System Monitor**

Kpersonlizer - Not able to find something.

Konqueror - **Mozilla Firefox**

K3b - **Gnomebaker**

---

### Post by Seisen on 2007-08-21
Ubuntu server is completely command-line only but if you want a Gui you can install the ubuntu-desktop package using apt-get.

---

### Post by ant2ne on 2007-08-21
"k->System Settings - This is a control center for KDE, and so I'm not sure what would replace this in Gnome."

I NEED this!

"Ubuntu server is completely command-line only but if you want a Gui you can install the ubuntu-desktop package using apt-get."

right, got the ubuntu gui. Is there some way to have it start in CLI, so I have to type startx to make the gui take over?

konq is more than a web browser... it is a file manager/explorer as well. Surfing and file "exploring" all in one. I love that program. Don't tell me there isn't an ubuntu version!

Also, power management?

---

### Post by Ek0nomik on 2007-08-21
> **ant2ne said:**
> "k->System Settings - This is a control center for KDE, and so I'm not sure what would replace this in Gnome."

I NEED this!

"Ubuntu server is completely command-line only but if you want a Gui you can install the ubuntu-desktop package using apt-get."

right, got the ubuntu gui. Is there some way to have it start in CLI, so I have to type startx to make the gui take over?

konq is more than a web browser... it is a file manager/explorer as well. Surfing and file "exploring" all in one. I love that program. Don't tell me there isn't an ubuntu version!

For the record, you can install KDE applications and run them in Gnome.  You will just have to install all the library files in order to run that software (which apt-get will take care of for you).

Gnome does have a file browser called Nautilus.  It is able to connect to FTP servers, connect via SSH and other options.  I don't think it can be used as a web browser though.

---

### Post by dpar on 2007-08-22
KDE Control Center can be replaced by Gnome-Control-Center:biggrin:

---

### Post by Ek0nomik on 2007-08-22
> **dpar said:**
> KDE Control Center can be replaced by Gnome-Control-Center:biggrin:

Man, why didn't aptitude show me that?  :/

---

### Post by ant2ne on 2007-08-23
> **dpar said:**
> KDE Control Center can be replaced by Gnome-Control-Center:biggrin:Hmmm can't run or find this.
```
antsvr@ubuntu:~$ Gnome-Control-Center
bash: Gnome-Control-Center: command not found
antsvr@ubuntu:~$ sudo apt-get install Gnome-Control-Center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Gnome-Control-Center
antsvr@ubuntu:~$ 

```

---

### Post by Ayuthia on 2007-08-23
gnome-control-center is all in lowercase so that is why it was not found.

---

### Post by chrome307 on 2007-08-23
> **Seisen said:**
> Ubuntu server is completely command-line only but if you want a Gui you can install the ubuntu-desktop package using apt-get.

How do I do this?

---

### Post by blaxbb on 2007-08-23
```
sudo apt-get install ubuntu-desktop
```

---

