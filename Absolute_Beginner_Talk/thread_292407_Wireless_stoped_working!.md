---
title: "Wireless stoped working!"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2006-11-03
My computer wont connect to both types of networks, at first i thought it might be the routers or my computer but i just loaded off the CD and it works fine... im guessing something happened on my instaled version and it wont connect to any of my networks...can anyone help me with this, im thinking like reinstall it or confiure my network manager, something of that sorts,](*,)](*,)

sorry for the long explanation, thanks in advance 8)

---

### Post by jimrz on 2006-11-03
> **Hmarroqu said:**
> My computer wont connect to both types of networks, at first i thought it might be the routers or my computer but i just loaded off the CD and it works fine... im guessing something happened on my instaled version and it wont connect to any of my networks...can anyone help me with this, im thinking like reinstall it or confiure my network manager, something of that sorts,](*,)](*,)

sorry for the long explanation, thanks in advance 8)

need a little more info. have you installed network-manager? if so you need to edit /etc/network/interfaces and comment out everything except 

```
auto lo
iface lo inet loopback
```

in order for network-manager to "see" your connections, since it ignores anything that is active in "interfaces"

---

### Post by Hmarroqu on 2006-11-05
I have the network manager that comes with the installation, it rekognizes my networks it just will not connect, it does with the live CD tho as i mentioned before, once again im on the CD right now and im going to use the code u posted. THANKs :)

---

### Post by jimrz on 2006-11-05
> **Hmarroqu said:**
> I have the network manager that comes with the installation, it rekognizes my networks it just will not connect, it does with the live CD tho as i mentioned before, once again im on the CD right now and im going to use the code u posted. THANKs :)

From Synaptic install 

```
network-manager + network-manager-gnome
```

then do the instrucion above.

then restart gnome and the nm applet should be in your top panel (you may see 2 networking icons, if so you can safely remove the original from the panel after configuring network-manager and confirming that it is working)

---

### Post by Hmarroqu on 2006-11-05
> **jimrz said:**
> need a little more info. have you installed network-manager? if so you need to edit /etc/network/interfaces and comment out everything except 

```
auto lo
iface lo inet loopback
```in order for network-manager to "see" your connections, since it ignores anything that is active in "interfaces"

The edit part, etc/network/interfaces, is that a directory to a file? sorry im pretty dumb.:-?:-?

NEVER MIND,, sorry i came to my senses, im working on editing it right now :)

---

### Post by jimrz on 2006-11-05
> **Hmarroqu said:**
> The edit part, etc/network/interfaces, is that a directory to a file? sorry im pretty dumb.:-?:-?

its a file. do this from terminal

```
sudo cp etc/network/interfaces etc/network/interfaces-original
```

this makes a backup of your current file (ALWAYS a good thing). then

```
sudo gedit etc/network/interfaces
```

and comment out all except auto lo, as described above

---

### Post by Hmarroqu on 2006-11-05
worked out GREAT, thanks alot! im so much happier now!

---

### Post by jimrz on 2006-11-05
> **Hmarroqu said:**
> worked out GREAT, thanks alot! im so much happier now!

:) you are more than welcome

stick with it ... you will learn much and have lots of fun

i still consider myself a newbie, but thanks to all the folks on these forums i am now able to pass along what i have acquired by following their advice. this is, in many ways, the best thing about ubuntu.

enjoy

---

### Post by capoyeti on 2006-11-05
Hi - I saw this original post and thought my problems would be solved too... but - I'd already commented out all except for 

```

auto lo
iface lo inet loopback
```
in the /etc/network/interfaces.

I'm using Edgy, and after having my system (Beryl, Wifi etc, etc) all working  happily, I installed the latest "linux-restricted-modules-common" security update.
This broke my xorg.conf and after fixing this (by manually recompiling the Nvidia kernel, I got my X server working again

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9625-pkg1.run
sudo /etc/init.d/gdm start
```
but still no wifi :-(

my machine sees the network card

```
chad@beastly:~$ lspci
...
...
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
...
```

but network-manager only sees the wired ethernet card.

(I have uninstalled (--purge) network-manager and network-manager-gnome and then reinstalled after editing the /etc/network/interfaces file

Any suggestions?

---

### Post by jimrz on 2006-11-05
> **capoyeti said:**
> Hi - I saw this original post and thought my problems would be solved too... but - I'd already commented out all except for 

```

auto lo
iface lo inet loopback
```
in the /etc/network/interfaces.

I'm using Edgy, and after having my system (Beryl, Wifi etc, etc) all working  happily, I installed the latest "linux-restricted-modules-common" security update.
This broke my xorg.conf and after fixing this (by manually recompiling the Nvidia kernel, I got my X server working again

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9625-pkg1.run
sudo /etc/init.d/gdm start
```
but still no wifi :-(

my machine sees the network card

```
chad@beastly:~$ lspci
...
...
02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
...
```

but network-manager only sees the wired ethernet card.

(I have uninstalled (--purge) network-manager and network-manager-gnome and then reinstalled after editing the /etc/network/interfaces file

Any suggestions?

i don't think nm is your problem, but rather the changes to madwifi in the new kernel in edgy. i have held off installing edgy in my laptop for that very reason. search these forums for "atheros" + "your card" and you will get an idea of where you stand. you may be able to get it working using ndis-wrapper.

i never could get mine on the edgy "live cd's" up to rc, but the final release one did work (sort of). on the final, i could get to the web ok, but could not connect }or even ping) my router or any other box on my network. anyway dapper is doing just fine on my laptop, so i am holding off till either the problem is resolved in edgy or possibly even wait for fiesty before changing it over.

---

### Post by capoyeti on 2006-11-05
thanks for the quick response..


problem is, wifi and nm were working GREAT before the new package was installed...

I went to Edgy on my desktop (this machine) from the start...

(laptop went the dapper-> edgy route and is happy with nm and wifi on Edgy)

so basically - I undid the changes that the new package made to my graphics/display setup by rebuilding the Nvidia kernel, but now want to do the same for my wifi i.e. 'undo' the changes made by installing 

linux-restricted-modules-common

---

### Post by jimrz on 2006-11-05
> **capoyeti said:**
> thanks for the quick response..


problem is, wifi and nm were working GREAT before the new package was installed...

I went to Edgy on my desktop (this machine) from the start...

(laptop went the dapper-> edgy route and is happy with nm and wifi on Edgy)

so basically - I undid the changes that the new package made to my graphics/display setup by rebuilding the Nvidia kernel, but now want to do the same for my wifi i.e. 'undo' the changes made by installing 

linux-restricted-modules-common

i'm not sure, but i think there is a way to revert via synaptic (or at least via cli). think i did it via cli when a dapper update broke X, but do not remember the proceedure except that you had to have the exact name of the previous version. if you have the edgy "alternate" cd ("desktop" may as well) it will have the .deb for the previous one on it. you could remove the new one via synaptic, then install the old deb, and then go back to synaptic and "lock version" on it, at least till you are sure a new one is out that will work for you. and of course, you can always search these forums for other / better solutions

---

### Post by Hmarroqu on 2006-11-20
This is an older post here so im taking a shot in the dark...everything worked out great with my previous problem but now i face another annoying problem...i turned of my network hardware on my laptop and now, when i connect to my houses network, the connection is extremely laggy and sometimes just gives up, im talking worse than 56k here.  Any ideas?

Thanks in advance!

---

