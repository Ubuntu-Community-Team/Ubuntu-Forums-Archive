---
title: "g-desktop and nvidia on server 64 bit?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-23
Hi, I tried installing 7.10 server AMD 64. The install went well except that I want a GUI desktop on it. I ran "sudo apt-get install gnome" and I think it installed everything but the kitchen sink. ( a mistake I won't make again). The problem is, I have nvidia 6100 series video, but unlike 64 bit desktop edition, it doesn't detect and install drivers for nvidia. It defaults to vesa generic driver. I tried "dpkg-reconfigure xserver-xorg" and had to install xserver-xorg-core first. Then when I tried, nvidia is not an option. If I can get a desktop to load, then I can use restricted drivers to install the driver.

Can anyone tell me the correct packages/drivers to install through apt from terminal, starting with a fresh install of server to get a desktop GUI for it?

Thanks

---

### Post by Lacrimstein on 2008-03-23
try getting the GL driver for nvidia:

sudo apt-get install nvidia-glx

After  you install that, 

sudo nvidia-config-display enable

restart the computer, and start gnome-session


If that fails, you can install the ubuntu-desktop package; that installs everything included in the normal,  desktop edition of Ubuntu, and it sets up all the configuration files to start up gnome automatically, as well as installing Ubuntu-specific GUI tools - so i would recommend doing that, but the method above will keep your system leaner, since it is a server.

---

### Post by iansane on 2008-03-23
Cool, thanks I didn't know what package names to install. Lean is what I want. I'll do a fresh install to make sure I don't have any junk left on it from my previous attempt and try what you say. Thanks :-)

---

### Post by saj0577 on 2008-03-23
What about doing this for a non 64 bit machine?

Saj

---

### Post by Lacrimstein on 2008-03-23
for 32 bit - exactly the same

---

### Post by saj0577 on 2008-03-23
Cheers i wil give it a go. :)

Will that include all the panels and that?

Saj

---

### Post by Lacrimstein on 2008-03-23
Yup. You're installing the entire Gnome DE, so panels, desktop, icons are included. I'm not sure, but you will probably have to install things like firefox, openoffice, etc. separately

---

### Post by saj0577 on 2008-03-23
Yeah i hope you do as i dont want any of them. Thanks i shall try it now and let you know.

Saj

---

### Post by Lacrimstein on 2008-03-23
oh and iansane, before you start gnome-session, start X

```

xinit && gnome-session

```

---

### Post by iansane on 2008-03-23
OK, Thanks Lacrimstien, Glad I hadn't left yet LOL. I'm outa here to give it a try

---

### Post by Lacrimstein on 2008-03-23
Oh, and one more thing: you need to install gnome or any other desktop manager;

if you want your server to be very lightweight, i suggest you install a window manager instead, such as twm. Those give you just window borders, no desktop or anything, and may look ugly - but its fast :KS

---

### Post by saj0577 on 2008-03-23
How i swap to twm (im gonig to try it on my desktop install first?

Saj

---

### Post by Lacrimstein on 2008-03-23
Wow, so many things I forgot lol...
anyway, here is the overall process:

Install the system
```

sudo apt-get install xserver-xorg
sudo apt-get install nvidia-glx
sudo nvidia-config-display enable

```

Then, you have a choice:

```
sudo apt-get install gnome
```

              or

```
sudo apt-get install twm
```
or any other window manager

then, restart the computer.

if you installed gnome, type in:
```
xinit && gnome-session
```

if you installed twm,

```
xinit && twm
```

hope it works for you!

---

### Post by saj0577 on 2008-03-23
And for non nvidia just miss out these two lines?

sudo apt-get install nvidia-glx
sudo nvidia-config-display enable


Saj

>  sudo xinit && twm --replace

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Get that error when ran on a ubuntu desktop edition?(tring to see what twm looks like before install on server

Saj

---

### Post by iansane on 2008-03-23
So when I did apt-get install gnome and it installed a ton of packages whas that right if I want gnome and desktop? It installed evolution, sound juicer and a bunch of other apps. If ubuntu-desktop works, that will be fine for me. I just want a server 64 bit in hopes that it will run multiple virtual machines better, but I do want a desktop with access to terminal, synaptic, add remove programs and all that. My goal is not neccesarily to set up a server. I want to try that  on my virtual machines and set up a domain (at least 3 vm's). I just don't get good performance from 32 bit and someone told me that a 64 bit server would run vm's a lot better.

---

### Post by Lacrimstein on 2008-03-23
Saj:

What you tried to do was start another instance of the X server on the same virtual display.

To start TWM on your desktop, on the login screen go to options -> Session and select TWM (you will need to install the twm package first, and restart X)

to run it from server with no X started,

```
xinit && twm && xterm
```

xterm will give you a terminal window, in which you can execute commands

---

### Post by iansane on 2008-03-23
when I tried "nvidia-config-display enable" it said "command nvidia-config-display not found"

Also got an error about fonts when I did "xinit && gnome-session"

I installed ubuntu-desktop and it loaded ok after reboot.

Now when I try to enable restricted drivers, update, or install from apt or synaptic I get this.

```
 ian@lotuscontrol:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

as you can see, I did apt-get update and apt-get upgrade. I also tried apt-get -f install. 

Any idea what I did wrong?

I should add that when I installed gnome it added the generic kernel. Now I have server and generic on the grub boot menu.

---

### Post by iansane on 2008-03-23
got rid of apci and apcid and that fixed the prob with the error message. Apparently something to do with using apt to install the desktop instead of letting a live CD install everything. I never had this problem before but never installed from server 64 cd either.

Now only one thing is restricted drivers won't run without ubuntu-restricted-modules-2.6.22.14 server.

Can't find that package in synaptic

---

