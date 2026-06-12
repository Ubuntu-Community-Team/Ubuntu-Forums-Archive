---
title: "How do I make this happen everytime I boot?"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by shane.reid on 2006-04-03
to get wifi working, when I boot I need to...

sudo rmmod bcm43xx
sudo ndiswrapper
sudo ifup eth0

seperately, i need to 
sudo mount /dev/hda4 /home/reid/.cedega

---

### Post by LordBug on 2006-04-03
The first 3 commands you could make an init script for.

The mount command is unneccesary.  Just a line into /etc/fstab and it'll mount on every boot.

---

### Post by Cephyr on 2006-04-03
Hmm, that's a strange sort of commands. I never had to do that with my ndiswrapped wifi card. Oh well, here's what you do.

Open up gedit and write those three commands in, each on a seperate line. Save it as "wireless" in an easy to remember spot, like your home directory.

Now head on over to the terminal and type in:

```
sudo gedit /boot/grub/menu.lst
```

Now, look around in that file until you find your default entry, the one you always boot to (mine is "Ubuntu, kernel 2.6.12-10-386"). On the line labeled "kernel", add to the end:

```
init=/home/user/wireless
```

Where "user" is your username.

---

