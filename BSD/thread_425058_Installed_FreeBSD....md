---
title: "Installed FreeBSD..."
date: 2007-04-27
forum: BSD
---

### Post by Ozor Mox on 2007-04-27
Just for the fun of it I installed FreeBSD on my currently unused desktop PC to see what it was like. I think it really doesn't like my computer. Here's what I tried...

Selected "All" for the installation type (to install all core packages). Installed Gnome from the ports selection at the end of the installation. Set Gnome to start on boot. Rebooted. Gnome starts but is painfully slow. The Window Manager/Panel/Nautilus things it shows took about 2 minutes each. It takes about 5 minutes to start up, and then each application will take several minutes to start up itself. Once running, applications run fine, but no sound and no proper display resolution.

Selected "All" for the installation type but didn't install Gnome. Configured Xorg first, then installed Gnome using ports. Exactly the same as above.

Selected "User" for the installation type so I only get basic packages. Installed Xorg after logging in. Configured. Installed Gnome. Same as above. Argh!

Selected "User" for the installation type. Installed Xorg after logging in. Configured. Installed KDE. It booted up perfectly fast but still no sound or proper display resolution and the fonts are virtually unreadable.

Other problems were that the boot time was hardly fast (especially including how long Gnome would take to start up). If I didn't have the LAN cable plugged in, the system would sometimes simply reboot itself while starting X.

What on earth was going on here? Am I going about this completely the wrong way or is it just not suited to my particular desktop? I've since reinstalled Ubuntu which works beautifully, but it'd be nice to have a BSD working nicely just because! :popcorn:

---

### Post by Nikron on 2007-04-28
You'll probably have to hand edit xorg.conf in freebsd.  Anyway, I just installed it using the 'User' option.  I can't really have a GUI considering I'm running it off of a Pentitum II processor, 64 megs of ram...  I mean, compiling and installing bash is taking forever.

---

### Post by ertrules22 on 2007-08-06
What exactly does your PC have as far as memory, hard drive space, GHz, etc.  This may help solve the problem, if I know what you have.  So, you edited the rc.conf, in the /etc/ (whatever it is directory, I'm not looking at what it is right now.)  Did you follow the directions on the FreeBSD handbook site?  I am unable to edit this file on mine as even the root user, but I followed a tutorial on the FreeBSD handbook, and all I had to do was type a line on start up (in the command line) and type startx, and it worked slightly slow but the laptop is a celeron!

---

### Post by the_darkside_986 on 2007-10-08
The first thing I noticed: you picked gnome. But IMO, Gnome on FreeBSD looks horrible and its file browser is barely usable compared to Ubuntu. So I always pick KDE. But if your system is old and slow then you might be better off using nothing but a few xterms (the default for what startx command does).

If you want your sound to work, you should google "open sound system." Their package, which one installs via pkg_add oss-package-name-orwhatever.tbz as root, is what I depend on always to get my sound to work in FreeBSD.

I understand that you picked "All" as your installation? I assume that this includes the kernel source tree. This is very important to have because if you are installing extra drivers, they might need this in order to build the kernel module interface. 

I noticed that gnome was too painfully slow on my system with an old Celeron and 128 MB of RAM so I am tempted to try PC-BSD (it has KDE) on that system, or some other desktop environment. Your display is probably using the vesa driver or something else that is slow so you should make sure the screen resolution isn't too high until you find (if possible) the correct graphics card driver.

---

