---
title: "VMware - network troubles"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Anicka on 2007-05-03
I have a strange problem with my VMware set-up. I have Feisty as a guest under Vmware workstation (5.5.3) in XP. In order to access the internet, I have found that I need to use NAT rather than bridged network. The connection Ubuntu <-> www works without problems, download-rate at 2-4 Mb/s, but Ubuntu <-> shared files from XP has a rate of close to zero.

I'm trying to copy files from my Ubuntu to a shared folder.Every once in a while a data-pulse gets through, but most of the time the network in at zero. At the same time vmware-guestd is overloading the CPU.

I have tried to set up vmxnet as suggested in this thread [http://ubuntuforums.org/showthread.php?t=412562](http://ubuntuforums.org/showthread.php?t=412562) as post #15, but no success. The connection is still pcnet32 (eth1). When I run "sudo ifconfig eth0 up" I get "eth0: ERROR while getting interface flags: No such device".

I need an at least semi-nice-ish connection between my system, so any increase of speed is appreciated.

---

### Post by Anicka on 2007-05-04
](*,)  bumping this thread. This is a screen shot of the system manager from yesterday when I was copying files from Ubuntu to Windows.

---

### Post by body-snatch-her on 2007-05-07
Same problem here! vmxnet compiles fine but won't load! Probably a simple ( read: newbie) problem but I can't figure it out...

---

### Post by veloce on 2007-05-08
> **Anicka said:**
> I have a strange problem with my VMware set-up. I have Feisty as a guest under Vmware workstation (5.5.3) in XP. In order to access the internet, I have found that I need to use NAT rather than bridged network. The connection Ubuntu <-> www works without problems, download-rate at 2-4 Mb/s, but Ubuntu <-> shared files from XP has a rate of close to zero.

I'm trying to copy files from my Ubuntu to a shared folder.Every once in a while a data-pulse gets through, but most of the time the network in at zero. At the same time vmware-guestd is overloading the CPU.

I have tried to set up vmxnet as suggested in this thread [http://ubuntuforums.org/showthread.php?t=412562](http://ubuntuforums.org/showthread.php?t=412562) as post #15, but no success. The connection is still pcnet32 (eth1). When I run "sudo ifconfig eth0 up" I get "eth0: ERROR while getting interface flags: No such device".

I need an at least semi-nice-ish connection between my system, so any increase of speed is appreciated.

I suggest you set up a second virtual network as "host only".  If you are using NAT then all your communications between the host and vm are broadcasting over your physical network.

---

