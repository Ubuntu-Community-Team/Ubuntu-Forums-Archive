---
title: "Need help with samba please"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Gizmo89 on 2006-11-12
hi, i'm trying to play music over a network using samba , which i read about, and this is going to sound really noobie, but how on earth do you open the blasted program? :s

Note. i have successfully installed ubuntu for the very first time, but am thinking of overwriting it with Kubuntu, know if kubuntu is any good?

---

### Post by EvanPMeth on 2006-11-12
Samba starts up automatically on start up. Your problem is that you probably do not have anything set up. Such as a shared folder or users to access that folder. The first step i would take is to check out this site. And follow the " How to share home folders with read/write permissions (Authentication=Yes)" then " How to add/edit/delete network users"

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Samba_Server)

and create a new group just for accessing that computer called "music". 
```
sudo gedit /etc/group
```
add at the end:
```
music:x:99:MUSICUSERNAME,NORMALUSERNAME
```
replace 99 with a number that is not currently present and of course replace MUSICUSERNAME,NORMALUSERNAME with the proper usernames.

Set the proper access to the folder you are sharing /home/group/

hope that helps.
-evan

---

### Post by kylevan on 2006-11-12
SAMBA is the program that enables Linux to read windows shares over the SMB protocol.  Anyway, you should be able to click on the "Places" menu, click on "Network Servers" and you should see your windows workgroup. (If it doesn't work right, try clicking the refresh/reload button in the toolbar.)  A media player like Totem or XMMS will open the actual media file.

as far as kubuntu is concerned, it's the exact same as Ubuntu, but uses the KDE interface as opposed to GNOME, and all the KDE/Qt based programs.

I *think* you can just install the kubuntu-desktop metapackage in synaptic as opposed to doing a completely new installation.

---

