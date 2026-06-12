---
title: "Nvidia Drivers"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by griz on 2006-02-20
Hi all,
I've got a Nvidia NV18 [GeForce 4 MX 440AGP 8X] video card in my computer which is dual-booting with Breezy and Dapper.  The Nvidia drivers work in  Breezy but I can't get them to work in Dapper.  When I try to install nvidia-glx with Synaptic, I get the following error:

E: /var/cache/apt/archives/nvidia-glx_1.0.8178+2.6.15.5-2_i386.deb: subprocess pre-installation script returned error exit status 2

I've tried all the information that I can find on the forums but can't get this to work.  This is the last major problem I have with Dapper and would really appreciate it if someone could possibly point me in the right direction.  

Many thanks,

Griz.

---

### Post by Jedeye on 2006-02-20
did you try
```
sudo apt-get install nvidia-kernel-common nvidia-glx
```
thats all I did in dapper
Edit:
almost forgot... and then edit your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

but check the forums for what to update your xorg.conf with... I put in the values from poofyhairguy's xgl/compiz How-To as I was setting it up for that.

---

### Post by griz on 2006-02-20
Thanks for the reply Jedeye, but it didn't work.  apt-get says I've already got the the newest nvidia-kernel-common.  I tried removing them and re-installing, but that didn't work either.  I'm thinking that I might have to re-install Dapper to get it working, but I don't want to have to do that :( 

Griz.

---

### Post by Jucato on 2006-02-20
you could also try asking in the Dapper section, they might be able to offer more help, since Dapper is still in testing period.

---

