---
title: "Win 2000 Dual Booting"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Akira_Oni on 2006-10-05
Ok, so I actually started using Ubuntu a few months ago out of necessity. I do like it, however it still doesn't meet all of my needs. So I recently got a copy of windows 2000 from a friend, and opened up some space on my drive using the Ubuntu Install disk.

Everything went smoothly. Windows even talked about dual booting during it's installation. SO.... where's my Ubuntu partition? I can see it. It's there. I just can't open/boot it. I'm actually using my Ubuntu install disk to type out this message. I swear I hate windows >_<

---

### Post by NESFreak on 2006-10-05
windows 2000 CAN ONLY r/w FAT?? and NTFS. Linux ntfs write support is very unstable. The best thing you could do is to set up an additional fat partition for file sharing.

NESFreak

---

### Post by think13 on 2006-10-05
I think your problem is the Windows boot loader.  It may not be able to see/boot from the linux partition.  Try restoring GRUB with this how-to:

[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by Akira_Oni on 2006-10-05
> I think your problem is the Windows boot loader. It may not be able to see/boot from the linux partition. Try restoring GRUB with this how-to:

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Tried that, however whenever I attempt to install it tells me there's no root and cycles back to partitioning

---

### Post by Akira_Oni on 2006-10-05
Anyone?

---

### Post by bulldog on 2006-10-05
Try this one,

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

And for your info,install windows first and Ubuntu second next time.:D

---

