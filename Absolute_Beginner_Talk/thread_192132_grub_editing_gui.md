---
title: "grub editing gui"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by mbgb14 on 2006-06-08
What programs exist to edit Grub graphically via Ubuntu? I want to rearrange the order of my OS's on my bootmenu - but don't know howto do it cline.

---

### Post by Jagot on 2006-06-08
GNOME System Tools can do that, amongst other things:

[http://www.gnome.org/projects/gst/index.html](http://www.gnome.org/projects/gst/index.html)

---

### Post by mbgb14 on 2006-06-08
[QUOTE=Jagot]GNOME System Tools can do that, amongst other things:

[http://www.gnome.org/projects/gst/index.html](http://www.gnome.org/projects/gst/index.html)[/QUOTE]
Thanks so much for the swift reply!
I'm not at my machine right now - is that in the repos? What's it under?

---

### Post by mostwanted on 2006-06-08
I'm sure there are perfectly capable GUI tools for GRUB, but really what is the difficulty in rearranging it yourself? Just open the grub file in a text-editor like this:

sudo gedit /boot/grub/menu.lst

And move around the blocks that look like this (most of the GRUB file is made up of comments which can be ignored):

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

If you want to set what entry to load as default you can move the savedefault part to one of the other entries.

---

### Post by mbgb14 on 2006-06-08
[QUOTE=mostwanted]I'm sure there are perfectly capable GUI tools for GRUB, but really what is the difficulty in rearranging it yourself? Just open the grub file in a text-editor like this:

sudo gedit /boot/grub/menu.lst

And move around the blocks that look like this (most of the GRUB file is made up of comments which can be ignored):

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

If you want to set what entry to load as default you can move the savedefault part to one of the other entries.[/QUOTE]
Thanks, I'll try that - just... I'm graphically obsessed ;)

---

### Post by aysiu on 2006-06-08
Before editing any system file, always make a backup copy first: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

---

### Post by mbgb14 on 2006-06-08
[QUOTE=Jagot]GNOME System Tools can do that, amongst other things:

[http://www.gnome.org/projects/gst/index.html](http://www.gnome.org/projects/gst/index.html)[/QUOTE]
Okay, it seems to be installed out of the box in Ubuntu 6.06.
It says in the description it can be used to edit the bootloader. But, I've searched and searched and I find no way to either open gnome-system-tools let alone configure the bootloader :( 

What am I doing wrong?

---

### Post by aysiu on 2006-06-08
[QUOTE=mbgb14]Okay, it seems to be installed out of the box in Ubuntu 6.06.
It says in the description it can be used to edit the bootloader. But, I've searched and searched and I find no way to either open gnome-system-tools let alone configure the bootloader :( 

What am I doing wrong?[/QUOTE] I don't think GST currently supports Ubuntu for bootloader editing.

I used [this](http://www.ubuntuforums.org/showpost.php?p=858906&postcount=13) in Breezy. It might work in Dapper, too.

---

### Post by Jagot on 2006-06-08
OK.  Having had a look around on the forums I found post by Sef which indicates GST has been disabled in Dapper due to bugs.  I'm sure there must be a way of getting it working, possibly downloading from that website and giving it a go but I'm not sure.  There is a newer version available from the site than is in the repos.

Also, not sure where you were looking aysiu because if you see my attachment it says that it supports GRUB, LILO and Yaboot for all distros.

---

### Post by mbgb14 on 2006-06-08
[QUOTE=aysiu]I don't think GST currently supports Ubuntu for bootloader editing.

I used [this](http://www.ubuntuforums.org/showpost.php?p=858906&postcount=13) in Breezy. It might work in Dapper, too.[/QUOTE]
Thanks for that - it ran fine, and opened up and it looks to do exactly what I wanted, although the Save button doesn't work. It pushes in and pops back out, but nothing changes :(

---

### Post by aysiu on 2006-06-08
[QUOTE=Jagot]
Also, not sure where you were looking aysiu becasue if you see my attachment it says that it supports GRUB, LILO and Yaboot for all distros[/QUOTE] Sorry. I guess I must have been looking at services and not boot... that's weird.

[quote=mbgb14]Thanks for that - it ran fine, and opened up and it looks to do exactly what I wanted, although the Save button doesn't work. It pushes in and pops back out, but nothing changes[/quote] Well, it worked in Breezy. Maybe you can send a private message to red_Marvin and see if he'll update it for Dapper.

---

