---
title: "problem installing"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by koprioni on 2006-12-01
i have problem on installing ubuntu6.1 and kubuntu.
i boot from cd/dvd and after loading the kernel then the installation stops and does nothing.
Plz help me.it shows the ubuntu/kubuntu logo and a bar that loading  and after a while it stops and shows me some green lines(below the bar).im trying to install i386.
i have a laptop with an intel pentium M 2Gz and ati mobitily radeon x700.
Thnx

---

### Post by Bachstelze on 2006-12-01
Try using an "Alternate" CD ;)

---

### Post by koprioni on 2006-12-01
what is an alternate cd?where can i find it?

---

### Post by Bachstelze on 2006-12-01
The "Alternate" CD is the old-school text-based installer. Less pretty but also far less likely to fail on you. You can get it from the same location where you got your "Desktop" CD.

---

### Post by 56phil on 2006-12-01
Welcome to Ubuntu.:) 

You can find it here:

[alternate install CD]("http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso")

Once you get Ubuntu installed, I'm sure you'll want to install the ATI video driver. Here's how:
```

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
After that, you probably won't have all the screen resolutions your system can do. So, you'll need to edit your xorg.conf file to add them:
```
sudo gedit /etc/X11/xorg.conf
```
Please make a backup copy first:```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Now, you're almost done. You need to do one more thing to keep your system from freezing when you shut down. You need to add vga=788 to the end of each kernel line in your menu.lst file:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst

```
I simply replaced 'quiet splash' with 'vga-788' because I like to keep a closer eye on things than many people.

Well, I hope this helps. If you have any more questins, check out these links:

[ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu:Edgy")
[Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")
You can always come back here too.

---

### Post by koprioni on 2006-12-01
thnx i found it. i hope this works
does anyone knows what may be the cause of the problem?
do i have to do something special to install from alternate cd?

---

### Post by Bachstelze on 2006-12-01
Most likely your graphics card is the problems. ATis are not the best thing in Linux.

---

### Post by koprioni on 2006-12-01
maybe yes!
when i had installed ubuntu 5.1 when it was being loaded it hunged up at something "starting hotplague system".do u think it can be done with 6.1 too?

---

### Post by Bachstelze on 2006-12-01
Yeah, that's a well known issue with Breezy - and older kernels in general, fixed now :)

---

### Post by koprioni on 2006-12-01
thnx 56phil!
its working now
af course im a little bit lost now but ill work it out.
Thnx again

---

