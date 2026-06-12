---
title: "Video problems on iMac G5 Rev C"
date: 2007-05-04
forum: Apple PPC Users
---

### Post by john8520 on 2007-05-04
After being so pleased with how fast and stable Feisty is on my powerbook G3, I decided to go ahead and give it a go on my main machine. I broke of a nice little 25gb hunk for feisty, popped in my ubuntu 7.04 CD, and booted off it. At first I had some video problems, but setting 'install video=ofonly' fixed that. Half an hour later, my install was done, and I was ready to boot into the new system. Yaboot came up, I hit 'L' for linux, it loaded the kernel, then I got a little yaboot ':' prompt, then after a few seconds said 'Linux' and preceded with booting. 

Here the fans come on full blast, and I get the ubuntu loading screen; only the colors are inverted, and the image is streatched. I did my best to take a picture, thats here:

[[IMG]http://img227.imageshack.us/img227/5600/dsc6475tm6.th.jpg[/IMG]](http://img227.imageshack.us/my.php?image=dsc6475tm6.jpg)

Any idea whats going on? I have a feeling that xorg.conf is just not properly set up, and that if I could some how either mount the linux stuff in OS X, or boot linux but have X *not* start I can go in and edit stuff manually. Any other thoughts? I'd relly like feisty running on here!

Thanks,
John

EDIT- 

oh geez, I totally forgot to post the specs of the machine, they're just a bit important...

```
iMac G5 Rev C, iSight
PowerPC G5 @ 1.9GHz
1GB RAM
160 GB HDD, split 130/25 for OSX/Linux
ATI Radeon X600 Pro, running the screen at 1440*900

```

---

### Post by stmiller on 2007-05-04
Thank you for posting this. We actually need persons with this rev. C iMac to try Linux. The rev. C has a totally different thermal/fan setup than previous machines, so with previous kernels thermal management was never under control.

You'll have to get to a terminal somehow, to make changes to the xorg.conf file, and to specify to load the thermal modules.

So either via ssh (if ssh is installed on the iMac?), locally on the machine (if you can Ctrl-Alt-F1 to a terminal), or the other way is to boot a Live CD (gentoo or Ubuntu alternative), mount the partition, and edit the certain configuration files.

You should know that your machine will not be damaged in any way with the 100% fans; the fans coming on full blast are a built-in hardware safety by apple in case proper thermal control is not loaded. In this case, the thermal modules are not being loaded for some reason.

It's probably good for you to read this page, though most info on there is out of date:
[https://wiki.ubuntu.com/iMacG5revC](https://wiki.ubuntu.com/iMacG5revC)

and this report: 

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/34723](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/34723)

And here is an xorg.conf for an iMacG5 20", if you want to make changes to yours and make it like this one:
[http://bersace03.free.fr/pub/Linux/iMac%20G5/xorg.conf](http://bersace03.free.fr/pub/Linux/iMac%20G5/xorg.conf)

And then for thermal, you need to edit the file /etc/modules
and add
therm-pm72
windfarm

and that will load those on boot.

Note: I do not have one of these machines to test myself.

---

### Post by john8520 on 2007-05-04
Fantastic! I'll give this stuff a try right away!

---

### Post by john8520 on 2007-05-04
Ok, problems.

I hit ctrl-alt-F1, and got moved to a screen with 'Loading, please wait...' in the upper left hand corner. A few minutes later, it spits out all this:

```

Loading, please wait...
stdin: error 0
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
mount: cannot read /etc/fstab: No such file or directory
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init


BusyBox v1.1.3 (Debian 1:1.1.3ubuntu3) Built-in-shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ 

```

Thoughts...?

---

### Post by stmiller on 2007-05-04
Hmm. Try Ctrl+Alt+F2 or F3. See if any of those give you a prompt that looks like

login:

---

### Post by john8520 on 2007-05-04
Nope. F2-F12 just have a blinking underscore in the top left hand corner. No login prompt.

I remember seeing that my Ubuntu Alt CD has a little command prompt on it, can I boot from that and fix the problem? If so... how?

Thanks!

John

---

### Post by stmiller on 2007-05-04
Ouch okay this means that the kernel did not actually boot properly, or it is hanging in the boot process. :-(

So the install process went okay, firstly? And did you make sure to pick powerpc64-install at the initial install prompt? These iMacs need a 64bit kernel.

---

### Post by john8520 on 2007-05-04
I was never given a chance to choose ppc64, or did I need to type 'powerpc64-install video=ofonly' at the beginning?

If so, I'll give it another go!

---

### Post by stmiller on 2007-05-04
Hey yeah try the feisty alternative CD. And at the boot prompt, press TAB to see possible install options. Choose the powerpc64 install.

---

### Post by john8520 on 2007-05-05
Nope :(

i did install-powerpc64 video=ofonly at that prompt, did the install as normal, and rebooted. I got the same errors... Thoughts? Maybe my CD is bad?

Is there a way I can netinstall or something?

---

### Post by john8520 on 2007-05-07
Anyone? 

I've reburned the Ubuntu CD at least 5 times, and installed over 10, and I'm getting NO changes. Maybe this machine will just never run linux, esp since Ubuntu development for PPC has been axed...

I tried YDL too, it pseudo-works, but there is terrible gfx support...

---

### Post by stmiller on 2007-05-07
Many have installed Linux just fine on this machine. It was only thermal management that didn't work. (Fans would run 100%). Have you searched this forum section for threads on the imac g5 rev c? Also check out the ppc section in forums.gentoo.org for possible hints. People there have had success with this iMac.

---

