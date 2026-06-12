---
title: "Can't boot after enabling nvidia! Please help..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by P86 on 2007-05-15
I installed the Nvidia driver and enabled it using konsole, and now I can't boot :(

I was told a backup of my xorg.conf was created, but I'm not sure where is the default backup location is, or what the command line is to recover it!

Please help!!!

---

### Post by reidms on 2007-05-15
If you can access a command line, all ya needa do is reconfigure X

I think you can on Ubuntu by running
```

X -configure
```
as root

---

### Post by P86 on 2007-05-15
I don't make it to the GUI. I'm at the command prompt in recovery mode.

---

### Post by krisfrajer on 2007-05-15
go to /etc/X11/ and then type:

grep -i sudo xorg.conf 

This will return a line: Type that line in your prompt command follow the steps choosing the video card and that should reconfigure your xorg.file to something darn close to the original version installed by ubuntu.

Let me know if it works.

---

### Post by krisfrajer on 2007-05-15
type this to recover your file:
sudo dpkg-reconfigure -phigh xserver-xorg

as I mention in my last post, the recovery program will ask you to choose your grapics card from a list. Dont be afraid of choosing the correct one ;)

---

### Post by reidms on 2007-05-15
> **P86 said:**
> I don't make it to the GUI. I'm at the command prompt in recovery mode.

You dont have to- just run the command I gave from the command line in recovery mode.

---

### Post by P86 on 2007-05-17
> **reidms said:**
> You dont have to- just run the command I gave from the command line in recovery mode.

I ran the command, rebooted, and was still just left at a black screen with a blinking cursor.

---

### Post by P86 on 2007-05-17
> **krisfrajer said:**
> type this to recover your file:
sudo dpkg-reconfigure -phigh xserver-xorg

as I mention in my last post, the recovery program will ask you to choose your grapics card from a list. Dont be afraid of choosing the correct one ;)

Thank you so much for your help! I picked "nv" out of the list, rebooted, and was able to get back in Kubuntu. I logged into the Gnome (which I installed seperately) desktop, and enabled my Nvidia card through the "Restricted Drivers Manager". Now I'm pretty sure I have 3d enabled.

---

