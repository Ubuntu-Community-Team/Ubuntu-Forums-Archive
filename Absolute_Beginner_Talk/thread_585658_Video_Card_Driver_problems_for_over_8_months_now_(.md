---
title: "Video Card Driver problems for over 8 months now (PayPal If Solved)"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Crafty Kisses on 2007-10-21
OK, so I have a NVIDIA GeForce 6800 GT, everytime I install the drivers, it malfunctions, I have a video down below to define Malfunciton, I noticed in my BIOS the option "Enable Video Ram Cacheable" appears and that was disabled, so should I enable that? 

Video:

Specs:

AMD Athlon 1800+
1 GB of Ram
40 GB HDD

---

### Post by Jimmyfj on 2007-10-21
Could you list the make of your mobo?

---

### Post by aktiwers on 2007-10-21
Have you done this?

Go here and download the latest driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1

Log in.
type:
```
sudo /etc/init.d/gdm stop
```
```
cd Desktop
```And then 
```
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
```when done.. type:
```
sudo reboot
```

---

### Post by Crafty Kisses on 2007-10-21
> **Jimmyfj said:**
> Could you list the make of your mobo?

Honestly man I couldn't tell ya.

---

### Post by Crafty Kisses on 2007-10-21
> **aktiwers said:**
> Have you done this?

Go here and download the latest driver:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Save it on Desktop.

Log out.

Hit CTRL+ALT+F1

Log in.
type:
```
sudo /etc/init.d/gdm stop
```
```
cd Desktop
```And then 
```
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
```when done.. type:
```
sudo reboot
```
I used restricted drivers manager, doesn't that install the latest drivers?

---

### Post by magli on 2007-10-21
There is something wrong with your attachment. It is only 98 bytes.

---

### Post by Pumalite on 2007-10-21
Post # 3 is a pretty good advise.

---

### Post by Crafty Kisses on 2007-10-21
> **magli said:**
> There is something wrong with your attachment. It is only 98 bytes.

Here are screens then:
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-9.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-1-4.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-2.png[/IMG]
[IMG]http://i81.photobucket.com/albums/j216/codenamexiii/Screenshot-8.png[/IMG]

---

### Post by overlord.gaurav on 2007-10-21
Why don't you try [Envy]("http://albertomilone.com/nvidia_scripts1.html") once. I know some people are ready to oppose me out there, but it works like a wonder for me!

EDIT: Awwww, the screen looks pathetic! It shouldn't be like that even without the graphic card drivers.

---

### Post by magli on 2007-10-21
Ouch... that looks pretty messy. You may want to try your luck on the nvidia forums. You should also look into some of the additional options you can add to your xorg.conf file. Check out this thread, it is off topic, but discusses some of interesting options you may want to try:
[http://forum.compiz-fusion.org/showthread.php?t=1762&highlight=black+window](http://forum.compiz-fusion.org/showthread.php?t=1762&highlight=black+window)

---

### Post by Mondoman on 2007-10-21
You might want to try running memtest86+ (bootable floppy or CD image freely downloadable) to make sure you don't have a memory/CPU issue, then try booting from the Linux "Live" CD (doesn't use your hard disk) and see if the video works OK.  If so, then at least you know it's not a problem with your video card hardware.

---

### Post by kyphi on 2007-10-21
The two necessary files for the nVidia 6800 card are in the repositories accessible via Synaptic.  They are nvidia-glx and nvidia-kernel-common.

After installation type in a terminal ```
sudo nvidia-glx-config enable
```

---

