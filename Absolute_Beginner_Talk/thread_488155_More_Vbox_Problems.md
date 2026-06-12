---
title: "More Vbox Problems"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by j_macattack67 on 2007-06-29
I know there are a lot of problems with vbox with people who have no idea what they are doing.  I may be one of them; I don't know.  I have done sudo aptitude install xen-headers-2.6.16.  I have done sudo aptitude install linux-headers-$(uname -r).  Here is the code I get.  Please help with this or tell me a way to get Microsoft Publisher 2003 to work in Ubuntu Feisty Fawn 7.04.  Either one would be great.
Code:

mccannon@mccannon-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-16-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

mccannon@mccannon-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.20-16-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

Dmesg is really long so i'll display it only when asked.

---

### Post by bodhi.zazen on 2007-06-29
Run sudo /etc/init.d/vboxdrv setup a second time (it takes twice typically, it is a bug).

If that fails, post  "tail demsg" , that will shorten the output ;)

---

### Post by starcraft.man on 2007-06-29
> **bodhi.zazen said:**
> Run sudo /etc/init.d/vboxdrv setup a second time (it takes twice typically, it is a bug).

If that fails, post  "tail demsg" , that will shorten the output ;)

Rats you beat me to it... oh well :p.

As for publisher alternatives, one word: [Scribus.]("http://linuxappfinder.com/package/scribus")

---

### Post by j_macattack67 on 2007-06-29
Ran sudo /etc/init.d/vboxdrv setup again.  Same output.  Couldn't get tail demsg to work but here is where it appears to go to hell.

Code:

[47116.180319] vboxdrv: Trying to deactivate NMI watchdog permanently...
[47116.180330] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[47116.180334] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[47135.739169] vboxdrv: Trying to deactivate NMI watchdog permanently...
[47135.739180] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[47135.739184] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[47446.891840] vboxdrv: Trying to deactivate NMI watchdog permanently...
[47446.891851] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[47446.891855] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[47471.199169] vboxdrv: Trying to deactivate NMI watchdog permanently...
[47471.199180] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[47471.199184] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

Good luck.  

PS provide detailed instructions or direct to a detailed how-to please.

---

### Post by j_macattack67 on 2007-06-29
Hey my mom needs publisher for cards and such and scribus doesn't have those templates.  Plus it doesn't open Publisher files from when we had WIndowsME.

Sorry, but thanks.

---

### Post by starcraft.man on 2007-06-29
> **j_macattack67 said:**
> Hey my mom needs publisher for cards and such and scribus doesn't have those templates.  Plus it doesn't open Publisher files from when we had WIndowsME.

Sorry, but thanks.

Well, nothings perfect. You can't use the Windows templates because the publisher format is exclusive to office. Blame MS.

As for the issue, I'm not sure never had that before. You did install build-essential right?

```
sudo aptitude install build-essential
```

You didn't mention that in preface, I believe vbox needs the tools.

Edit: If all you need is cards, [KDE has a greeting card app]("http://linuxappfinder.com/package/kreetingkard"). You can also of course install it in GNOME. Alternative [publishing tools]("http://linuxappfinder.com/office/publishing") can be found here. I'm just trying to point to options.

---

### Post by j_macattack67 on 2007-06-29
Yeah did that to.  And still got same output.  What is this NMI watchdog?

Thanks

---

### Post by bodhi.zazen on 2007-06-29
Did you install "watchdog" , it is a firewall.

---

### Post by j_macattack67 on 2007-06-29
hope not how do i deactivate it?

---

### Post by bodhi.zazen on 2007-06-29
I think you need to edit /boot/grub/menu.lst

In the ubuntu section you need to add : nmi_watchdog=0

at the end of the kernel line :

like this > 
title Ubuntu .....
root (hdx,y)
kernel /boot/vmlinux ... root=/dev/hdxy .... nmi_watchdog=0
....

Then, with this one, reboot

---

### Post by Seisen on 2007-06-29
Are you running a 64-bit computer?

---

### Post by starcraft.man on 2007-06-29
> **Seisen said:**
> Are you running a 64-bit computer?

Oh for the love of... I can't believe I forgot to ask that basic question. Virtual Box 1.4 does not support 64 bit, you need vmware if it is a 64 bit OS.

---

### Post by j_macattack67 on 2007-07-02
Nope running on Intel

---

### Post by starcraft.man on 2007-07-02
> **j_macattack67 said:**
> Nope running on Intel

No, we don't mean the CPU (ALL of the latest CPU's provide x86 and x64 instruction). Are you running 64 bit version of Ubuntu?

---

### Post by j_macattack67 on 2007-07-02
no its the i836 or what ever.  It came in the red case and I entered nmi_watchdog=0 in the kernel and I'm still having problems.

Thanks

---

### Post by bodhi.zazen on 2007-07-02
Hmmm ....

I would post on the virtualbox forums then :(

[http://forums.virtualbox.org/index.php?](http://forums.virtualbox.org/index.php?)

---

### Post by j_macattack67 on 2007-07-27
Thank you every one for your help.  I got it to work thanks.  Sorry for not getting back.

---

### Post by bodhi.zazen on 2007-07-28
\o/

For the benefit of others ...

How ?

---

### Post by anewguy on 2007-07-28
By the way, just to add a little curiousity to the mix, NMI stands from non-maskable interrupt, or at least it did in the old days.  A very technical thing, so I really hope you find a simple answer to your problem (I'd bet you will!!).:)

---

### Post by database_dan on 2007-11-07
> **bodhi.zazen said:**
> \o/

For the benefit of others ...

How ?

this maybe common knowledge now, but all you have to do is disable NMI in Grub (add the option "nmi_watchdog=0" to the kernel line)

```

sudo gedit /boot/grub/menu.lst

```

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5bf0de92-cba4-43a6-a866-1b6995c5c036 ro quiet splash  **nmi_watchdog=0**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

---

