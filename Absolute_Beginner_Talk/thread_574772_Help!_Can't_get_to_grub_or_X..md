---
title: "Help! Can't get to grub or X."
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by skiwithpete on 2007-10-13
Hi,

I tried to upgrade from 7.04 to 7.10 through automatic updates, and I can't get into X anymore.

Not only that, but Grub has lost the line to boot into windows.

So now I have a computer that can only boot into "recovery mode" which is the prompt.  I can't startx because the comp crashes.

O yeah, and I'm in Canada and my Ubuntu CD is in London.

What I really need to do is figure out how to edit /boot/grub/menu.lst from the prompt, and get it so I can boot into Windows, from there I'll burn a new Ubuntu live disk.

Please let me know how to do this.  I'm a noob so any lines that I need to type in whould be a great help! 

Thanks for your help,
p

---

### Post by Martje_001 on 2007-10-13
For the X problem:
```
sudo dpkg-reconfigure xserver-xorg
```

For grub:
Try to change the partition-number. It can help, like it did me!

---

### Post by Pumalite on 2007-10-13
You can retore XP's MBR. Boot from XP CD, hit 'r' for Recovery>FIXMBR>FIXBOOT.

---

### Post by PmDematagoda on 2007-10-13
Shouldn't you be able to use Supergrub for the reinstallation of Grub?

---

### Post by Pumalite on 2007-10-13
In fact you could use Super Grub to boot either OS, or fix the MBR or reinstall Grub

---

### Post by PmDematagoda on 2007-10-13
So wouldn't Supergrub be a much better alternative for repairing Grub than Windows own fix MBR option since Windows will not see Ubuntu or any Linux distro for that matter?

---

### Post by skiwithpete on 2007-10-13
Thanks so far,

all I want to do is edit menu.lst to put back in the reference to Windows (hda0,2) and keep using grub.  I just don't know how to do that without being in Gnome.

From the line command end of it, I want to configure Grub.

Thanks for the X config I will try that soon.

---

### Post by Pumalite on 2007-10-13
To edit menu.lst you need a Live CD or Knoppix. I prefer Knoppix.
If you can get a command line in your actual installation:
gksudo gedit /boot/grub/menu.lst

---

### Post by meierfra on 2007-10-13
> all  I really need to do is figure out how to edit /boot/grub/menu.lst from the prompt, 
```

 nano  /boot/grub/menu.lst
```

---

### Post by skiwithpete on 2007-10-14
Thanks nano was exactly what I was looking for.

Hopefully now, I can repair X

Cheers,

P

---

