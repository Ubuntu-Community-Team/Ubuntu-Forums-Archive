---
title: "Dim screen, Brightness controls won't work."
date: 2010-03-30
forum: Apple Hardware Users
---

### Post by joypunk on 2010-03-30
I successfully installed Ubuntu on my Macbook Pro (5,4 model) and have been running it just fine for about a week. I am triple-booting my Macbook (Windows 7, OSX Snow Leopard, and Ubuntu 10.04). Yesterday when I booted into Ubuntu, the screen was very dim, I would say about 5% brightness, if even that. You can see things on the screen, but it is very, very difficult.

The last thing I remember doing in Ubuntu was attempting to install dotnet20 from winetricks. The install failed, but everything appeared to still be working correctly. At the end of the night I rebooted into Windows 7 (my primary OS). The next time I booted into Ubuntu it had the dim screen issue. Every time I boot into Ubuntu the screen stays this way.

Using the Fn+F2 (or just F2... I've tried both) to increase the brightness makes no changes. The only solution I've seen to a similar issue after some searching was to go into the System menu and tell Ubuntu not to use the webcam to adjust brightness for the ambient light. Well, I can't do that because I can't --see-- the System menu because the screen is too dim.

Any ideas?

---

### Post by linuxopjemac on 2010-03-30
> Special keys (screen backlight, keyboard backlight, CD eject) and automatic keyboard backlight control require pommed to be installed. The package version from the standard repositories for Lucid Lynx is fine.
```

sudo apt-get install pommed
```

Edit /etc/pommed.conf to adjust settings for screen brightness and the like:

```
gksudo gedit /etc/pommed.conf
```

Then restart pommed:

```
sudo service pommed restart
```


In addition, you still need the nvidia-bl-dkms module from the [MactelSupportTeam/PPA]("https://wiki.ubuntu.com/MactelSupportTeam/PPA") to make screen backlight adjustments work correctly (also together with pommed). Note that at the time of writing there is no repository for Ubuntu 10.04 (Lucid Lynx) yet, but you can use the 9.10 (Karmic) version. (All other packages work fine when installed from the default repositories of Ubuntu 10.04 (Lucid Lynx)).

To add the ppa open the above link to the PPA's wiki page and follow the instructions. Then go to menu System -> Administration and open Software Sources. Find the newly-added entry and edit it to refer to "karmic" instead of "lucid". Closing the Software Sources control panel will update the package lists.

Then install the package:

```
sudo apt-get install nvidia-bl-dkms
```

nvidia-bl-dkms must be in /etc/modules file to load. Open the file in an editor with:

```
gksudo gedit /etc/modules
```

And add to the end this line:
```

nvidia_bl shift=2
```

The shift option reduces the dimming range to make it more comfortable; you can tune the value as you want. The module will be loaded after a reboot (or use "sudo modprobe nvidia_bl shift=2" to load it right away).

Link:
[https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid)

---

### Post by joypunk on 2010-03-30
Yup, I did all that initially, and it was working initially. Something else has happened to cause the screen to become so dim.

(Even if I hadn't of done those things, I couldn't do them now because I can't see squat on the screen.)

Thanks for the reply.

---

### Post by linuxopjemac on 2010-03-30
weird.

---

### Post by linuxopjemac on 2010-03-30
Maybe you have both mbp-nvidia-bl-dkms and nvidia-bl-dkms installed, like [here]("http://ubuntuforums.org/showthread.php?t=1440541").

You might want to do this:
```
echo 100 > /sys/devices/virtual/backlight/nvidia_backlight/brightness
```
see [here]("http://ubuntuforums.org/showthread.php?t=143683")

---

### Post by linuxopjemac on 2010-03-30
If you can't do this at all, you might have to do this from the liveCD and chroot into the sytem, see [here]("http://mac.linux.be/content/chroot-system-livecd").

You can add a script to /etc/init.d to make it start at boot (the echo thing).

---

### Post by joypunk on 2010-03-30
> **linuxopjemac said:**
> If you can't do this at all, you might have to do this from the liveCD and chroot into the sytem, see [here]("http://mac.linux.be/content/chroot-system-livecd").

You can add a script to /etc/init.d to make it start at boot (the echo thing).

I think this is what I need. Definitely need to access the system from outside of the install since I can't see anything on the actual install.

I'll give this a try and report back tonight.

Thanks again.

---

### Post by joypunk on 2010-03-30
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# echo 100 > /sys/devices/virtual/backlight/nvidia_backlight/brightness
bash: /sys/devices/virtual/backlight/nvidia_backlight/brightness: No such file or directory

```

I did everything right, didn't I?

I'm a self-admitted noob at linux, I could just reinstall the OS seeing as I just set it up a few days ago and didn't have a whole lot already installed. I'm just worried about this happening again so I'd like to know how to fix it.

---

### Post by joypunk on 2010-03-30
I looked in the newly created /mnt/root/sys folder, and there's nothing in there at all. So the /devices/virtual/... etc. folders aren't going to be there either.

How do I tell which nvidia_bl_dkms modules I have installed?

---

### Post by joypunk on 2010-03-30
Well, I was able to remove the nvidia-bl-dkms package from the liveCD / chroot combo. Logged back into Ubuntu and I could see everything again!

Now I have the mbp-nvidia-bl-dkms installed, but the Fn-F1 and Fn-F2 keys don't do anything to the brightness. The on screen display pops up and the levels change, but the actual screen brightness does not change.

---

### Post by linuxopjemac on 2010-03-31
remove mbp-nvidia-bl-dkms and install the [mactel PPA]("https://launchpad.net/~mactel-support/+archive/ppa")
sudo apt-get update
then
```
sudo apt-get install nvidia-bl-dkms
```
if that does not not work, remove nvidia-bl-dkms and install mbp-nvidia-bl-dkms

---

### Post by joypunk on 2010-04-01
Gonna mark this as solved. Some config in the nvidia-bl-dkms is causing my dim screen, but using the mbp-nvidia-bl-dkms works for me. I can't control the brightness of the screen, but I can see the screen.

Brightness controls are a different issue and I believe I've seen threads on the forums for fixing that. So this is solved.

Thanks for the help, linuxopjemac.

---

### Post by sks24 on 2012-02-14
Will the foregoing "work" with a MacBook 1,1 running 10.04?  Or is there another way to enable screen brightness adjustments?

---

