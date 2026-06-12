---
title: "Accessing Windows shared fodlers on Xubuntu"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by dmeehan on 2006-08-28
I have recently added an xubuntu box to my home netowrk. Following excellent instructions received from this forum I managed to access the xubuntu box on the windows pcs.

How can I access the Windows shared fodlers on the xubuntu box?
And also, is there a way of "mapping" (like in windows) the shared folders, so I dont have to re-conenct everytime i logon?

:confused:

---

### Post by &#12465;&#12452;&#12488; on 2006-08-28
I'm not sure about Xubuntu, but you can probably point your file browser to a location like smb://ip. I don't know if there's a "Network Servers" choice like GNOME's Nautilus has.

To mount shares automatically on boot, you can add them to /etc/fstab. Take a look here: [http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

