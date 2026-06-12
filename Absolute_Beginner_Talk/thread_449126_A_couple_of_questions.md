---
title: "A couple of questions"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by hani1400 on 2007-05-19
I need help with 2 things, im pretty much a noob to linux but not a computer idiot.

First the refreshing rate, i cant change it so i assume the graphics driver i have is not the correct one for my video card which is 7900 GTX, can anyone give me a link for its driver and tell me how to install it?

I just installed a bad driver and i couldnt enter the GUI, can anyone also tell me how to roll back the driver via the command line?

---

### Post by lazyart on 2007-05-19
at the command line, type```
sudo dpkg-reconfigure xserver-org
```
You'll probably want to select the nv driver as you run thru the configuration.   Then type```
startx
```
Once in the GUI go to system>administration>restricted drivers manager and install the nVidia driver.  Rebooth and you'll be rolling again.

---

### Post by mahiyar on 2007-05-19
Always remember that before changing any driver in linux save/backup your related configuration files, in this case the configuration file is /etc/X11/xorg.conf later when you run into problems you can always restore the backed up copy.

---

### Post by hani1400 on 2007-05-20
Thanks guys!
I tried the sudo thing, and it tells me xserver-org is not installed and no info is available.

---

### Post by hani1400 on 2007-05-20
Oh and also i have been trying to login as root and it wont let me, basically what im trying to do now is exit X and go from there with nvidias instructions on how to install their driver.

---

### Post by Bachstelze on 2007-05-20
You don't login as root in Ubuntu. You login as yourself and use sudo to run commands ith root privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hani1400 on 2007-05-20
Ok great, i tried the sudo one that lazyart gave me and it is telling me:
> package 'xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files, and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed.
Please help!

---

### Post by Bachstelze on 2007-05-20
Because lazyart is very lazy and forgot a letter ;) It's *xserver-xorg*.

---

### Post by hani1400 on 2007-05-20
lol Thanks so much!

Ok now im stuck at the package configuration where it wants me to enter the Bus Identifier for my video card, the default value thats already there is PCI:3:0:0 and i have no idea what it should be?

---

### Post by bobplano on 2007-05-20
the reconfigure does a pretty good job of autodetecting so if you don't know it you can probably just say ok
if you are completely determined to find out you can do lspci -X and find it

---

### Post by hani1400 on 2007-05-20
Ok thanks Bob.
Now im done with the configuration, how do i get out of X?

---

### Post by Bachstelze on 2007-05-20
To restart your X :

```
sudo /etc/init.d/gdm restart
```

---

### Post by hani1400 on 2007-05-20
Ok, heres what im trying to follow:
> BEFORE YOU BEGIN DRIVER INSTALLATION

Before beginning the driver installation, you should exit the X server.
In addition you should set your default run level so you will boot to a
vga console and not boot directly into X (please consult the documentation
that came with your Linux distribution if you are unsure how to do this;
this is normally done by modifying your /etc/inittab file).  This will
make it easier to recover if there is a problem during the installation.
After installing the driver you must edit your X config file before
the newly installed driver will be used.  See the section below entitled
EDITING YOUR X CONFIG FILE.


INTRODUCTION TO THE NEW NVIDIA DRIVER INSTALLER

After you have downloaded NVIDIA-Linux-x86_64-1.0-7184-pkg1.run,
begin installation by exiting X, cd'ing into the directory containing
the downloaded file, and run:

    sh NVIDIA-Linux-x86_64-1.0-7184-pkg1.run

The .run file is a self-extracting archive.  When the .run file is
executed, it extracts the contents of the archive, and runs the contained
`nvidia-installer` utility, which will walk you through installation of
the NVIDIA driver.

The .run file accepts many commandline options.  Here are a few of the
more common options:

    --info
        Print embedded info about the .run file and exit.

    --check
        Check integrity of the archive and exit.

    --extract-only
        Extract the contents of ./NVIDIA-Linux-x86_64-1.0-7184.run,
        but do not run 'nvidia-installer'.

    --help
        Print usage information for the common commandline options
        and exit.

    --advanced-options
        Print usage information for the common commandline options as
        well as the advanced options, and then exit.

Installation will also install the utility `nvidia-installer`, which may
be later used to uninstall drivers, auto-download updated drivers, etc.

[http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-7184/README/readme.txt](http://http.download.nvidia.com/XFree86/Linux-x86_64/1.0-7184/README/readme.txt)

Right now im in terminal, ive also tried doing this by exiting X (ctrl+alt+f1 .. i think that is exiting X right?)

Everytime its telling me that it "cant open NVIDIA-Linux-x86_64-1.0-7184-pkg1.run"

---

