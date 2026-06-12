---
title: "Completely new to ubuntu, need help booting disks."
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2006-10-23
Ok well first off im new too all of this and theres alot of things i dont know so first off, what is a dual boot? how do you do it? and idk if thats right for me cause this is my setup, i have my primary hd a windows xp harddrive, and then i got ubuntu installed on the second harddrive (slave) and i would like to switch back and forth in a bootsequence as i please, so how do i set that up, for now what i gotta do is hit DEL to enter my bios and change harddrive boot up order, which is a huge pain, also, after i reconnected my windows xp harddrive and i tried to switch back to my ubuntu, it said the root file system is corrupt or something and linux wont load, then i unplugged the windows harddrive and it worked just fine. how is that and is there a way to set it up where it will and where i dont have to enter the bios every time to choose which harddisk i want to boot from.

---

### Post by Bachstelze on 2006-10-23
Hi and welcome to Ubuntu :)

All you have to do is to edit GRUB configuration file so it allows you to boot Windows as well. Please paste the contents of the file /boot/grub/menu.lst as well as the output of

```
sudo fdisk -l
```

---

### Post by bullgr on 2006-10-23
let's start from the beginging...

you have one hard disk witch is windows installed.

boot from the ubuntu cd and install ubuntu. in the question where
to write the grub bootloader (grub is the linux bootloader for
dual booting) choose to write grub to MBR (master boot record, this is windows bootloader).

that's it. after that when you boot your pc you have the choice to boot in ubuntu or in windows.

if you like to chance some grub settings (highlighted option wait time etc), edit as root the file /boot/grub/menu.lst next time you boot in ubuntu

> sudo gedit /boot/grub/menu.lst

hope i help...
if you like more detailed help or guide, there is many-many articles for that, little googling will be ok.

---

### Post by Irony on 2006-10-23
Install GRUB (Grand Unified Boot Loader) to your MBR (master boot record, the first sector of your master drive) and point it to your slave drive (hdb2 or hdb1 wherever root is?).

GRUB will be in your Ubuntu install disc - go through the install process but skip the installing until it gets to GRUB.

You may then have to manually configure your menu.lst to dual boot XP (or it maybe automatic).

See for more details;

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Bachstelze on 2006-10-23
He already has Ubuntu installed. I don't think it's worth reinstalling just to fix a little GRUB setting...

---

### Post by Irony on 2006-10-23
No, just install grub, in Hoary you just type rescue at the boot prompt;

[PHP]Boot from the install ubuntu CD and at the prompt typed;
boot: rescue
Go to a  mount points, hda5 would be;
dev/disc/disc0/part5
At the sh-3.00# prompt type;
grub-install /dev/hda
After being returned to the prompt, do;
#umount /dev/hda5
#reboot[/PHP]

---

### Post by Bachstelze on 2006-10-23
No need to even reinstall GRUB I think. He seems to have GRUB installed on the MBR of drive 2 and Windows on drive 1. So all he has to do is to add an entry on his menu.lst to chainload his Windows.

---

### Post by apoch on 2006-10-23
The simplest thing for you to do is make the linux drive your primary and the windows drive the slave.

Then edit /boot/grub/menu.lst and add

title Windows XP
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
root (hd1,0)
makeactive
chainloader +1

---

### Post by TheNemeses on 2006-10-23
ok i got a guide and i know how i want to set it up, but in the terminal whenever i try to type
sudo gedit menu.lst
it says display error (null) what does that mean and how do i fix that

---

### Post by TheNemeses on 2006-10-23
lol oh nvm, im such a newb i would always go into the command prompt screen CTRL ALT f1, then i figured out the application terminal that looks like notepad, well i got it work!!! thanks guys theres still alot more questions and problems i am having but i will make those in a new thread.

---

