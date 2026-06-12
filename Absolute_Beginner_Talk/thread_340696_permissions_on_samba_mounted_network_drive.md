---
title: "permissions on samba mounted network drive"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-01-17
I have a Buffalo LinkStation Pro network drive mounted as /media/share with samba on an edgy system and I'm having some issues with permissions.  

Owner and group are both set to root, with read write and execute access granted to owner and group and other having only read and execute permissions.  I can write to it, create directories, move files, and so on if I do it through the terminal with sudo, but running *sudo chmod 777 /media/share* gives me a message that I dont have permission to do that.  Does anyone have an idea what would cause that and how to change it?

Also, can you tell me what I need to do to have it remounted automatically at login?

---

### Post by kebes on 2007-01-17
You can fix both problems at once (permission and automount), by following the instructions in this guide:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)


That will set the samba share to mount during boot, and the modifications made to "/etc/fstab" will make it so that all users have read-write permission to the mountpoint.

Hope that helps...

---

### Post by Lucardo Mamones on 2007-01-17
Just to make sure i understand correctly. you are connecting via Samba to a network drive mounted on /media/share

what command did you use to mount this drive? 

to have it mount at boot you will need to add a line into /etc/fstab see:

[http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab](http://kim.biyn.com/Linux/how_to_mount_samba_windows_shares_at_boot_time_via_fstab)

---

### Post by Ba66e77 on 2007-01-21
Thanks, kebes.  That worked like a charm

---

### Post by borris.morris on 2007-02-03
Sorry to Hi-Jack, but what about if I don't want it to automatically be mounted at boot? I have a wireless network and I'm only on it sometimes.

---

### Post by kebes on 2007-02-03
> **borris.morris said:**
> what about if I don't want it to automatically be mounted at boot? I have a wireless network and I'm only on it sometimes.

If you want to do it on the commandline, here's how you do a one-time mount:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite)

You can also create a little script to do this, of course. (Which will then be clickable, etc.) I believe you can also add network locations to Nautilus, and mount them on demand.

---

### Post by borris.morris on 2007-02-06
I figured it out using "sudo smbmount //confettiserver/"share drive" /home/jessie/xdrive/ -o rw,fmask=777,dmask=777"  It works perfect. And yes, I did make a script. It mounts three things if I am connected to this network, otherwise, nothing. Pretty sweet.

---

