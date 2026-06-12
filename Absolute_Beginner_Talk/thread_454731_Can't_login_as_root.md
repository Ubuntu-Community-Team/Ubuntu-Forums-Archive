---
title: "Can't login as root"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by JordanII on 2007-05-25
I am trying to install the driver to my nVidia GeForce 6100 GPU and when I open it from the terminal with the command "sh NVIDIA-Linux-x86-1.0-8174-pkg1.run" it says that I need to be logged in as root. I went to the login screen and it told me that I can't login to the root account from that screen. How should I go about doing this? Thanks!

~Jordan

---

### Post by madmetal on 2007-05-25
> **JordanII said:**
> I am trying to install the driver to my nVidia GeForce 6100 GPU and when I open it from the terminal with the command "sh NVIDIA-Linux-x86-1.0-8174-pkg1.run" it says that I need to be logged in as root. I went to the login screen and it told me that I can't login to the root account from that screen. How should I go about doing this? Thanks!

~Jordan

give a look ;)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by icechen1 on 2007-05-25
use this command ```
gksudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
```

---

### Post by JordanII on 2007-05-25
> **madmetal said:**
> give a look ;)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Will do. Thanks!

~Jordan

---

### Post by JordanII on 2007-05-25
I did what it said but now it says that I can't do it while running X. How do I get out of X? Thanks!

~Jordan

---

### Post by taurus on 2007-05-25
> **icechen1 said:**
> use this command ```
gksudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
```

You also need to shutdown your X server first before you can install nVidia by hand or else it will complain about it.  

<Ctrl><Alt>F2 and log in with your username and password.  Then, shut down gdm with

```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
sudo /etc/init.d/gdm start
```
(Make sure you are in the directory where "NVIDIA-Linux-x86-1.0-8174-pkg1.run" is when you run the second command.)

---

### Post by JordanII on 2007-05-25
> **taurus said:**
> You also need to shutdown your X server first before you can install nVidia by hand or else it will complain about it.  

<Ctrl><Alt>F2 and log in with your username and password.  Then, shut down gdm with

```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
sudo /etc/init.d/gdm start
```
(Make sure you are in the directory where "NVIDIA-Linux-x86-1.0-8174-pkg1.run" is when you run the second command.)

Thanks a lot! I'll give that a try.

~Jordan

---

### Post by JordanII on 2007-05-25
> **taurus said:**
> You also need to shutdown your X server first before you can install nVidia by hand or else it will complain about it.  

<Ctrl><Alt>F2 and log in with your username and password.  Then, shut down gdm with

```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-8174-pkg1.run
sudo /etc/init.d/gdm start
```
(Make sure you are in the directory where "NVIDIA-Linux-x86-1.0-8174-pkg1.run" is when you run the second command.)

I tried what you said and it says that I need the libc development packages. What should I do? Thanks!

~Jordan

---

### Post by taurus on 2007-05-25
Maybe you need to install the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```
Which release are you running?

---

### Post by JordanII on 2007-05-25
> **taurus said:**
> Maybe you need to install the build-essential package.

```
sudo aptitude update
sudo aptitude install build-essential
```
Which release are you running?

I am running 7.04. It is downloading now. Thanks!

~Jordan

---

