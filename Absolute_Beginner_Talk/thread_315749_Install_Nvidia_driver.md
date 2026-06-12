---
title: "Install Nvidia driver"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2006-12-09
Hi guys,

I'm trying to install the Nvidia driver for my graphics card. I'm supposed to use the following command:

"sh NVIDIA-Linux-x86-1.0-9629-pkg1.run"

However, when I execute the script, I get the error "must be run as root".

I try to copy the installer into the root directory, but Ubuntu says I don't have the permissions to do that.

Does anyone have any suggestions?

Thanks in advance guys!!!

- Stone9

---

### Post by useResa on 2006-12-09
> **Stone9 said:**
> Hi guys,

I'm trying to install the Nvidia driver for my graphics card. I'm supposed to use the following command:

"sh NVIDIA-Linux-x86-1.0-9629-pkg1.run"

However, when I execute the script, I get the error "must be run as root".

I try to copy the installer into the root directory, but Ubuntu says I don't have the permissions to do that.

Does anyone have any suggestions?

Thanks in advance guys!!!

- Stone9
You should use the "sudo" command in order to run as root.
Therefor issue the following ```
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
```

Good luck

---

### Post by invalid on 2006-12-09
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Stone9 on 2006-12-09
> **useResa said:**
> You should use the "sudo" command in order to run as root.
Therefor issue the following ```
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
```

Good luck

Oh okay. I used that command but now I get this error!!!


You appear to be running an X server; please exit X before installing.

I can't find any instance of X server running... I'm not even sure what X server is!

---

### Post by r4ik on 2006-12-09
Try,

Ctrl Alt F1 

sudo /etc/init.d/gdm stop

use the command given and do a

sudo /etc/init.d/gdm start

and you should be there.

please use kdm for kde

if X fails  "sudo dpkg-reconfigure xserver-xorg"  and follow the defaults.

Good luck !

---

### Post by al_sharpe on 2006-12-09
Hello Stone9:

For a beginner I would recommend loading the nvidia driver

with System/Administration/Synaptic Package manager

and search for nvidia

Install nvidia-glx

the latest Ubuntu version is 8776

I see nvidia has released a newer one.

There will be fewer surprises this way.

To enable the driver, run "sudo nvidia-glx-config enable".

It will ask for password, use your login password

Enjoy

Al Sharpe

---

### Post by r4ik on 2006-12-09
Could be mistaken but that would not kill X.

---

### Post by tiptip on 2006-12-09
what **r4ik** said work fine :
here it is again with a little add

```
Ctrl Alt F1
```
```
sudo /etc/init.d/gdm stop
```
please use kdm for kde
go to the place you downloaded nvidia driver and write :
```
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```
and then :
```
sudo /etc/init.d/gdm start
```

and now
```
sudo /etc/init.d/gdm
```
(or kem if you use kde)
and add
```

modprobe -r nvidia
modprobe i2c_core
modprobe nvidia

```

that should do the trick

---

### Post by rsambuca on 2006-12-09
Can't you just logout, and start a new Session in terminal mode?

---

