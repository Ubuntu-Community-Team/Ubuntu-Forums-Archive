---
title: "How to install?"
date: 2011-04-09
forum: Any Other OS
---

### Post by noxified on 2011-04-09
i have one question.i know it`s impossible to upgrade from ubuntu to debian.
so i was wandering...when installing,debian,do i need all dvd installers ?or it`s ok to have just first and after that i can finish the instalation from the internet?
Or it`s ok if i use only first CD?
i have internet by router.Thanks
Or to install from a 3.7 gb usb flash?

---

### Post by XubuRoxMySox on 2011-04-09
If you have a good internet connection and unrestricted bandwidth, you can do a [Debian Net Install]("http://www.debian.org/CD/netinst/").  It lets you pick and choose only the software you really want, avoiding alot of the cruft that most distros add in an effort to "be all things to all users."

*Without* a good internet connection, you'll want to use the DVDs and install from them.

I have done a few 'net installs and spent hours every day for weeks trying to make everything work! Wireless, display, sound, printing were all problematic and frustrating. And I'm just not that geeky (and the Debian forums don't like kids).

I stuck with it, did abuncha trial and error and finally ended up with an almost perfect Debian/Xfce mixture! But y'know what surprised me? My "perfect mixture" was very little different from Xubuntu! I mean omygosh, I had done all that work only to end up with what I already had in Xubuntu! :D

It was a good learning experience though, and it's good if **[COLOR="Purple"]"your inner geek"[/COLOR]** needs to come out and play! But for us non-geeky kids, it's nice to have all that work already done.

Debian is awesome, by the way! Super fast, rock-stable (if you *choose* Stable), and reliable. There's no better base to build from, and Canonical is wise to build Ubuntu on such an awesome foundation.

-Robin

---

### Post by kiyop on 2011-04-09
If you have a good internet connection and unrestricted bandwidth and if you have kernel loader like grub2, grub legacy, grub4dos, lilo, or syslinux and so forth, you need only kernel and initramfs to start installation.

For example, for i386,
<kernel>
[ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux](ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux)
<initramfs>
[ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz](ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz)

---

### Post by Timmer1240 on 2011-04-09
Try out Linux Mint Debian Its a very good distro been using it for a few months and really like it alot!

---

### Post by CharlesA on 2011-04-09
> **kiyop said:**
> If you have a good internet connection and unrestricted bandwidth and if you have kernel loader like grub2, grub legacy, grub4dos, lilo, or syslinux and so forth, you need only kernel and initramfs to start installation.

For example, for i386,
<kernel>
[ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux](ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux)
<initramfs>
[ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz](ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz)

That seems a bit overly complicated when the netinstall ISO is only around 150MB.

---

### Post by kiyop on 2011-04-09
Yes. It is a little difficult for newbie.;)
But, you know, the total size of "linux" and "initrd.gz" is less than 9MB and it takes shorter time to download them than to download the netinstall iso.:popcorn:
Furthermore, with linux and initrd.gz, CD-R is not necessary if some linux distribution is installed in internal HDD.

noxified may have internal HDD with grub2 and ubuntu installed.

---

### Post by Perfect Storm on 2011-04-09
Moved to Other OS/Distro Talk.

---

### Post by noxified on 2011-04-09
I have a good internet connection(6 mb/s ,real download speed)so it shouldn`t take too much time..But i wanna install it from my hdd.(other hdd)
I have a hdd with ubuntu installed(wich i`m using right now)
and i wanna install debian,not for anything specific.Just to find my "love"linux.:D
Almost everyone have a linux ,that is in love with it.I just wanna find mine.Kidding.
I wanna install ubuntu just for experimenting and stuff.I use PC for multimedia and internet only.So ubuntu it`s enough for me..But i wanna experiment.
There`s any way to put debian preinstalled to another hdd(i have 2 hdd`s)?I mean ,like i`d move ubuntu to another hdd,it would work.Same thing with debian?or could i put installer there?(everything partitioned before,so i wouldn`t be needed to delete install files) and i`ll delete them after install it`s finished.

---

### Post by noxified on 2011-04-10
anyone?

---

### Post by Elfy on 2011-04-10
> Just to find my "love"linux.If you want to look about at different distro's rather than keep installing things to hdd's have you thought about doing it with a virtual machine?


> There`s any way to put debian preinstalled to another hdd(i have 2 hdd`s)?I mean ,like i`d move ubuntu to another hdd,it would work.Same thing with debian?or could i put installer there?(everything partitioned before,so i wouldn`t be needed to delete install files) and i`ll delete them after install it`s finished.Not completely sure what you mean here, but if you mean install it to a hdd somewhere else then plug it in I'd not think that would save you anything. 

Whether you can do so now or not I'm not sure but I have in the past had an iso added to grub2 custom file so I could pick it from boot - and thus start the install from the ubuntu grub2.

---

### Post by kiyop on 2011-04-10
For example, for i386, boot with ubuntu installed in your HDD and download
<kernel>
[ftp://ftp.jaist.ac.jp/pub/Linux/Debi...ler/i386/linux]("ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux")
and
<initramfs>
[ftp://ftp.jaist.ac.jp/pub/Linux/Debi...i386/initrd.gz]("ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz")
and check md5sum value with
> 918c94b183e9a88a3fa5ca175143473c  ./netboot/debian-installer/i386/initrd.gz
12608d0f0ea9ab133a1eecdd73aff2fa  ./netboot/debian-installer/i386/linuxin
[ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/MD5SUMS](ftp://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/MD5SUMS)
by
```
cd download # or "desktop", your location for downloaded files: linux and initrd.gz
md5sum linux initrd.gz
```If md5sum values match, place them in /.
```
sudo mv linux initrd.gz /
```Add an menuentry to boot installer in /etc/grub.d/40_custom
```
gksu gedit /etc/grub.d/40_custom
```and add the following lines at the end.
```
menuentry "debian installer" {
insmod ext2
search -f --set /initrd.gz
linux /linux
initrd /initrd.gz
}
```Save and close the gedit.

Execute the following in order to add the menuentry into /boot/grub/grub.cfg.
```
sudo update-grub
```Reboot and press "shift" key to show grub menu.
Select "debian installer".
The installer will start, I hope.

---

### Post by noxified on 2011-04-12
it worked,thanks.:D

---

### Post by krapp on 2011-04-20
[http://www.debian.org/CD/live/](http://www.debian.org/CD/live/) is pretty painless... if your internet isn't too slow.

---

