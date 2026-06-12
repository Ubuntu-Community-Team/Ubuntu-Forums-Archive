---
title: "Untinstalling VMWare"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-07-16
I was following [this tutorial]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=emulation") when I tried to install, I got this error:

> :/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

I go to synaptic, and VMware is unchecked. I completely uninstalled it under synaptic earlier but my machine still claims it's there. Does anyone know a more in depth way to check if it's installed or force it's removal?

I'm kirking/noobing out over here, but frustrated 'cuz i'm baby steps away from having a perfect system.

---

### Post by someusernoob on 2006-07-16
Did you first install vmware-player with Synaptic?

Typ in a terminal: 
```

whereis vmware 

(or vmware-player)

```
What does it say?

You can also try:
```

sudo updatedb

locate vmware

```

---

### Post by Emceay on 2006-07-16
Yeah, I used synaptic to install, but I kept getting a different error every time I tried to install any other programs, so i removed it.

This is what I got:
> t:/tmp/vmware-server-distrib$ whereis vmware
vmware: /etc/vmware /usr/share/man/man4/vmware.4.gz


locate:
> :/tmp/vmware-server-distrib$ locate vmware
/var/cache/apt/archives/vmware-player-kernel-modules-2.6.15-25_2.6.15.10-7_i386.deb
/var/cache/apt/archives/vmware-player-kernel-modules_2.6.15.10-7_all.deb
/var/cache/apt/archives/vmware-player_1.0.1-4_i386.deb
/var/lib/dpkg/info/xserver-xorg-driver-vmware.list
/var/lib/dpkg/info/xserver-xorg-driver-vmware.md5sums
/etc/vmware
/etc/vmware/locations
/home/mark/.vmware
/home/mark/.vmware/preferences
/home/mark/vmware
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/share/app-install/desktop/vmware-player.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/doc/xserver-xorg-driver-vmware
/usr/share/doc/xserver-xorg-driver-vmware/changelog.Debian.gz
/usr/share/doc/xserver-xorg-driver-vmware/copyright
/usr/share/man/man4/vmware.4.gz


Do I just delete these folders or what?

---

### Post by someusernoob on 2006-07-16
Whats in the /etc/vmware dir?
```

ls /etc/vmware/

```

(Its a lower case "L")

---

### Post by Emceay on 2006-07-16
Returned this:
> $ ls /etc/vmware/
locations


---

### Post by someusernoob on 2006-07-16
Hmmm

```

ls /etc/vmware/locations/

```

And youre sure you completly removed:

vmware-player-kernel-modules-2.6.15-25_2.6.15.10-7_i386
vmware-player-kernel-modules_2.6.15.10-7_all
vmware-player_1.0.1-4_i386

with Synaptic? 

You can delete the vmware folders in you home dir (dont forget the hidden one)

Other then the /etc/vmware folder there is nothing left on your computer. (and this one probably, but should not be the problemmaker: /usr/share/man/man4/vmware.4.gz)

Did you restart your computer? (;) )

---

### Post by Emceay on 2006-07-16
> **someusernoob said:**
> Hmmm

```

ls /etc/vmware/locations/

```

And youre sure you completly removed:

vmware-player-kernel-modules-2.6.15-25_2.6.15.10-7_i386
vmware-player-kernel-modules_2.6.15.10-7_all
vmware-player_1.0.1-4_i386

with Synaptic? 

When I enter Synaptic, those packages are unchecked, perhaps I didn't do a complete removal. Can I delete those files listed in the var folder?

> 
Did you restart your computer? (;) )

Now that you mention it, probably not. I just did before writing this, when I located vmware all of the folders were still in place.

---

### Post by Emceay on 2006-07-16
Tried again, Still getting this:

> b$ sudo ./vmware-install.pl
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.



locate vmware:
> $ locate vmware
/var/cache/apt/archives/vmware-player-kernel-modules-2.6.15-25_2.6.15.10-7_i386.deb
/var/cache/apt/archives/vmware-player-kernel-modules_2.6.15.10-7_all.deb
/var/cache/apt/archives/vmware-player_1.0.1-4_i386.deb
/var/lib/dpkg/info/xserver-xorg-driver-vmware.list
/var/lib/dpkg/info/xserver-xorg-driver-vmware.md5sums
/etc/vmware
/etc/vmware/locations
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/share/app-install/desktop/vmware-player.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_vmware-player.png
/usr/share/doc/xserver-xorg-driver-vmware
/usr/share/doc/xserver-xorg-driver-vmware/changelog.Debian.gz
/usr/share/doc/xserver-xorg-driver-vmware/copyright
/usr/share/man/man4/vmware.4.gz

---

### Post by someusernoob on 2006-07-16
```

sudo rm -r /etc/vmware
sudo apt-get clean
sudo apt-get autoclean

```

rm = remove
apt-get clean & autoclean will clean up all the packages in the /var/cache/apt/archives/ folder.

The other folders and files related to vmware are supposed to be there with the standard installation of Ubuntu, so i'd say dont delete those. (They belong to xserver-xorg-driver-vmware)

If you right click those packages in Synaptic, can you choose "Mark for Complete Removal"?

---

### Post by Emceay on 2006-07-16
> If you right click those packages in Synaptic, can you choose "Mark for Complete Removal"?

Yes, I could've sworn I did for vmware. I guess not, since autoclean worked.
The installer is all set now. Very informative. Thank you for walking me through that. :D

---

