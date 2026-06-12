---
title: "Help with multiple things..."
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by alienduckie on 2007-11-19
Earlier today I installed Ubuntu 7.10 and i have a few problems...

1- I have Windows Vista Home Premium on an HP Computer, When I start up my computer, it goes directly into Ubuntu. How do I switch between Vista and Ubuntu?

2- On the log-in screen when you start up Ubuntu, it says on my monitor "Input Signal Out Of Range." When I actually get into Ubuntu and start using it, the automatically message goes away. I know there are a million of these topics but none of them solved my problem.

3- How can I view and use my files from Vista (pictures, music etc.) on Ubuntu? I check Computer but when I click on my hard drive, it doesn't have my files. In fact it does't even look like when I view it in Vista.

So if anyone out there could help, it'd be much appreciated. Thanks

---

### Post by Dr Small on 2007-11-19
1.) You will need to press ESC at bootup to access the GRUB menu and select Vista.
2.) I have only heard of this once, and it was because my xorg needed reconfiguring on Gutsy, in order for me to even see the desktop.
3.) You should be able to mount your hard drives in Nautilus and view your pictures & music.

Dr Small

---

### Post by taurus on 2007-11-19
1.  Edit /boot/grub/menu.lst and increase the timeout from whatever the current value to a higher, longer, one.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

2.  Maybe

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

3.  You need to install ntfs-3g and mount your windows partition before you can use it.

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
gksudo ntfs-config
```
and point it to where ntfs partition it.  It will add an entry in /etc/fstab for you so it will be mounted automatically each time you boot.

---

### Post by PeterJS on 2007-11-19
> **alienduckie said:**
> Earlier today I installed Ubuntu 7.10 and i have a few problems...

1- I have Windows Vista Home Premium on an HP Computer, When I start up my computer, it goes directly into Ubuntu. How do I switch between Vista and Ubuntu?

Can you elaborate on directly? As in straight to the ubuntu loading splash? or straight to GRUB which only has options for booting ubuntu?

> 
3- How can I view and use my files from Vista (pictures, music etc.) on Ubuntu? I check Computer but when I click on my hard drive, it doesn't have my files. In fact it does't even look like when I view it in Vista.

So if anyone out there could help, it'd be much appreciated. Thanks

If they aren't installed, install ntfs-g3 and ntfs-config with Synaptic. I use Xubuntu, so I can't tell you exactly where in the menu it will show up in gnome, but under system there should be an entry for the NTFS configuration tool, run that and it will let you set up reading and writing to the vista partition.

---

### Post by Sef on 2007-11-19
> Can you elaborate on directly? As in straight to the ubuntu loading splash? or straight to GRUB which only has options for booting ubuntu?

You should have the option when you first start up as to which operating system you want to use.

---

