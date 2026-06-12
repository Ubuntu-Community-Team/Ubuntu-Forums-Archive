---
title: "zv6000 and breezy... again"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by greenerpole on 2005-12-08
All apologizes for this thread which tackles again the overspoken zv6000 issue. I went through dozens of forums and tried to read thousands of pages, manuals, guides... but as i am a total newbie (who wanted to go to linux for so long but just dared a couple of days ago), I did understand where some problems were, but not always how to fix them.

****
My laptop : HP Pavilion zv6000
15.4" widescreen monitor with brightview
AMD 64 3800+
512MB RAM (one stick)
ATI Radeon Xpress 200M w/128MB RAM
Wireless B/G combo card (Broadcom chip)
4 USB 2.0 ports and 1 firewire port
80GB HDD
DVD +-R/RW (DL)
digital media reader

****
I downloaded and burnt both Live and Install on Ubuntu DL page (ubuntu-5.10-live-amd64.iso, and ubuntu-5.10-install-amd64.iso) 

****
Boot on the Live CD :
1. At the first prompt, pressing directly Enter led me to a black screen (and a computer impossible to shut down by some other way than unplugging the battery)
2. This was solved (thx to the forum) by typing at the "boot" prompt :```
 live vga=771 noapci nolapci noapic nolapic
```
3. Then everything went on quietly, language, keyboard, hardware detection...
4. Next, there is this list where the installer is checking a few points, noting 'ok' or 'failed', in front of each point
5. And then, black screen, the cursor disappears, the cd-reading noise vanishes... and no way to turn the laptop off in a clean way (to my knowledge)

Question : what is the problem, here ? what can i do ?

Actually, before to go further in my installation, using the Install disc (partitioning my disk, deleting winxp, and all that stuff), I would be sure to be able to install a proper Ubuntu on the computer... which is not the case for now.

Thanks for your help, I am really looking forward to be an Ubuntu addict.

---

### Post by greenerpole on 2005-12-09
ok, i gave up with the Live CD, and decided to try a real Installation.

Before starting, I erased the native winXP and reinstalled it on a dedicated NTFS 20Go partition. Which lets 60Go for Ubuntu.

1. Booted on Install CD (5.10 amd64) typing when first prompted : ```
linux vga=771 noapic nolapic
```. 
2. Specified language, location, keyboard ; detected hardware ; scanned CD ; loaded additional elements
3. The DHCP network configuration failed (told it to do it later), which is normal as I'm not connected
4. Gave it a name
5. Let it manage the Free Space to create its own partitions (\ and swap, if i remember well), and create its ext3 file system on the disk
6. Installed the base system (ok)
7. Copying remaining packages is the crucial step : freezed three times in a row (1st at 70%-Nautilus, 2nd at 28%-hwdata, 3rd at 89%-libvte-common)...

Does anyone have any idea about this problem, and how I can solve it ?

---

### Post by greenerpole on 2005-12-09
... After a dozen tries in a row to install Ubuntu with the Breezy Install CD, and the very same dozen frozen screens at the same step ("copying remaining packages"), I gave up with Breezy.

Started back with Hoary, and my zv6000 liked it very much. With the same strategy than with Breezy, the installation went (this time) alright until the welcome menu (where the user name is prompted). After providing username and password, the screen freezes.

Rebooting on Recovery Mode, edited xorg.conf with ```
sudo pico /etc/X11/xorg.conf
``` and in the Device cell where ATI driver is summoned, add : ```
Option "noaccel"
``` (saving with Ctrl+X then "Y")

Then, restarted the graphical interface with : ```
sudo /etc/init.d/gdm restart
```

And now, I am so happy, writing from my brand new Ubuntu system:D 

Ok, still stuff to do to get everything working (especially the ATI...)

---

### Post by debernardis on 2005-12-10
I have a zv6000, too, with Broadband wi-fi card. One thing I found necessary in order to make it work is **acpi=off** in the boot options. Otherwise, it randomly crashes when using wlan.

---

### Post by greenerpole on 2005-12-10
Are you on Breezy or Hoary ?
Did you manage to go through the installation ?

---

### Post by debernardis on 2005-12-10
Breezy Ubuntu, no problems in installation except the need of NoAccel to get X working.
ACPI=OFF makes my wi-fi card work without crashes (which were abundant even with ACPI=NOIRQ), but spoiled battery indication (which BTW disappeared after some fiddling), and I don't know if I were good at activating APM instead.

---

### Post by debernardis on 2005-12-11
I am very very happy (at least in the present moment).
You know, ACPI=OFF made my ndiswrapper+Broadcomm wi-fi card work at the expenses of battery indicator. APM could not be brought to life by APM=ON in the grub menu.lst.

Well but reading ndiswrapper.sourceforge.net docs I grasped it was a problem of IRQ indeed, and what I had to do was to find a more complex spell for my kernel boot.

Being a newbie in tuxology my decision was to google here and there for kernel boot magic spells to find one that seemed fit. And [here]("http://forums.fedoraforum.org/showthread.php?t=85403") the spell seemed to do very directive things to acpi and irqs!

Feeling like Harry Potter, I edited my grub line, adding:
> **acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq**
and it worked indeed!

Now I am posting from my Pavilion ZV6278EA, internal wi-fi enabled, battery indicator enabled, with no crashes (up to now); still no graphic card acceleration - that is the next game.
I have no clue on what that magic spell technically does in the belly of my kernel, but I'll discover (later) what words are the really magic ones by selective elimination. I'd really appreciate an explanation, however, from a wise somebody.

---

### Post by debernardis on 2005-12-11
Oh well. Now I managed to update the Ati Radeon Xpress 200 driver by religiously following the well-known [howto]("http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589") , BUT...

...it's very important to notice that after 

```
sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
```

no .deb packages are apparently produced in the working directory. They are to be found in /tmp , as described in one post adventurously found inside the 45 pages of comments to the howto.

After that everything went fine and now glxgears rotate so nicely...:KS

---

### Post by debernardis on 2005-12-12
Suspend to Ram was easy to implement as described [here]("http://www.ubuntuforums.org/showthread.php?t=76062&highlight=suspend+hibernate").
Editing /etc/default/acpi-support and uncommenting **ACPI_SLEEP=true** was enough.
Now I have to grasp how to trigger "suspend to ram" when closing lid; and hibernation (suspend to hd) is the next.

---

### Post by debernardis on 2005-12-16
Bluetooth send/receive files installed thanks to [this article]("http://doc.gwos.org/index.php/GnomeBlueTooth").
Would be nice to have [p3nfs]("http://www.koeniglich.de/p3nfs.html") working to connect to my Nokia 9500...

In the meantime hibernation worked with no tweaks.

---

### Post by debernardis on 2005-12-18
To get the best functionality for bluetooth, the right move was to turn to KDE 3.5 as described [elsewhere ]("http://kubuntu.org/announcements/kde-35.php"). In Kde I found utilities to directly open the file system of my nokia 9500 (opening Konqueror and going to bluetooth:/ was enough).

Now I can choose between Gnome and KDE at time of login... nice.

---

### Post by greenerpole on 2005-12-18
Woooh, you seem quite advanced now. 

Finally, after say 10 unsuccessful tries in installing Breezy, it surprisingly worked. It worries me a little bit that installation could be so random.

Haven't got time to go through the ATI driver installation, but so far I don't really feel the need of that.
I am more concerned about not managing to set up the wifi. I checked on winXP, it works, so it is not a hardware matter.
Then I followed the HOWTO[HTML]http://www.ubuntuforums.org/showthread.php?t=25683[/HTML], and I added to the /boot/grub/menu.lst instead of 
```
kernel /boot/vmlinuz root=/dev/hda2 ro vga=771 quiet splash no_timer_check
```
this new code (I owe from your post, debernardis)
```
kernel /boot/vmlinuz root=/dev/hda2 ro vga=771 quiet splash acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq no_timer_check
```

Then rebooting and even trying ```
sudo modprobe ndiswrapper
```, still no light for the wifi card, and nothing appearing in the 'Networking' menu (in System->Administration). 

Here I am. Any ideas ?

---

### Post by debernardis on 2005-12-19
If ndiswrapper seems not to be there, just get rid of the installation and start over like in [http://www.ubuntuforums.org/showpost.php?p=571571&postcount=34](http://www.ubuntuforums.org/showpost.php?p=571571&postcount=34) :
```

sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```
As described above, try to ```
sudo apt-get install ndisgtk
``` which installs a GUI front-end to ndiswrapper driver setting. 
After installing you are going to find a "Wireless network drivers" icon in one of your gnome menus (at present, working with kde, I don't know where exactly, but you can start it also with sudo ndisgtk).
You'll have the chance first to install the .inf driver (I am using bcmwl5a.inf taken from the pre-installed winxp - in a pavilion zv6278e, go to c:\swsetup\wlan and there take bcmwl5.inf , bcmwl5a.inf and bcmwl.sys, then copy them somewhere in your ubuntu file system, i.e. in ~/Desktop, then select the copied .inf file in ndisgtk); if everything is OK it will tell you "hardware present".
Then, you'll "configure network" (the second button) and there you will have to activate WLAN0 and give the ESSID (wi-fi network name) and other details.

---

### Post by greenerpole on 2005-12-28
Guess what ? 
I'm still in trouble...

1. I tried your tricks with ndisgtk. I first removed all the ndiswrapper history, then got the ndisgtk stuff installed. Everything went alright, and it told me, as you mentionned, that "Hardware is present" (at last... I was starting to doubt it). But then, pushing the "Configure"  button, I see the modem, I see the ethernet, but I don't see anything looking like wlan0. Rebooting, or trying ```
sudo modprobe ndiswrapper
```didn't help much.

2. So I told myself that maybe the problem was somewhere else. There is still so much to be done to get this computer working. First, the clock, which is running twice too fast. I read a lot of things about it, and decided to add ```
noapic
``` in the kernel line of /boot/grub/menu.lst. This worked. The clock came to a good pace.

3. About this very same kernel line in menu.lst : do you have an idea, even the slightest, about the meaning of all the options we keep on adding ? For the moment, I have : ```
quiet splash noapic acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq no_timer_check
```
I tried to downgrade to ```
quiet splash noapic irqpoll routeirq 
``` just to try (I am still a perfect beginner), but now it seems that it freezes when I let it alone too long (as if the screensaver could not be loaded...).

I still don't really know what to do... Well, quite a lot of steps to climb before even thinking about tackling the ATI driver problem.

---

### Post by debernardis on 2005-12-30
[QUOTE=greenerpole]3. About this very same kernel line in menu.lst : do you have an idea, even the slightest, about the meaning of all the options we keep on adding ? For the moment, I have : ```
quiet splash noapic acpi=strict acpi=noirq pci=biosirq pci=nosort irqpoll routeirq no_timer_check
```
[/QUOTE]

You told that: I must confess I have no idea of the meaning of all those options.
Not that I didn't try googling but with scarce satisfaction.
Only Mr.Torvalds could help us.

For the ndiswrapper problem:
I have the 1.1-4ubuntu2 version. Is that yours too?
Try with ```
cat /var/cache/modass/ndiswrapper-source.avail_version

```

Also, look at the output of my "locate ndiswrapper" command (do it after an "updatedb"):

```

/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper
/etc/ndiswrapper/bcmwl5a
/etc/ndiswrapper/bcmwl5a/14E4:4301:103C:12F3.5.conf
/etc/ndiswrapper/bcmwl5a/bcmwl5.sys
/etc/ndiswrapper/bcmwl5a/14E4:4320:0E11:00E7.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4320:103C:12F4.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4320:103C:12F8.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4320:103C:12FA.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4320:103C:12FB.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4324:103C:12F9.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4324:103C:12FC.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4324:103C:12FD.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4318:103C:1355.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4318:103C:1356.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4318:103C:1357.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4319:103C:1358.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4319:103C:1359.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4319:103C:135A.5.conf
/etc/ndiswrapper/bcmwl5a/bcmwl5a.inf
/etc/ndiswrapper/bcmwl5a/14E4:4318.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4320.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4319.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4324.5.conf
/etc/ndiswrapper/bcmwl5a/14E4:4301.5.conf
/var/lib/dpkg/info/ndiswrapper-utils.postinst
/var/lib/dpkg/info/ndiswrapper-utils.list
/var/lib/dpkg/info/ndiswrapper-utils.md5sums
/var/lib/dpkg/info/ndiswrapper-source.md5sums
/var/lib/dpkg/info/ndiswrapper-source.list
/var/lib/dpkg/info/ndiswrapper-modules-2.6.12-10-386.postinst
/var/lib/dpkg/info/ndiswrapper-modules-2.6.12-10-386.list
/var/lib/dpkg/info/ndiswrapper-modules-2.6.12-10-386.md5sums
/var/cache/modass/ndiswrapper-source.buildlog.2.6.12-10-386.1134319516
/var/cache/modass/ndiswrapper-source.buildstate.2.6.12-10-386
/var/cache/modass/ndiswrapper-source.cur_version
/var/cache/modass/ndiswrapper-source.avail_version
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.12-10-386/misc/ndiswrapper.ko
/usr/share/doc/ndiswrapper-utils
/usr/share/doc/ndiswrapper-utils/README.Debian
/usr/share/doc/ndiswrapper-utils/README
/usr/share/doc/ndiswrapper-utils/AUTHORS
/usr/share/doc/ndiswrapper-utils/changelog.gz
/usr/share/doc/ndiswrapper-utils/copyright
/usr/share/doc/ndiswrapper-utils/changelog.Debian.gz
/usr/share/doc/ndiswrapper-source
/usr/share/doc/ndiswrapper-source/README.Debian
/usr/share/doc/ndiswrapper-source/README
/usr/share/doc/ndiswrapper-source/AUTHORS
/usr/share/doc/ndiswrapper-source/changelog.gz
/usr/share/doc/ndiswrapper-source/copyright
/usr/share/doc/ndiswrapper-source/changelog.Debian.gz
/usr/share/doc/ndiswrapper-modules-2.6.12-10-386
/usr/share/doc/ndiswrapper-modules-2.6.12-10-386/changelog.Debian.gz
/usr/share/doc/ndiswrapper-modules-2.6.12-10-386/copyright
/usr/share/man/man8/ndiswrapper.8.gz
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-buginfo
/usr/src/linux-headers-2.6.12-10-386/include/config/ndiswrapper
/usr/src/linux-headers-2.6.12-10-386/include/config/ndiswrapper/module.h
/usr/src/linux-headers-2.6.12-10/include/config/ndiswrapper.h
/usr/src/linux-headers-2.6.12-10/drivers/net/ndiswrapper
/usr/src/linux-headers-2.6.12-10/drivers/net/ndiswrapper/Makefile
/usr/src/modules/ndiswrapper
/usr/src/modules/ndiswrapper/debian
/usr/src/modules/ndiswrapper/debian/changelog
/usr/src/modules/ndiswrapper/debian/compat
/usr/src/modules/ndiswrapper/debian/copyright
/usr/src/modules/ndiswrapper/debian/control.modules.in
/usr/src/modules/ndiswrapper/debian/postinst.modules.in
/usr/src/modules/ndiswrapper/debian/rules
/usr/src/modules/ndiswrapper/debian/control
/usr/src/modules/ndiswrapper/debian/postinst
/usr/src/modules/ndiswrapper/debian/control.backup
/usr/src/modules/ndiswrapper/debian/postinst.backup
/usr/src/modules/ndiswrapper/Makefile
/usr/src/modules/ndiswrapper/divdi3.c
/usr/src/modules/ndiswrapper/hal.c
/usr/src/modules/ndiswrapper/iw_ndis.c
/usr/src/modules/ndiswrapper/iw_ndis.h
/usr/src/modules/ndiswrapper/loader.c
/usr/src/modules/ndiswrapper/loader.h
/usr/src/modules/ndiswrapper/longlong.h
/usr/src/modules/ndiswrapper/misc_funcs.c
/usr/src/modules/ndiswrapper/ndis.c
/usr/src/modules/ndiswrapper/ndis.h
/usr/src/modules/ndiswrapper/ndiswrapper.h
/usr/src/modules/ndiswrapper/ntoskernel.c
/usr/src/modules/ndiswrapper/ntoskernel.h
/usr/src/modules/ndiswrapper/pe_linker.c
/usr/src/modules/ndiswrapper/pe_linker.h
/usr/src/modules/ndiswrapper/proc.c
/usr/src/modules/ndiswrapper/usb.c
/usr/src/modules/ndiswrapper/usb.h
/usr/src/modules/ndiswrapper/winnt_types.h
/usr/src/modules/ndiswrapper/wrapper.c
/usr/src/modules/ndiswrapper/wrapper.h
/usr/src/modules/ndiswrapper/x86_64_stubs.S
/usr/src/modules/ndiswrapper/INSTALL
/usr/src/modules/ndiswrapper/version
/usr/src/modules/ndiswrapper/ndis_exports.h
/usr/src/modules/ndiswrapper/hal_exports.h
/usr/src/modules/ndiswrapper/ntoskernel_exports.h
/usr/src/modules/ndiswrapper/misc_funcs_exports.h
/usr/src/modules/ndiswrapper/usb_exports.h
/usr/src/modules/ndiswrapper/wrapper_exports.h
/usr/src/ndiswrapper-source.tar.bz2
/usr/src/ndiswrapper-modules-2.6.12-10-386_1.1-4ubuntu2+2.6.12-10.24_i386.deb
/dev/.udevdb/class@misc@ndiswrapper

```

Is yours like that? I don't know how to help you, I am a noob too :confused:

---

