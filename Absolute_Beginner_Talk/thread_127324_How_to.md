---
title: "How to"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by benjiej on 2006-02-08
What is the command syntax to pull up fstab and /boot/ ???

---

### Post by eRoot on 2006-02-08
To edit fstab: sudo gedit /etc/fstab
To access the /boot folder: cd /boot

Hope that helps.

---

### Post by Sutekh on 2006-02-08
[QUOTE=benjiej]What is the command syntax to pull up fstab[/QUOTE]

What do want to do with fstab, view it or edit it?

```
cat /etc/fstab
```This will print out the contents of /etc/fstab (or any file) to the command line

```
sudo gedit /etc/fstab
```This will open gedit (a tet editor for GNOME) and open the /etc/fstab file

> 
 and /boot/ ???
What do you need from boot?

/boot/ is a folder, youcould change directory to it, 
```
cd /boot/
```but then what do you need?

---

### Post by benjiej on 2006-02-08
My Grub is not working so I am trying to manually mount it in the /boot. The problem is when I do an Fstab
"root@ubuntu:~# sudo gedit /etc/fstab" I get
"(gedit:25787): Gtk-WARNING **: cannot open display:"
I tried to do an 
"root@ubuntu:~# cat /etc/fstab" and I get
"/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda7 swap swap defaults 0 0"

It appears that I am missing my /root and /home.

The other issue is I need to get my widonws working again at the very least. I am toying with the idea of mounting my Fat 32 partition that windows is on and pull all the files there onto my external HD. If I go that route then I will simply frag this HD and start over fresh.

I have one more question when I do a list of /boot/ I get
"System.map-2.6.12-9-386  config-2.6.12-9-386      memtest86+.bin
abi-2.6.12-9-386         initrd.img-2.6.12-9-386  vmlinuz-2.6.12-9-386"
Is there a way I can edit these and maybe get rid of Grub altogethor to get window to boot back up???

---

### Post by taurus on 2006-02-08
Gedit only works if you are in window...  If you are from a terminal, try pico

sudo pico /etc/fstab

---

### Post by Sutekh on 2006-02-08
[QUOTE=taurus] 	Gedit only works if you are in window... If you are from a terminal, try pico

sudo pico /etc/fstab[/QUOTE]
Good point.

[QUOTE=benjiej]
The other issue is I need to get my widonws working again at the very least. I am toying with the idea of mounting my Fat 32 partition that windows is on and pull all the files there onto my external HD. If I go that route then I will simply frag this HD and start over fresh.[/QUOTE]
Okay, chuck in your Windows install CD, and work your way into the recovery console (**R** at the main screen if memory serves).  When you finally get to a prompt use the command
```
fixmbr
```

[PS if your Windows hard drive is not the boot disc then you will need to specify where fixmbr should work its black magic.  
Use
```
map
```to find the names of your hard drives, and then
```
fixmbr \Device\HardDisk#
```Where # is the number of the hard disc with windows - You probably won't need to do this]


If you can get back into Windows, then let us know and we can work to get you back into Ubuntu.

---

### Post by benjiej on 2006-02-08
Ok I have run my fixmbr and I still get just a blank screen with a cursor. At this point I have worked a week to get Grub to work and it always writes over my MBR even though I put it in my /root. I am at my wits end, the only way I can even get my computer to run now is to load the Live CD. Has anyone else had this issue?

---

