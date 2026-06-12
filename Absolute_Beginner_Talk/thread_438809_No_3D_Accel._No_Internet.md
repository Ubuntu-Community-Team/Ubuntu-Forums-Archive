---
title: "No 3D Accel. No Internet"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by andrew.co.za on 2007-05-10
Hi, I so badly want to become an Ubuntu l337zor hacker. But for now i'm still digging my way through Absolute Beginner Forums.

I don't have 3D Acceleration and i don't have an internet connection. I have a 7900GTX and i have an internet connection at work.
The pre-installed nvidia drivers won't enable and the 9755 drivers (which i downloaded at work) are also not working. what i've gathered so far is that there are dependency issues. I have everything i need on my Ubuntu PC at home (driver plus everything i could get off the Beryl website but that a whole other post). how do i get 3D acceleration up and running? Please someone give me a useful answer!

---

### Post by diskotek on 2007-05-10
i'm not sure if these links would be useful dor you, but you can check it:
[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

by the way what does **l337zor hacker** means?

---

### Post by Kobalt on 2007-05-10
Have you checked the Restricet Drivers Manager : System > Admin. > Restricet Drivers Manager ?

---

### Post by andrew.co.za on 2007-05-10
l337zor Hacker = Elite Hacker (by that i just mean i want to know my way around Ubuntu and linux the way i do in Windows). Anyway, I've been to the Restricted Drivers Manager when i enable the drivers that are pre-installed it asks for confirmation. After accepting, the drivers stay disabled, what's up with that. when i run the 7955 driver package i get an error saying dependencies are not satisfiable, or something like that. when i run the run file from the site (after stopping the xserver) it says it needs to compile something and then gives an error saying the libc headers are missing. How do i install these headers? Aseblief help me out here.

---

### Post by Bachstelze on 2007-05-10
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

the nvidia installer should work then.

---

### Post by andrew.co.za on 2007-05-11
Package build-essential not found. Thanks for trying though.

---

### Post by andrew.co.za on 2007-05-11
Anyone else have any suggestions?

---

### Post by MoxJet on 2007-05-11
Did you get your internet working?
Otherwise, you might want to try the following commands:
```
sudo mii-tool
sudo ifdown eth0
sudo ifup eth0
sudo ifconfig
sudo ifconfig eth0
```
If eth0 is what you're using ( most probable if you use DSL )
You might also want to look in your /etc/network/interfaces file
```
gksu gedit /etc/network/interfaces
```

---

### Post by andrew.co.za on 2007-05-11
No, i don't have a connection at home at all. but i can download stuff at work and take it back home.

---

### Post by Bachstelze on 2007-05-11
build-essential and your kernel headers are on your Ubuntu CD.

```
sudo apt-cdrom add
* insert your CD here and press Enter*
sudo apt-get install build-essential linux-headers-$uname -r)
```

Just as a side note, if you have no Internet connection, Ubuntu wil be much hasstle to install software. You might be better off with Debian.

---

### Post by andrew.co.za on 2007-05-14
Thanks that worked, the nvidia drivers installed successfully, but they broke GDM. I don't think i was meant to be a linux user, i run into issues every step of the way. If someone has any idea why the drivers killed the x server and how to fix it i'd appreciate it. But to be honest i think i'm just going to have to deal with a carcass of an operating system lying around on my HDD since grub is installed anyway.

---

### Post by seshomaru samma on 2007-05-14
First - don't be discouraged by problems, most people cannot install nVidia drivers on Windows even after years of running it (infact most people don't know what drivers are...)
dont expcet to be a Linux hacker after 3 days of Linux,
give it some time
what you should try is log into recovery mode (you will find the option on the grub menu) and run this command
```
sudo dpkg-reconfigure xserver-xorg
```

(not sure if you need that 'sudo' bit in the command)

---

### Post by andrew.co.za on 2007-05-14
Thanks for the pep talk :P but believe me i really don't want to give up, i'm not that kind of person. Thing is; this isn't the first time i've battled with linux or even ubuntu for that matter. Thanks for the help i'll give it a try and let you know. 

By the way it was the part about most people not even knowing what a driver is that convinced me ;) i've tried to explain that one a few time myself. A perfect world would be one where open source is the standard.

---

