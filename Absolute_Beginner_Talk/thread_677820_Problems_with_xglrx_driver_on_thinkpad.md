---
title: "Problems with xglrx driver on thinkpad"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Furstan_88 on 2008-01-25
Hi,

I'm getting a error when trying to install video-drivers for my IBM Thinkpad T60 (graphics by ATI).

```

Ekristoffer@kristoffer-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
The following packages were automatically installed and are no longer required:
  libstdc++5 unixodbc odbcinst1debian1 gcc-3.3-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 27.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114187 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was trying to resolve a bug but it didn't work, and now I'm trying to set back what I destroyed. This is the guide I followed:
[I]
  Fix suspend/resume

If you suffer from Ubuntu bug 121653 and you choose to fix it via the two following methods, first you need to make a few changes to /etc/default/acpi-support:

POST_VIDEO=false
RADEON_LIGHT=true
ENABLE_LAPTOP_MODE=true

Upgrading to FGLRX-8.443.1

This driver fixes the issues with suspend/resume. Uses the new codebase so, if you want stabillity, stick to 8.40.1 It is not recommended to use it with AIGLX yet, but works perfectly with XGL. (That's not my experience; I installed 8.443.1 with Envy and saw lots of graphic garbage on the screen. For my FireGL 5200, 8.40.4 with a cucstom kernel as described below works much better --Dave)

Install dkms:

$ sudo apt-get install dkms

Download ati-driver-installer-8.443.1-x86.x86_64.run from here.

Run:

$ chmod a+x ati-driver-installer-8.443.1-x86.x86_64.run

Build the packages:

$ ./ati-driver-installer-$VER-x86.x86_64.run --buildpkg Ubuntu/gutsy

Install:

$ sudo dpkg -i *.deb

Disable 8.37.1 from the restricted modules. Edit /etc/default/linux-restricted-modules-common and add to the list:

 DISABLED_MODULES=fglrx
[/I]

Thank in advance
/Kristoffer

---

### Post by startherepodcast on 2008-01-25
I had got the same problem... I tried the new ATi drivers with AIGLX for compiz-fusion direct rendering... But to my surprise it was much choppier than running wit hthe old version!
I tried to go back loads of times and I went hrough a lot of XServer starting failiures and finally figured out that I would have to stick to the new drivers... 
I disabled VideoOverlay and OpenGLOverlay I think it was in the Device section of /etc/X11/xorg.conf and now everything is working like a charm... Except for Video.

Hope that helped

Leon

---

