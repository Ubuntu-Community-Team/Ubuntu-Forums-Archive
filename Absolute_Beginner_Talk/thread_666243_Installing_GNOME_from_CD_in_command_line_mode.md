---
title: "Installing GNOME from CD in command line mode"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Dmitri.Tikhonov on 2008-01-13
I have been using Ubuntu 7.10 for about a month (so I know very little) and lately installed KDE 3.5 to try it. At this stage my sound card became unrecognizable and I decided to remove KDE using Synaptic . Somehow I removed the network support, GNOME and Nautilus together with KDE... Now my Ubuntu boots and I can only use the command line interface. Is there any way i could install GNOME and Network using the CD from the command line without reinstalling the entire system?
Many many thanks,
Dmitri

---

### Post by dustman on 2008-01-13
[http://ubuntuforums.org/archive/index.php/t-55715.html](http://ubuntuforums.org/archive/index.php/t-55715.html) this might help ;)

---

### Post by Xavieran on 2008-01-13
you can do ```
sudo apt-get install ubuntu-desktop
```

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main restricted

```

This is the CDROM info in my /etc/apt/sources.list ...you could add that to your /etc/apt/sources.list (nano /etc/apt/sources.list and then do a > sudo apt-get update && sudo apt-get install ubuntu-desktop

---

### Post by Dmitri.Tikhonov on 2008-01-13
Sadly, I do not network support and therefore the command install ubuntu-desktop fails because it is unable to fetch data from the web. is there anything i can try to get back the web access and then install desktop. 
Many thanks again,
Dmitri

---

### Post by dustman on 2008-01-13
> **Dmitri.Tikhonov said:**
> Sadly, I do not network support and therefore the command install ubuntu-desktop fails because it is unable to fetch data from the web. is there anything i can try to get back the web access and then install desktop. 
Many thanks again,
Dmitri

what Xavieran suggested does not need network support ;) . All you need is the Ubuntu CD, and that's it.
First : 
```
sudo gedit /etc/apt/sources.list
```

add the following at the end of the file:
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071015)]/ gutsy main restricted
```
save and exit.

Then: ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

Just like Xavieran posted.

---

### Post by capink on 2008-01-13
Another solution (will only work if you have internet access form live cd):

1. Start your computer using live cd
2. Go to the terminal and type:

```
mkdir rootfs
```

3. Mount your root partition on rootfs:

```
sudo mount -t ext3 /dev/sdXY ./rootfs
```

Replace sdXY with proper value (e.g. sda1)

4. Copy the file /etc/resolve.conf to your root partition

```
sudo cp -av /etc/resolv.conf ./rootfs/etc
```

4. Chroot onto your installation by typing:

```
sudo chroot ./rootfs
```


6. Install any packages you want while in chroot:

```
apt-get update
```

```
apt-get install ubuntu-desktop
```


7. Exit chroot

```
exit
```

8. Reboot.

---

### Post by Dmitri.Tikhonov on 2008-01-13
Thank you very very much! My GNOME is back!

---

### Post by Dmitri.Tikhonov on 2008-01-13
Many thanks to dustman, Xavieran and capink!!!

---

### Post by dustman on 2008-01-13
you're welcome ;) . keep up the good work!


Cheers!

---

