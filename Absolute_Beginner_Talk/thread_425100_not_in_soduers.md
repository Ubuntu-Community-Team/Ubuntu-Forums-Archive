---
title: "not in soduers?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Anti-thesisofreason on 2007-04-27
I have recently loaded the bare minimum for Xubuntu I have a cli prompt and thats about it, which is what I expected. I have a machine that I can only load in low memory mode so I went with the bare minimum.

I have a few questions.

1. how do I dismount/shutdown without running into troubles later when I boot again?

2. why do I get a "you are not in the sudoers file" when I try to use the sudo command?

also I am trying to edit the sources.list but when ever I try nothing happens. I use "sudo nano /etc/apt/sources.list"
I get prompted for a password, which I put in and then nothing happens. I have tried using "editor" in place of "nano" but still nothing.

3. how do I mount a drive like a cd rom?

I am very new to this I have used cli in windows before but the command structure is obviously different in Unbuntu so it will take me some time to learn.

Thanks ahead of time!

Jay

---

### Post by Seisen on 2007-04-27
How did you install the bare minimum for Xubuntu?

---

### Post by Zuuswa on 2007-04-27
to shutdown your computer from the command prompt, try this:
```
sudo shutdown now
```
if you want to restart instead of shutdown, try
```
sudo shutdown -r now
```
I dont think nano comes with xubuntu, though I am not sure.  Try vim or pico instead.
If you arent in the sudoers file, then you might have some problems.  You will need to make sure that you are in the admin group, you can do this from comand line like this:
```
sudo addgroup *username*  admin
```
then, you take a peek into your sudoers file
```
sudo vim /etc/sudoers
```
and make sure that you have this line all the way at the bottom:
> %admin ALL=(ALL) ALL


although, if you cant sudo now, you may have to boot into a recovory mode in order to do those.  If that is the case, then just drop the sudo in front of the commands, as you will already be running as root.

As for mounting a drive as a cd-rom, im not too sure exactly what you are asking.  Do you want to mount a cd-rom, or do you want to mount a partition/drive?

. . : : edit : : . .
I think I just had a lil brain fart when I read your last line.  Anyway, to mount/unmount devices, drives, partitions, etc. :
```
sudo mount *path to device/drive/partition*
sudo umount *path to device/drive/partition*
```

you may want to refer to your fstab as to what your partitions/drives are called, it can be found here:
> /etc/fstab

---

### Post by Anti-thesisofreason on 2007-04-27
> **Seisen said:**
> How did you install the bare minimum for Xubuntu?

when I booted to the install disk I chose to intall a server. I found these directions helped me that far. [https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

