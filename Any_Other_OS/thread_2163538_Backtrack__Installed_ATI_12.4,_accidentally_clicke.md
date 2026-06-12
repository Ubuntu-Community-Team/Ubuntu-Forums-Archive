---
title: "Backtrack:  Installed ATI 12.4, accidentally clicked activate fglrx driver"
date: 2013-07-18
forum: Any Other OS
---

### Post by dstoler on 2013-07-18
[FONT=arial]So I managed to manually install the latest ATI drivers for my HD7950, I am using backtrack 5 r3 (ubuntu 10.04 kde) I downloaded the drivers from amd webside and did chmod +x amd-catalyst-13.4-linux-x86.x86_64.run and then ./amd-catalyst-13.4-linux-x86.x86_64.run and it installed everything and all was well. Seeing how I am new to Linux I was exploring my computer and came across the hardware drivers section and noticed it said that my drivers were not activated, so I proceeded to click it and it started downloading and installing. I didnt think much of it at the time but what I realize now is I reactivated the fglrx drivers and it uninstalled the ati drivers. Now when I attempt to reinstall ati drivers with the above process it says to me that 

"a previous install of the fglrx has been detected. please uninstall the old version before installing this version. Optionally run installer with -force option to overwrite the existing driver. Forcing install is not recommended."

I have followed many tutorials and feel I am just burying myself deeper and deeper each time as I really do not know what I am doing yet for the most part. I have tried this command 
[COLOR=#222222] 
sh /usr/share/ati/fglrx-uninstall.sh[/COLOR]apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

[B]but it just tells me no such file or directory. I just need to know how to "start over" with the process and make sure that everything is removed that should be removed and continue on in the right direction. 


[/B]It appears backtrack forums are closed so I didn't know where else to turn to. Thank you for your time and I hope I didn't leave out any crucial information.[/FONT]

---

### Post by dstoler on 2013-07-18
I am so confused on what could be going on and what to do from here. Whenever I try to reinstall the drivers from amd's website as stated above I get the error to please remove the old fglrx drivers first. I run these 2 commands:

```
[FONT=arial]sh /usr/share/ati/fglrx-uninstall.sh[/FONT]
```

and I get no such directory. Then I try this code:

```
[FONT=arial]apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*[/FONT]
```

and I get this:

```
[FONT=arial]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Package fglrx is not installed, so not removed
Note, selecting xorg-driver-fglrx for regex 'fglrx_*'
Note, selecting fglrx-kernel-source for regex 'fglrx_*'
Note, selecting xorg-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx for regex 'fglrx_*'
Note, selecting fglrx-driver-dev for regex 'fglrx_*'
Note, selecting fglrx-control-qt2 for regex 'fglrx_*'
Note, selecting fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-modaliases for regex 'fglrx_*'
Note, selecting xfree86-driver-fglrx-dev for regex 'fglrx_*'
Note, selecting fglrx-amdcccle for regex 'fglrx_*'
Note, selecting fglrx-control for regex 'fglrx_*'
Note, selecting fglrx-amdcccle for regex 'fglrx-amdcccle*'
E: Couldn't find package fglrx-amdcccle*[/FONT]
```

Should I try adding -force command to the end of the install? How can I get my correct drivers for my setup? I have been at this all day and feel I am getting nowhere. Thanks in advance.

---

### Post by dstoler on 2013-07-18
I just did "apt-get install fglrx" and this is what it kicked back:

```
[FONT=arial]Reading package lists... Done[/FONT][FONT=arial]Building dependency tree       [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]The following packages were automatically installed and are no longer required:[/FONT]
[FONT=arial]  libecryptfs0 libgnome2-vfs-perl libdmraid1.0.0.rc16 libdebconfclient0[/FONT]
[FONT=arial]  libgnomevfs2-extra ecryptfs-utils cryptsetup rdate gdb bogl-bterm[/FONT]
[FONT=arial]  libdebian-installer4 librarian0 software-properties-gtk rarian-compat[/FONT]
[FONT=arial]  libgnome2-canvas-perl synaptic reiserfsprogs libgnome2-perl dmraid[/FONT]
[FONT=arial]  python-pyicu scrollkeeper apport-gtk[/FONT]
[FONT=arial]Use 'apt-get autoremove' to remove them.[/FONT]
[FONT=arial]The following extra packages will be installed:[/FONT]
[FONT=arial]  fglrx-amdcccle[/FONT]
[FONT=arial]The following NEW packages will be installed:[/FONT]
[FONT=arial]  fglrx fglrx-amdcccle[/FONT]
[FONT=arial]0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.[/FONT]
[FONT=arial]Need to get 0B/34.3MB of archives.[/FONT]
[FONT=arial]After this operation, 110MB of additional disk space will be used.[/FONT]
[FONT=arial]Do you want to continue [Y/n]? y[/FONT]
[FONT=arial]Selecting previously deselected package fglrx.[/FONT]
[FONT=arial](Reading database ... 298051 files and directories currently installed.)[/FONT]
[FONT=arial]Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu5_amd64.deb) ...[/FONT]
[FONT=arial]Selecting previously deselected package fglrx-amdcccle.[/FONT]
[FONT=arial]Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.723.1-0ubuntu5_amd64.deb) ...[/FONT]
[FONT=arial]Processing triggers for man-db ...[/FONT]
[FONT=arial]Processing triggers for ureadahead ...[/FONT]
[FONT=arial]Setting up fglrx (2:8.723.1-0ubuntu5) ...[/FONT]
[FONT=arial]update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.[/FONT]
[FONT=arial]update-initramfs: deferring update (trigger activated)[/FONT]
[FONT=arial]Loading new fglrx-8.723.1 DKMS files...[/FONT]
[FONT=arial]First Installation: checking all kernels...[/FONT]
[FONT=arial]Building only for 3.2.6[/FONT]
[FONT=arial]Building for architecture x86_64[/FONT]
[FONT=arial]Building initial module for 3.2.6[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Error! Bad return status for module build on kernel: 3.2.6 (x86_64)[/FONT]
[FONT=arial]Consult the make.log in the build directory[/FONT]
[FONT=arial]/var/lib/dkms/fglrx/8.723.1/build/ for more information.[/FONT]
[FONT=arial]dpkg: error processing fglrx (--configure):[/FONT]
[FONT=arial] subprocess installed post-installation script returned error exit status 10[/FONT]
[FONT=arial]dpkg: dependency problems prevent configuration of fglrx-amdcccle:[/FONT]
[FONT=arial] fglrx-amdcccle depends on fglrx; however:[/FONT]
[FONT=arial]  Package fglrx is not configured yet.[/FONT]
[FONT=arial]dpkg: error processing fglrx-amdcccle (--configure):[/FONT]
[FONT=arial] dependency problems - leaving unconfigured[/FONT]
[FONT=arial]No apport report written because the error message indicates its a followup error from a previous failure.[/FONT]
[FONT=arial]                          Processing triggers for python-gmenu ...[/FONT]
[FONT=arial]Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...[/FONT]
[FONT=arial]Processing triggers for initramfs-tools ...[/FONT]
[FONT=arial]update-initramfs: Generating /boot/initrd.img-3.2.6[/FONT]
[FONT=arial]Processing triggers for python-support ...[/FONT]
[FONT=arial]Errors were encountered while processing:[/FONT]
[FONT=arial] fglrx[/FONT]
[FONT=arial] fglrx-amdcccle[/FONT]
[FONT=arial]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]
```

Anything?

---

### Post by QIII on 2013-07-18
[I]Moved to [B]Other OS/Distro Support


[/B][/I]Although backtrack is based on Ubuntu, it is a separate distribution.

---

### Post by dstoler on 2013-07-18
Nothing about any of this is seemingly Backtrack specific though is it? Alrighty then, thanks for the awesome help!

---

### Post by cpatrick08 on 2013-07-18
backtrack is dead and has been forked as [http://www.kali.org/](http://www.kali.org/)

---

