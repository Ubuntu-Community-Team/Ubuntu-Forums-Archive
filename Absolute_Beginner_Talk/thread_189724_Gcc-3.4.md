---
title: "Gcc-3.4"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-06-05
I am trying to install nvidia drivers and I have it almost working.  The only problem I am currently having is that when i run the installer it gets to the gcc check screen and screams that it needs gcc-3.4 to compile the new drivers.  Thing is I have gcc-3.4 installed but it is picking up the default gcc-4.0.  What can I do so that it recognizes gcc-3.4 instead?

---

### Post by Rackerz on 2006-06-05
I think it's gcc=3.4 before running the installer. I could be wrong though.

---

### Post by richbarna on 2006-06-05
export CC=gcc-4.0 before running the installer.

---

### Post by JNowka on 2006-06-05
Still gave me the same error :/

---

### Post by richbarna on 2006-06-05
Have you installed build-essential ?

---

### Post by JNowka on 2006-06-05
> export CC=gcc-4.0 before running the installer.

Will that make the compiler gcc-4.0 or gcc-3.4?

---

### Post by JNowka on 2006-06-05
[QUOTE=richbarna]Have you installed build-essential ?[/QUOTE]

Yes I have.  I have had to compile several programs.

---

### Post by slimb on 2006-06-05
[QUOTE=JNowka]Will that make the compiler gcc-4.0 or gcc-3.4?[/QUOTE]

if you're following the nvidia install instructions it asks you install a few things that are needed for the driver install to go well. 

have you been following that guide?  If not you can find it here : 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)  (this is for dapper)  if you're running breezy let us know.

---

### Post by gr0kzer0 on 2006-06-05
I know it isn't a modem driver that you want to instal, but if I remember correctly, there's info on what you need to do when you run scanModem.  Sorry, I can't remember the URL of where you get scanModem from, but a google should locate it for you.  It's something about creating a symbolic link to the GCC version you want... heck, I'm sorry, I just can't remember.  But if you're really stuck, checking out scanModem may help.  Or maybe the linmodem site... Sorry for the vagueness.

---

### Post by JNowka on 2006-06-05
Im running breezy and my linux box doesn't have an internet connection.

---

### Post by JNowka on 2006-06-05
I continue to get an error that says "Unable to load the kernel module 'nvidia.ko'.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownerhip of the NVIDIA graphics device(s).

> Unable to load the kernel module 'nvidia.ko'.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownerhip of the NVIDIA graphics device(s).

---

### Post by JNowka on 2006-06-05
Well it caused linux to crash permetately.  Reinstalling

---

### Post by Kobalt on 2006-06-05
Hi,
I remember I had to install gcc3.4 on breezy when I had a Sagem F@st 800 usb modem. What I did was to download and install these three packages : 
cpp-3.4
gcc-3.4-base
gcc-3.4
Or something like that... you should find it [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcc-3.4&searchon=names&subword=1&version=all&release=all").
After this, I had to type in command line : 
```
CC=gcc-3.4
```
```
export CC
```

I hope it helps...

Cheers.

---

