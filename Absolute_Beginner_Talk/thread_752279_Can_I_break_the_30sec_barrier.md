---
title: "Can I break the 30sec barrier ?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by SnakeHips on 2008-04-11
I got curious after reading this thread about boot loading times.
[http://ubuntuforums.org/showpost.php?p=3590794&postcount=5](http://ubuntuforums.org/showpost.php?p=3590794&postcount=5)
...and used this *tweak* to see what effect it would have ,though i needed 
some reference to measure against so i installed "bootchart"

```
sudo apt-get install bootchart
```

The first measure (Bootchart_before) shows 34secs and after (Bootchart_after) 32secs!

So I gained a 2sec increase and it got me wondering if i could break the 30sec barrier...

....any ideas ?

/boot/grub/menu.lst

...

default 0
timeout 3
hiddenmenu

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=eac0a3d4-07ff-4793-bbd0-615e095a92b0 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=eac0a3d4-07ff-4793-bbd0-615e095a92b0 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=eac0a3d4-07ff-4793-bbd0-615e095a92b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=eac0a3d4-07ff-4793-bbd0-615e095a92b0 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by jakupl on 2008-04-11
well it must be possible, cus I'm at 27 sec.

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/gutsy-20080411-1.png[/IMG]

---

### Post by jakupl on 2008-04-11
If you don't use bluetooth for anything, you could turn it off?? maybe. Mine is off

---

### Post by jakupl on 2008-04-11
actually my bootchart says 25 sec when I unplug my flashpen and printer,

---

### Post by SnakeHips on 2008-04-11
> **jakupl said:**
> If you don't use bluetooth for anything, you could turn it off?? maybe. Mine is off

I went here - system/preferences/sessions and disabled bluetooth manager.........bootchart still shows "bluetoothd-serv" in its output. How do I switch it off ?

p.s. 25secs - cool.

---

### Post by jakupl on 2008-04-12
try installing sysv-rc-conf. to adjust the boot proces

```
sudo apt-get update
sudo apt-get install sysv-rc-conf
```

then type:
```
sudo sysv-rc-conf
```
to start the program.

---

### Post by SnakeHips on 2008-04-13
Thanks for the tip ,I've looked at it and trying to learn more. I found this helpful
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

I found this entry and as i'm not using a laptop i switched it off..
30. laptop-mode - A service to tweak the battery utilization when using laptops. You can leave it on. The default is 2,3,4,5 

Cant say i'm noticing any boot improvements yet but as i learn more i may eventually shave a few more seconds off :-)  currently still avg 32secs

---

### Post by insane_alien on 2008-04-13
last time i booted my torrentbox it took 10 seconds to boot.

it runs arch with barely anything at all on it. it has just enough to download nad seed torrents and allow ssh access.

---

### Post by jgrabham on 2008-04-13
You could install CF cards into an IDE slot and boot off them - It'll make it lightning fast!!

---

### Post by jakupl on 2008-04-13
> **jgrabham said:**
> You could install CF cards into an IDE slot and boot off them - It'll make it lightning fast!!

sorry but I don't actually understand that... what does it mean in english? :)

---

