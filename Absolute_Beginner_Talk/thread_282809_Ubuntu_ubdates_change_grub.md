---
title: "Ubuntu ubdates change grub"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by shickidyshade on 2006-10-23
Every time i update ubuntu it changes my menu list when i boot my computer ](*,) is their a way to delete old versions of ubuntu are displayed in the grub menu.
Thanks
Shade

---

### Post by Aberrix on 2006-10-23
the menu is contained in

```
/boot/grub/menu.lst
```

I'd suggest making a backup of it if you're going to edit it.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.backup
```

then just edit it and comment out the lines you don't want using '#'

```
sudo vi /boot/grub/menu.lst
```

---

### Post by Tomosaur on 2006-10-23
Yes, you can uninstall/delete the old versions, but most people will reccommend you keep at least one old version in case the current version goes wrong on you.

To DELETE THE OLD VERSIONS:
Open up a command line (terminal) and type
```

cd /boot
ls vm*

```
This should show you all of your bootable versions. You can delete the ones you don't want by typing:
```

sudo rm <filename>

```

HOWEVER. As stated above, it's probably a better idea to keep an old version or two, just in case. If you wish to do so, you can simply tell Grub to ignore older versions. You need type:
```

gksudo gedit /boot/grub/menu.lst

```
Find the line which says:
```

#howmany all

```
and change the word 'all' to a number. I use '2'. This is the number of different versions grub will show.

Once you're done, save the file, exit gedit, then type 'sudo update-grub' into the command line. Next time you restart, grub should only be showing however many versions you asked it to.

Alternatively, take a look at the link in my sig, which will allow you to change a number of Grub settings, including the number of kernels shown.

---

### Post by steve.horsley on 2006-10-23
It's much easier to delete the old kernels with Synaptic - search for "linux". I advise keeping the previous kernel for at least a week or two, just in case the new one turns out to have a nasty problem.

---

### Post by CatKiller on 2006-10-23
^^ What Steve said. Keep your package management as sane as possible, and uninstall the package rather than deleting the files. Using Synaptic will automatically update your menu.lst.

---

### Post by shickidyshade on 2006-10-23
you can use synatptic to delete old kernels any suggestions how to do that

---

### Post by CatKiller on 2006-10-23
> **shickidyshade said:**
> you can use synatptic to delete old kernels any suggestions how to do that

Open Synaptic (System -> Administration -> Synaptic Package Manager)
Find the kernel that you don't want any more (like linux-image-2.6.15-23-386, for example)
Click on the little box next to it and select "Mark for Removal"
Click on Apply, at the top.
Read what the box says, and if that's what you want to do, click on OK.

---

