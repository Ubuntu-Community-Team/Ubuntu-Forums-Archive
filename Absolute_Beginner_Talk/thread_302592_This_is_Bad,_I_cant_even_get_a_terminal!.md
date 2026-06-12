---
title: "This is Bad, I cant even get a terminal!"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by redbluemangle on 2006-11-18
I was trying to mount my windows (fat32) partition to my home folder and make that into my desktop. So using psychocats method I did it but now Everything is all screwy and and [/b]I can't even get a console up.[/b] I can only write this because I had firefox open.

---

### Post by redbluemangle on 2006-11-18
I can't open a terminal! what can I do?

---

### Post by coder_ on 2006-11-18
What does it say when you try to launch the terminal?

---

### Post by redbluemangle on 2006-11-18
let me clarify. 

I mounted /dev/hdd1 to /home because I set nautilus to use /home as the desktop and I wanted my main storage disk to be my desktop. I unwittingly, the "home" folder in Nautilus's  config was actually /home/brian

so I have my desktop set to /home/brian which doesnt exist. Now for some reason none of my launchers are working. I cant launch a console to fix any of this.

---

### Post by redbluemangle on 2006-11-18
well before it would give me a no such directory error but I have since remade /home/brian and now the console looks like it's starting and it just doesnt come up.

---

### Post by redbluemangle on 2006-11-18
ok I need someones help. Since I can't open a console or any programs that arent already open I need someone to edit my fstab for me. I have a copy hosted here [http://www.sendspace.com/file/7a3vee](http://www.sendspace.com/file/7a3vee) and I need hdd1 which is mounted at /home to be changed to /windows . rehost the file on sendspace and I will replace the bad one with the good. Will I be able to overright it by downloading ontop of it? I can't issue any sudo commands :(

OR

could I just boot off the live CD and edit my fstab?

---

### Post by CatKiller on 2006-11-19
> **redbluemangle said:**
> could I just boot off the live CD and edit my fstab?

First off, you should be able to run commands with **Alt-F2**. In particular, you should be able to run **gksudo gnome-terminal**, which **should** get you round the no-home-folder-no-folder-to-start-in problem with the normal terminal. Or, failing that, you can run **sudo umount /home** and **gksudo gedit /etc/fstab**.

If the Alt-F2 trick isn't working, you can restart the computer and press Esc to get into the GRUB menu and choose recovery mode. This should get you running as root directly, so you can edit your fstab with **nano**.

Failing either of these, you can boot off the live cd to fix your fstab. You'll need to mount your hard drive first. I'll assume that your Linux / partition is hda1. If it isn't, change that to whatever it should be.

```
sudo -s
mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
nano /mnt/linux/etc/fstab
shutdown -r now
```

---

