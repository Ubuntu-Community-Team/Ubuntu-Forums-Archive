---
title: "Update manager"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Hookheathen on 2008-02-05
Hello,

I was downloading a deb package when the Internet connection halted. I did not try again to download the package. I now get the following alert when using update manager to download normal Ubuntu updates:-

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

i have tried following this instruction but without success. Help please!!!

---

### Post by philinux on 2008-02-05
Make sure you use 

sudo 
in front of that command.

---

### Post by steveneddy on 2008-02-05
run in terminal

```

sudo dpkg --configure -a

```

to correct the issue.

---

### Post by jrib on 2008-02-05
Paste the output you get when you run ```
sudo dpkg --configure -a
```

---

### Post by mygor on 2008-02-05
I have a similar problem. the only difference is that the update manager locked up on install

here is the output from dpgk"


mygor@mygor-desktop:~$ sudo dpkg --configure -a
[sudo] password for mygor:
Setting up python-bittorrent (3.4.2-11ubuntu3~7.10) ...

Setting up language-pack-en (1:7.10+20071120) ...
Setting up apturl (0.1ubuntu2) ...

Setting up capplets-data (1:2.20.1-0ubuntu1) ...

Setting up libssl0.9.8 (0.9.8e-5ubuntu3.1) ...

Setting up avahi-autoipd (0.6.20-2ubuntu3.2) ...

Setting up bittorrent (3.4.2-11ubuntu3~7.10) ...

Setting up linux-image-2.6.22-14-generic (2.6.22-14.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up app-install-data-commercial (8.4) ...
Caching application data...
Skipped k3dsurf.desktop: does not include a menu name
Generating mime/codec maps...

Setting up libperl5.8 (5.8.8-7ubuntu3.1) ...

Setting up libdb4.4 (4.4.20-8.1ubuntu3.1) ...
Setting up libavahi-common-data (0.6.20-2ubuntu3.2) ...
Setting up libavahi-common3 (0.6.20-2ubuntu3.2) ...

Setting up libisc32 (1:9.4.1-P1-3ubuntu1) ...

Setting up libisccc30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libc6-i686 (2.6.1-1ubuntu10) ...

Setting up language-pack-gnome-en (1:7.10+20071120) ...
Setting up libdns32 (1:9.4.1-P1-3ubuntu1) ...

Setting up openssh-client (1:4.6p1-5ubuntu0.1) ...

dpkg: error processing libpng12-0 (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up libisccfg30 (1:9.4.1-P1-3ubuntu1) ...

Setting up liblwres30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libbind9-30 (1:9.4.1-P1-3ubuntu1) ...

Setting up libavahi-core5 (0.6.20-2ubuntu3.2) ...

Setting up avahi-daemon (0.6.20-2ubuntu3.2) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Avahi mDNS/DNS-SD Daemon avahi-daemon                        [ OK ] 

Setting up bind9-host (1:9.4.1-P1-3ubuntu1) ...
Setting up dnsutils (1:9.4.1-P1-3ubuntu1) ...

Setting up perl-modules (5.8.8-7ubuntu3.1) ...
Setting up perl (5.8.8-7ubuntu3.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libpng12-0
mygor@mygor-desktop:~$  "


What can I do to fix this?

---

### Post by stoodleysnow on 2008-02-05
How much RAM do you have?
What sort of CPU?

---

### Post by mygor on 2008-02-05
I have an AMD XP 1600 with 512mb of DDR ram MSI KT 266 Pro mainboard.
I have run Memtest on this system with no errors.

I have just solved the problem. I installed this 7,10 OS last night. When I restarted the system I ran the updater, it had to download 230+ MB. So I let it run and went to bed. When I woke up I found it locked up( the updater not the system). I think that the energy saving feature may have turned off the hard drive during the installation of the updates. The updates had already been downloaded so I just reran the updater. It seems to have corrected this problem.

Thanks for the help!

---

### Post by Hookheathen on 2008-02-05
Thanks for advice, here is the output................

michael@michael-laptop:~$ sudo dpkg -configure -a
Password:
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-laptop:~$ sudo dpkg configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-laptop:~$

---

### Post by mygor on 2008-02-05
> **Hookheathen said:**
> Thanks for advice, here is the output................

michael@michael-laptop:~$ sudo dpkg -configure -a
Password:
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-laptop:~$ sudo dpkg configure -a
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-laptop:~$

Your command line is wrong. Copy and paste this command.


sudo dpkg --configure -a

this will get you the correct output.

---

### Post by Hookheathen on 2008-02-05
Er, yes. I was under the impression I was capable of telling the difference when typing " -a and -o". I thought that  somehow I made this mistake but no, I reentered -a a few times but it obstinately came back again  "dpkg: unknown option -o

Interesting!

---

### Post by mygor on 2008-02-05
> **Hookheathen said:**
> Er, yes. I was under the impression I was capable of telling the difference when typing " -a and -o". I thought that  somehow I made this mistake but no, I reentered -a a few times but it obstinately came back again  "dpkg: unknown option -o

Interesting!

Your command line should have 2 dash marks in front of the word configure. I think that is the problem.

sudo dpkg --configure -a   Is what it is supposed to say. But yours reads

sudo dpkg -configure -a  Try changing that!

---

### Post by Hookheathen on 2008-02-07
Many thanks Mygor, after a couple of worrying screens saying Synaptic was bust and two reboots later, all seems well and subsequent notified updates have been downloaded and seemingly installed without further bother.

---

