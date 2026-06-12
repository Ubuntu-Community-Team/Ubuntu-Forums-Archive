---
title: "ubuntu nub: impressed, with a couple of queries"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2006-09-30
Hi all - looks like a great community here. :)

Yesterday I installed ubuntu Desktop 6.06 LTS, and I'm most impressed. I've installed SUSE Linux 10 before, but that's as far as my experience with Linux goes. Even so, the process was quick and painless, and I have a lovely GUI, several nice apps and a XAMPP test web server.

If someone could enlighten me on the following points it would be great:

My menu.lst contains the following:

```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hde2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hde2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hde2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hde2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hde1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Why are there two instances of ubuntu, each with recovery mode? They both seem to load the same ubuntu OS. I did install ubuntu Server prior to repartitioning and installing Desktop (once I realised it didn't include a GUI) - are the additional entries from that? If so, how do I tell which kernel version to remove?

Also, I'd like to change the default login screen resolution as the default 1280 by something doesn't look pretty on my old CRT at 60Hz.

I'll begin searching for HTML/CSS/PHP editors for Linux soon, but if anyone has any recommendations I'd be glad to hear them.

Many thanks.

Edit: Sorry, just thought of another one... how do I stop the hard drive icons appearing on the desktop?

---

### Post by aysiu on 2006-09-30
You can uninstall the old kernel by searching in System > Administration >Synaptic Package Manager for the phrase *linux-image*

For HTML/CSS/PHP, I use Gedit. Screem, Bluefish, Quanta, and Amaya may also be worth checking out.

You can have the hard drive icons not appear by pressing Alt-F2 and typing ```
gconf-editor
``` go to Apps > Nautilus > Desktop > Volumes_Visible

---

### Post by Rumor on 2006-09-30
> **ImpelGD said:**
> Hi all - looks like a great community here. :)

Yesterday I installed ubuntu Desktop 6.06 LTS, and I'm most impressed. I've installed SUSE Linux 10 before, but that's as far as my experience with Linux goes. Even so, the process was quick and painless, and I have a lovely GUI, several nice apps and a XAMPP test web server.

If someone could enlighten me on the following points it would be great:

My menu.lst contains the following:


Why are there two instances of ubuntu, each with recovery mode? They both seem to load the same ubuntu OS. I did install ubuntu Server prior to repartitioning and installing Desktop (once I realised it didn't include a GUI) - are the additional entries from that? If so, how do I tell which kernel version to remove?



It's possible the additional entries are from the other install. You can edit the menu.lst file and remove them without jeopardizing anything. Back it up first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
Then edit it:
```
sudo gedit /boot/grub/menu.lst

```
You can remove or comment out the extra set of entries.


> **ImpelGD said:**
> Also, I'd like to change the default login screen resolution as the default 1280 by something doesn't look pretty on my old CRT at 60Hz.

The file containing your screen resolutions is your xorg.conf file. You can back up and edit it like the menu.lst file. The path to it is /etc/X11/xorg.conf. Near the bottom of the file you will see the list of resolutions for each color depth You can add to them and it should (theoretically) work. If it doesn't, that's what back ups are for. :) 


> **ImpelGD said:**
> 
I'll begin searching for HTML/CSS/PHP editors for Linux soon, but if anyone has any recommendations I'd be glad to hear them.

Many thanks.

Edit: Sorry, just thought of another one... how do I stop the hard drive icons appearing on the desktop?

I don't do html editing, but I have hear people say good things about Nvu which is available through synaptic (System > Administration > Synaptic Package Manager

You can make the drive icons go away by opening a terminal (Applications > Accessories > Terminal) and typing gconf-editor in it and pressing enter. In the editor, click on apps > nautilus > desktop and uncheck the "Volumes Visible" checkbox. 

Then you should be all set!

---

### Post by ImpelGD on 2006-09-30
Thanks for the quick reply aysiu.

I have the following linux-image packages installed:

linux-image-386
Linux kernel image on 386.

linux-image-2.6.15-27-386
Linux kernel image for version 2.6.15 on 386.

linux-image-2.6.15-26-386
Linux kernel image for version 2.6.15 on 386.

alsa-base
ALSA driver configuration files

Just so I'm sure, it's merely the '2.6.15-26-386' one I need to remove, correct?

---

### Post by aysiu on 2006-09-30
Yes. Remove linux-image-2.6.15-26-386

---

### Post by ImpelGD on 2006-09-30
Lovely job... volumes not visible on desktop, only one kernel installed, and...

> **Rumor said:**
> The file containing your screen resolutions is your xorg.conf file...
login screen uses 1152x864!

Will look at editors soon. Thanks a lot for your help and advice. :D

---

### Post by lebski88 on 2006-09-30
For HTML, PHP etc editing I would recommend Eclipse with the Aptana plug-in.

Check out [www.aptana.com](www.aptana.com) for the eclipse plug in. You can run Aptana as a stand-alone application but it's better to use Eclipse as a platform as it gives you more flexibility. Aptana is brilliant  for editing html, css and javascript. It offers code completion, highlighting and even pops up a little box telling you which commands work in which browsers. I'm totally sold on it! Aptana currently lacks PHP support (although this will be fixed in the next release I think).

Fortunately Eclipse supports something called views; if you install Aptana into Eclipse then Aptana becomes a view. As such the best thing to do is install another plug-in which properly handles PHP colouring/code assist. Then when you open a PHP file Eclipse will use that view, whearas when you open an HTML file is will use Aptana. A google search for eclipse plug-in php (or whatever else you need) will find you a whole bunch of plug-ins. They are platform independant so will work with either linux or windows.

Of course if you are feeling hardcore then you could always use vi or emacs... but the learning curve is very steap!

---

### Post by afterxleep on 2006-10-06
> **lebski88 said:**
> For HTML, PHP etc editing I would recommend Eclipse with the Aptana plug-in.

Check out [www.aptana.com](www.aptana.com) for the eclipse plug in. You can run Aptana as a stand-alone application but it's better to use Eclipse as a platform as it gives you more flexibility. Aptana is brilliant  for editing html, css and javascript. It offers code completion, highlighting and even pops up a little box telling you which commands work in which browsers. I'm totally sold on it! Aptana currently lacks PHP support (although this will be fixed in the next release I think).

Fortunately Eclipse supports something called views; if you install Aptana into Eclipse then Aptana becomes a view. As such the best thing to do is install another plug-in which properly handles PHP colouring/code assist. Then when you open a PHP file Eclipse will use that view, whearas when you open an HTML file is will use Aptana. A google search for eclipse plug-in php (or whatever else you need) will find you a whole bunch of plug-ins. They are platform independant so will work with either linux or windows.

Of course if you are feeling hardcore then you could always use vi or emacs... but the learning curve is very steap!

I just made .deb packages to ease up Aptana install on Ubuntu.  

[http://www.aptana.com/forums/viewtopic.php?t=520](http://www.aptana.com/forums/viewtopic.php?t=520)

There are a 34Mb download.  (About 160Mb less than eclipse)

---

