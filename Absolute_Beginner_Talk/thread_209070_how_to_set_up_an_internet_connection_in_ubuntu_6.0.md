---
title: "how to set up an internet connection in ubuntu 6.06?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by jclmusic on 2006-07-04
how do u do it?

---

### Post by Kilz on 2006-07-04
[QUOTE=jclmusic]how do u do it?[/QUOTE]
That depends on what kind of connection.

---

### Post by jclmusic on 2006-07-04
direct broadband connection 2 the net via a router using ethernet wires.

---

### Post by MaximB on 2006-07-04
you don't mean adsl or a connection that requiers a passward for the ISP ?
or do you ?

---

### Post by jclmusic on 2006-07-04
nope, no password. on my windows comp, i just plug it in and it works, with no added settings required.

however, as we all know, windows is very insecure (and i think inferior!) so i wanna use linux 4 the net :)

---

### Post by Kilz on 2006-07-04
[QUOTE=jclmusic]direct broadband connection 2 the net via a router using ethernet wires.[/QUOTE]
For the most part they tend to work as long as the [network card is supported.]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards") Are you having problems?

---

### Post by jclmusic on 2006-07-04
[QUOTE=Kilz]For the most part they tend to work as long as the [network card is supported.]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards") Are you having problems?[/QUOTE]

yep, basically no net! i bought this comp second hand very cheap and customised the hardware and built it up myself. however, i've never touched the ethernet card, and i have no idea what make it is. any way 2 find out?

update: it has a compaq label on it! so i basically need a new 1?

---

### Post by Ctrl+Alt+Del on 2006-07-04
type 'lspci' in a terminal and post the output, that's the easiest way to find out wether it should work.

---

### Post by jclmusic on 2006-07-04
that command said it was an 'Intel Ethernet Pro 100'. thanx!

---

### Post by MaximB on 2006-07-04
you can phisiclly open your computer and see the name of the model (it must be written on the network card).

---

### Post by jclmusic on 2006-07-04
ok, after opening up and takin the card out 4 a look, it's an intel.

---

### Post by Kilz on 2006-07-04
[QUOTE=jclmusic]ok, after opening up and takin the card out 4 a look, it's an intel.[/QUOTE]
There is curently a [bug with the Intel pro 100]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/24047") 
But looking back at old posts [someone found a way around it in Breezy]("http://www.ubuntuforums.org/showthread.php?t=30714&highlight=Intel+Ethernet+Pro+100+ubuntu")
The post recommends to pass the noapic option to the kernel. To do this open a terminal and copy and paste this in
```
gksudo gedit /boot/grub/menu.lst
```
The editor will open, this is the grub boot menu, be very careful with what you change because it could make Ubuntu unbootable.
Scroll down the file, look for the first line that says
```
**kernel**		/boot/vmlinuz-2.6.15-23-amd64-generic **root=**/dev/hda3 ro quiet splash
```your may be slightly diffrent as I have a amd64 prossessor. The important things are bolded add noapic to the end so it looks liek this.
```
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hda3 ro quiet splash noapic
``` and click save. Then reboot.

---

### Post by jclmusic on 2006-07-05
i am now typing from ubuntu!!

thank u so much, u rule! :D 

man i owe u people big time! thank u!!!!!!!!!!

---

