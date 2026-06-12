---
title: "How do I follow these kernal steps? Please help!"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by FawnX on 2007-07-25
Hi. I recently installed Ubuntu on my PS3, and have been having a slight problem with WiFi. This is apparently a known issue, and I found a solution here > [http://psubuntu.com/forum/viewtopic.php?t=449](http://psubuntu.com/forum/viewtopic.php?t=449)

It's a replacement kernal that'll add WiFi support for the PS3. However, I have no idea how to install it, despite the fact that he lists steps.

[SIZE="1"][I]Usage Instructions:

1. Download the .deb to a known directory.
2. #>sudo dpkg -i linux-image-2.6.22-rc2_2.6.22-rc2-10.00.Custom_powerpc.deb
3. #>cd /boot
#>ls -al
Look in your /boot/ directory. You should have a symlink to the new kernel named vmlinux and an initrd ramdisk named initrd.img . Your old kernel should be at vmlinux.old and initrd.img.old .
4. #>sudo nano /etc/kboot.conf [/I][/SIZE]

What the heck does that mean? I'm a Linux noob, and I've never done any scripting or commands. Ubuntu was very easy to install and didn't require any of this. Where do I type in all these commands? Why can't I replace the kernal by simpler means?

This all seems very confusing... Can anyone help please?

---

### Post by Seisen on 2007-07-25
Put this in the terminal after you download the .deb file 

```
sudo dpkg -i linux-image-2.6.22-rc2_2.6.22-rc2-10.00.Custom_powerpc.deb
3. #>cd /boot
```

then after that installs put this in the terminal

```
cd /boot
``` then this

```
ls -al
``` make sure that symbolic link is their and then put this in the terminal

```
sudo nano /etc/kboot.conf 
```

---

### Post by Cypher on 2007-07-25
What happens when Ubuntu boots up on the PS3? Do you get a desktop? Is it Gnome? If so, you will have to open up terminal by going to Application->Accessories->Terminal.

---

### Post by FawnX on 2007-07-25
Thanks for the help, Seisen.

> **Cypher said:**
> What happens when Ubuntu boots up on the PS3? Do you get a desktop? Is it Gnome? If so, you will have to open up terminal by going to Application->Accessories->Terminal.

Yes, it does boot to the desktop. Thanks for the advice.

---

### Post by Seisen on 2007-07-25
It it boots into gnome I would use gedit instead of nano then. So change that last command to this

```
gksudo gedit /etc/kboot.conf
```

---

