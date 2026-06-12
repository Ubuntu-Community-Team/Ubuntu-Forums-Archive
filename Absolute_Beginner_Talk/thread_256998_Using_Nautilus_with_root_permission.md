---
title: "Using Nautilus with root permission"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by bryan4134 on 2006-09-13
Simple question I think.  I want to copy files to /usr/share/themes using Nautilus rather than terminal - I am unable to as this requires root user permissions.  Is there a way to do this or can it only be done in the terminal mode?

---

### Post by catlett on 2006-09-13
Open a terminal and enter ```
gksudo nautilus
```This will open nautilus as root. Then you can do 2 things.
1. You can drag and drop files that belong to root. You may have to open another terminal and enter gksudo nautilus again to get 2 root nautilus going. That way you can open 1` to one folder and the other to another folder and then drag and drop files from one to the other.
2. You can now go to any folder and change it's permissions so you can open it's files or drag and drop it's contents when you are a user. Just right click on the folder to bring up the options menu. Then select the 'permissions' tab. You can then check of the tabs for 'others' or 'group'. If you are the only one using your computer and you want full access, you can check them all off. If you don't want other people to have access, be selective. Also don't change the permisions on system files like root and usr. They need to be root.

---

### Post by xyz on 2006-09-13
I like that one,too from the Dapper Guide:
```
gksudo gedit /usr/share/applications/Nautilus-root.desktop
```
Insert those lines into the file:
> [Desktop Entry]
Name=File Browser (Root)
Comment=Browse the filesystem with the file manager
Exec=gksudo "nautilus --browser %U"
Icon=file-manager
Terminal=false
Type=Application
Categories=Application;System;

Of course, save the file and go to: Applications -> System Tools -> File Browser (Root)

I can't get my hands on them right now but some member(s?) wrote some nice right-click-on-the-file scripts and "open as root", "gedit as root","root-nautilus-here".
I'll try to locate them on the site when I have more time.

---

### Post by xyz on 2006-09-13
Found one:
>  how to open files as root user via right click
Insert the following lines into the new file
> for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksudo "gnome-open $uri" &
done
Save the file and make it executable:
```
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```
Right click on file -> Scripts -> Open as root
Might come in handy,too!
Dapper Guide.

---

### Post by caimex on 2006-09-14
> **xyz said:**
> 

I can't get my hands on them right now but some member(s?) wrote some nice right-click-on-the-file scripts and "open as root", "gedit as root","root-nautilus-here".
I'll try to locate them on the site when I have more time.

I have those nautilus scripts installed. You can get them easily with automatix, one of the items in the list is "nautilus scripts" or something similar.

---

