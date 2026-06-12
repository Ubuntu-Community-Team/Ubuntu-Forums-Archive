---
title: "X won't start"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by TannerLD on 2006-12-26
Hello,

My new installation on my new Dell computer is having a bit of trouble. When X tries to start up I get "(EE) No devices detected. Fatal server error: no screens found". My video card is a ATI V3400.

Any help?

Thanks
-Tanner

---

### Post by taurus on 2006-12-26
Try booting into recovery mode from GRUB menu and at the prompt, reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
startx
```
(If you are not sure about a question, just take the default value...)

---

### Post by TannerLD on 2006-12-26
> **taurus said:**
> Try booting into recovery mode from GRUB menu and at the prompt, reconfigure your X again.

```
dpkg-reconfigure xserver-xorg
startx
```
(If you are not sure about a question, just take the default value...)

Hmm, same error.

Thanks
-Tanner

---

### Post by taurus on 2006-12-26
Did you use the LiveCD or the alternate CD to install it on your machine?

---

### Post by TannerLD on 2006-12-26
> **taurus said:**
> Did you use the LiveCD or the alternate CD to install it on your machine?

I used the "install CD" that I downloaded for Badger (yes not the latest, but I'd rather update after getting installed).

Thanks
-Tanner

---

### Post by taurus on 2006-12-26
So you installed Breezy and you upgraded to which release now, Dapper or Edgy?

---

### Post by TannerLD on 2006-12-26
> **taurus said:**
> So you installed Breezy and you upgraded to which release now, Dapper or Edgy?

I haven't upgraded yet.

The CD might've not have been Badger, it was whatever the last release of Ubuntu was (funny how fast those things fade).

Thanks
-Tanner

---

### Post by taurus on 2006-12-26
The last release was Edgy, 6.10...  Is that the LiveCD that you have?

---

### Post by TannerLD on 2006-12-26
> **taurus said:**
> The last release was Edgy, 6.10...  Is that the LiveCD that you have?

I burned the "install" edgy cd. Not sure if the edgy livecd and install cd were the same.

Thanks
-Tanner

---

### Post by taurus on 2006-12-26
When you boot the CD, do you see a Gnome window manager or you just install it directly from the CD, without clicking on the install icon?

---

### Post by TannerLD on 2006-12-26
> **taurus said:**
> When you boot the CD, do you see a Gnome window manager or you just install it directly from the CD, without clicking on the install icon?

Install directly from the cd.

Thanks
-Tanner

---

### Post by taurus on 2006-12-26
That would be the alternate CD then...

What happens if you run these from the recovery mode as well?

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by TannerLD on 2006-12-26
> **taurus said:**
> That would be the alternate CD then...

What happens if you run these from the recovery mode as well?

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

xserver-xorg postinst warning: overwriting possibly-customized configureation file; backup in /etc/X11/xorg.conf.200612262324

Thanks
-Tanner

---

### Post by TooRight on 2006-12-27
I have a Dell and had the same problem... it's the ATI driver... try this at the command prompt:

> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig force--initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now 


---

