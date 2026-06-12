---
title: "I just want something that works."
date: 2012-09-19
forum: Any Other OS
---

### Post by geirknappen on 2012-09-19
My fist linux distro, ubuntu 9.04, would innstall wireless drivers for me on both my laptop and desktop pc from the live cd. Ubuntu 10.04 would require me to connect a cable direct to my laptop, and then choose the needed driver from the hardwaredrivers software. Ubuntu 11.04, 11.10 and 12.04 would require me to download wireless drivers from the internet and do a complex install drivers via terminal thing.

Ubuntu 12.04 would also not work well with graphics drivers, so I decided to keep using 10.04. Something strange happened lately: [This guide]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#DVD_Playback_Capability") for making dvds work, would no longer work for me (It worked in the past). All this experience with ubuntu, made me think that I should probably try other distros. I discovered a software called unetbootin that would allow me to test various ditros on usb.

Ive tested kubuntu, xubuntu, lubuntu (12.04), debian 6 xfce, linux mint 13 mate,  bodhi 2 and fedora (beefy). I wanted to try opensuse 12.2, but that would for some reason not boot. 

What I would want is:
1 Something with nice softwarecenter 
2 Easy to install hardwaredrivers (and does work with proprietary drivers. im my case broadcom b43 and nvidia). Best scenario: installs from live usb.
3 Core functionality does not stop to work. In my case dvd playback capability.
4 Boots from live usb medium, and works with unetbootin
5 (+ I did like gnome 2)

My guess is that there is no such thing as what I just described, and that 10.04 is my best alternative at the moment, although the dvd issue exist.

---

### Post by MckayKnight on 2012-09-19
Ubuntu 12.04.1 LTS should do all what you have mentioned a long with newer packages and a newer kernel.

1. Ubuntu has an easy to use Software Center.
2. By default on a fresh install Ubuntu should detect your nVidia driver and prompt you to install a proprietary driver.
3. As far as I know Ubuntu 12.04.1 has been pretty much stable for the core area. If you want DVD playback you can install VLC a long with Ubuntu's Restricted Extras.
4. Ubuntu can boot from a USB by using Startup Disk Creator.
5. Gnome 2 still exist but they name changed due to copyright issues it's official name is called: MATE, [http://mate-desktop.org/](http://mate-desktop.org/)

If you're having wireless driver issues or just wireless problems a 'Networking and Wireless' section exist on these forums.

You can also check out this link: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Happy camping. :)

---

### Post by BBQdave on 2012-09-19
> **geirknappen said:**
> My fist linux distro, ubuntu 9.04, would innstall wireless drivers for me on both my laptop and desktop pc from the live cd. Ubuntu 10.04 would require me to connect a cable direct to my laptop, and then choose the needed driver from the hardwaredrivers software. Ubuntu 11.04, 11.10 and 12.04 would require me to download wireless drivers from the internet and do a complex install drivers via terminal thing.

Give the list of OS's on presumably the same hardware, older hardware, I would recommend Fedora 16 Xfce.

I migrated from Debian 6 - Gnome 2 on older hardware, to F16 Xfce on old and new hardware. F16 Xfce worked out of the box :D

---

### Post by geirknappen on 2012-09-21
> **MckayKnight said:**
> Ubuntu 12.04.1 LTS should do all what you have mentioned a long with newer packages and a newer kernel.

1. Ubuntu has an easy to use Software Center.
2. By default on a fresh install Ubuntu should detect your nVidia driver and prompt you to install a proprietary driver.
3. As far as I know Ubuntu 12.04.1 has been pretty much stable for the core area. If you want DVD playback you can install VLC a long with Ubuntu's Restricted Extras.
4. Ubuntu can boot from a USB by using Startup Disk Creator.
5. Gnome 2 still exist but they name changed due to copyright issues it's official name is called: MATE, [http://mate-desktop.org/](http://mate-desktop.org/)

If you're having wireless driver issues or just wireless problems a 'Networking and Wireless' section exist on these forums.

You can also check out this link: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Happy camping. :)

The thing is thay I've become superlazy when It comes to doing any manual fixes. I know what to do to make wireless work, but such things take time. When I tried to install nvidia driver (recommended version)... It didn't go that well (screen went black). I could use ubuntu without proprietary nvidia driver, but for some reason, I suspect that it would not be wise. I don't want to kill my computer.

+ I've only got 1 gb memory on my laptop. How much memory does ubuntu mate  consume on idle? And mate desktop environment is maintained only by one guy? My guess is that if I had to go for anything buntu, Ir would gave to be xubuntu.

---

### Post by geirknappen on 2012-09-21
> **BBQdave said:**
> Give the list of OS's on presumably the same hardware, older hardware, I would recommend Fedora 16 Xfce.

I migrated from Debian 6 - Gnome 2 on older hardware, to F16 Xfce on old and new hardware. F16 Xfce worked out of the box :D

Hmmm... Both debian and fedora seemed to me to be intended for someone with more technical computerskills than mine. I tried the gnome 3 desktop fedora, and didn't like it (and therefore did not test it much). Perhaps the xfce version is better.

---

### Post by QIII on 2012-09-21
I have an Xubuntu Quantal machine running around on around 280MB with conky and Compiz going.  Probably more with a proprietary video driver.

---

### Post by geirknappen on 2012-09-22
> **QIII said:**
> I have an Xubuntu Quantal machine running around on around 280MB with conky and Compiz going.  Probably more with a proprietary video driver.

Hmmm... It almost sound like a confession that the xubuntu 12.04 is not living up to standards, and that I should wait for a future release. 
(by the way... The 64 bit desktop point release xubuntu 12.04.1 did not work with unetbootin 581)

---

### Post by QIII on 2012-09-22
I don't know what that would be confessing beyond the fact that I have more cool stuff running on my daily driver than I do on my test machine.

---

### Post by NormanFLinux on 2012-09-23
> **geirknappen said:**
> Hmmm... Both debian and fedora seemed to me to be intended for someone with more technical computerskills than mine. I tried the gnome 3 desktop fedora, and didn't like it (and therefore did not test it much). Perhaps the xfce version is better.

With Fedora, the autoten script can painlessly install everything you need to get it usable. Installing EasyLife takes care of configuring a Fedora installation to an optimal state. If that's too much work, a Fedora mix like Funduntu or Koraa would perhaps be better suited to your needs.

---

### Post by black veils on 2012-09-24
linux mint 13 xfce might be the closest to what you are wanting. it is supposed to have easier access to codecs and drivers (repositories added already).

locking software versions like the kernel, is a good idea if you want to try and prevent breakage.

settings updates to only be important security updates. though i find the mint update manager to be convoluted in the actual management of that process, i dont think it works.

---

### Post by rybnik on 2012-09-24
> **black veils said:**
> linux mint 13 xfce might be the closest to what you are wanting. it is supposed to have easier access to codecs and drivers (repositories added already).


I agree with you on Mint, but (out of curiosity) why do you say xfce?  Is the xfce version (or kde version, for that matter) different from the regular version in more ways than just the desktop environment?

Again, just curious... thanks!

---

### Post by black veils on 2012-09-24
> **rybnik said:**
> I agree with you on Mint, but (out of curiosity) why do you say xfce?  Is the xfce version (or kde version, for that matter) different from the regular version in more ways than just the desktop environment?

Again, just curious... thanks!

a point that the original poster made was they liked gnome2, and xfce has the same sort of configuration options.

also they seemed to be concerned with breakage, and i figured xfce doesnt have heavy graphical requirements, so that might be relevant.

thats it really.

to answer your other question, i dont think there is any difference, except for desktops, but that in itself is a big difference.

---

### Post by rybnik on 2012-09-24
^I see.  Thanks.

---

