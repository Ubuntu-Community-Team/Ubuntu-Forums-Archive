---
title: "Boot menu loader"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by MrTumbles on 2006-09-26
I recently tried to make the move to Ubuntu from Windows XP and I was wondering about how I could edit the grub boot loader. Naturally the first thing that I did was look up the help documentation that came with my Distro. After not finding the bootloader administration tool in the menu, I tried to find it in the 'add/remove' section, and it wasn't there either. Finally, I tried the terminal command 'boot-admin' and yes, the command wasn't found either.

Do I have to download a certain software package? Am I doing something wrong? Is the option hidden elsewhere? Any help in the right direction would be a welcome one.

---

### Post by Average Joe on 2006-09-26
I am not sure if this is what you mean, but you can customize the boot menu yourself. Therefore your have to edit the /boot/grub/menu.lst file (make a backup first!):

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.backup
gksudo gedit /boot/grub/menu.lst
```

Is this file you can change the menu entries, default entry, boot splash image etc.

Hope this helps.

---

### Post by Obor on 2006-09-26
Read [this page on wiki]("https://help.ubuntu.com/community/GrubHowto") - should answer some of your questions

---

### Post by anaconda on 2006-09-26
There is also a graphical tool for editing grub.
I think it's name is: 
grubed
You have to install it with synaptic (or aptitude)
for more info search the forums. 

EDIT: Here is a link:
[http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed](http://www.ubuntuforums.org/showthread.php?t=228104&highlight=grubed)

(Sorry I haven't tried grubEd, so cant help more..)

---

### Post by MrTumbles on 2006-09-29
Hi guys, sorry for the late reply, I've been busy the last few days.

Well I tried that GrubEd program that anaconda suggested and it worked like a charm: Did everything I wanted it to. Thanks for the handy program!

Average Joe: I tried those terminal commands you asked of me. I managed to make that backup of menu.lst just fine, but that second command didn't work for some reason. It gave me and error, which said 'Gtk error **: Cannot open display." Do you know what this could mean?

---

