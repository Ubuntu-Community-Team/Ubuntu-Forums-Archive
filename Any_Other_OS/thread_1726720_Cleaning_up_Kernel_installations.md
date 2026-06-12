---
title: "Cleaning up Kernel installations"
date: 2011-04-11
forum: Any Other OS
---

### Post by MetalheadGautham on 2011-04-11
Hi, I've an installation of ubuntu 9.10 (well actually the corresponding mint but anyway...)

I've been trying to find a way of clearing up clutter from my system. I noticed a huge bug (or rather nag) in the way the OS handles kernel upgrades. Instead of removing the previous versions of kernels from the system, it keeps them intact. My tiny 200MB ext2 /boot partition is all filled up.

Is there any way to keep only the current kernel version and remove everything else ? Apt-get autoremove does not seem to do it.

---

### Post by TeoBigusGeekus on 2011-04-11
Open synaptic, search for linux-image. Keep the 1~2 latest ones and purge all the others.
Don't forget to do a
```
sudo update-grub 
```
afterwards.

---

### Post by Kirboosy on 2011-04-11
You can use a program called [Ubuntu Tweak]("http://ubuntu-tweak.com/")

Or you can use Synaptic Package Manger (System-->Admin-->Synaptic) and remove the kernels by typing in their names into the quick search box. (kernel2.6.xx.xx or something similar) 

Run in a terminal the following command after removing the kernels via Synaptic ```
sudo update-grub
```

Hope that helps,
~Caboose

---

### Post by Perfect Storm on 2011-04-11
Moved to Other OS/Distro Talk forum.

---

### Post by MetalheadGautham on 2011-04-12
Ubuntu tweak does not seem to install.
And synaptic shows only 1 version installed but a ls on my /boot says:

```

abi-2.6.31-11-rt          config-2.6.32-26-generic      System.map-2.6.31-11-rt       vmcoreinfo-2.6.32-27-generic
abi-2.6.32-21-generic     config-2.6.32-27-generic      System.map-2.6.32-21-generic  vmcoreinfo-2.6.32-28-generic
abi-2.6.32-23-generic     config-2.6.32-28-generic      System.map-2.6.32-23-generic  vmcoreinfo-2.6.32-30-generic
abi-2.6.32-24-generic     config-2.6.32-30-generic      System.map-2.6.32-24-generic  vmlinuz-2.6.31-11-rt
abi-2.6.32-25-generic     grub                          System.map-2.6.32-25-generic  vmlinuz-2.6.32-21-generic
abi-2.6.32-26-generic     initrd.img-2.6.31-11-rt       System.map-2.6.32-26-generic  vmlinuz-2.6.32-23-generic
abi-2.6.32-27-generic     initrd.img-2.6.32-21-generic  System.map-2.6.32-27-generic  vmlinuz-2.6.32-24-generic
abi-2.6.32-28-generic     initrd.img-2.6.32-23-generic  System.map-2.6.32-28-generic  vmlinuz-2.6.32-25-generic
abi-2.6.32-30-generic     initrd.img-2.6.32-24-generic  System.map-2.6.32-30-generic  vmlinuz-2.6.32-26-generic
boot                      initrd.img-2.6.32-25-generic  vmcoreinfo-2.6.31-11-rt       vmlinuz-2.6.32-27-generic
config-2.6.31-11-rt       initrd.img-2.6.32-26-generic  vmcoreinfo-2.6.32-21-generic  vmlinuz-2.6.32-28-generic
config-2.6.32-21-generic  initrd.img-2.6.32-27-generic  vmcoreinfo-2.6.32-23-generic  vmlinuz-2.6.32-30-generic
config-2.6.32-23-generic  initrd.img-2.6.32-28-generic  vmcoreinfo-2.6.32-24-generic
config-2.6.32-24-generic  lost+found                    vmcoreinfo-2.6.32-25-generic
config-2.6.32-25-generic  memtest86+.bin      

```

can I safely delete any of those ?

---

### Post by Kirboosy on 2011-04-12
> **MetalheadGautham said:**
> Ubuntu tweak does not seem to install.

It must be because you are running a older version of Ubuntu...

[QUOTE=MetalheadGautham]
And synaptic shows only 1 version installed but a ls on my /boot says:

```

abi-2.6.31-11-rt          config-2.6.32-26-generic      System.map-2.6.31-11-rt       vmcoreinfo-2.6.32-27-generic
abi-2.6.32-21-generic     config-2.6.32-27-generic      System.map-2.6.32-21-generic  vmcoreinfo-2.6.32-28-generic
abi-2.6.32-23-generic     config-2.6.32-28-generic      System.map-2.6.32-23-generic  vmcoreinfo-2.6.32-30-generic
abi-2.6.32-24-generic     config-2.6.32-30-generic      System.map-2.6.32-24-generic  vmlinuz-2.6.31-11-rt
abi-2.6.32-25-generic     grub                          System.map-2.6.32-25-generic  vmlinuz-2.6.32-21-generic
abi-2.6.32-26-generic     initrd.img-2.6.31-11-rt       System.map-2.6.32-26-generic  vmlinuz-2.6.32-23-generic
abi-2.6.32-27-generic     initrd.img-2.6.32-21-generic  System.map-2.6.32-27-generic  vmlinuz-2.6.32-24-generic
abi-2.6.32-28-generic     initrd.img-2.6.32-23-generic  System.map-2.6.32-28-generic  vmlinuz-2.6.32-25-generic
abi-2.6.32-30-generic     initrd.img-2.6.32-24-generic  System.map-2.6.32-30-generic  vmlinuz-2.6.32-26-generic
boot                      initrd.img-2.6.32-25-generic  vmcoreinfo-2.6.31-11-rt       vmlinuz-2.6.32-27-generic
config-2.6.31-11-rt       initrd.img-2.6.32-26-generic  vmcoreinfo-2.6.32-21-generic  vmlinuz-2.6.32-28-generic
config-2.6.32-21-generic  initrd.img-2.6.32-27-generic  vmcoreinfo-2.6.32-23-generic  vmlinuz-2.6.32-30-generic
config-2.6.32-23-generic  initrd.img-2.6.32-28-generic  vmcoreinfo-2.6.32-24-generic
config-2.6.32-24-generic  lost+found                    vmcoreinfo-2.6.32-25-generic
config-2.6.32-25-generic  memtest86+.bin      

```can I safely delete any of those ?[/QUOTE]

I think in Synaptic you should try searching "[I]linux-image-2"
[/I] 

Run the following command in terminal ```
uname -r
```This will show the current kernel you are running. I would recommend removing the older ones but still leave the next most recent one just for safety.


~Caboose

---

### Post by MetalheadGautham on 2011-04-15
Thanks :D
Finally some 111mb of free space on my 200MB /boot partition...

But is there any way I can choose to automatically upgrade to the latest kernel and discard older ones when an upgrade happens ?
I was used to this kind of an upgrading process back in my Arch Linux desktop....

---

### Post by Kirboosy on 2011-04-15
After some Googling it seems that Ubuntu does not support that...(I'm not going to say it can't because someone may add that feature later.)

I would recommend updating to a higher version of Ubuntu (11.04 comes out in 13 days or 10.04 if you like LTS.) The newer versions will be able to run Ubuntu Tweak which makes it a few clicks to remove old kernels. 

Ubuntu Tweak doesn't do it automatically but its easier than Synaptic. You just sparked my curiosity to see if I can write a script that will auto remove kernels...

~Caboose

---

### Post by bodhi.zazen on 2011-04-15
As long as we are in other OS talk, other distros do a better job of managing old kernels without having to install additional packages or manually removing them.

Fedora keeps 2 old kernels which is sufficient for most any circumstance.

---

### Post by HunkirDowne on 2011-04-18
Just another tack and a caveat.  The caveat is, if you are using aptosid (was sidux), you should log out of GUI, log in as root, and go init 3 before messing around with apt-get.

Say I have three kernels and want to get rid of the oldest one.  So I get a list of what I have:
```
# ls -1 /boot/initrd*
```
> /boot/initrd.img-2.6.38-2.slh.6-aptosid-686
/boot/initrd.img-2.6.38-2.slh.7-aptosid-686
/boot/initrd.img-2.6.38-3.slh.2-aptosid-686

Then I use dpkg to get the proper name for later use in apt-get:
```
# dpkg --get-selections | grep 2.6.38-2.slh.6-aptosid-686
```
> broadcom-sta-modules-2.6.38-2.slh.6-aptosid-686 install
linux-headers-2.6.38-2.slh.6-aptosid-686        install
linux-image-2.6.38-2.slh.6-aptosid-686          install


You may notice an entry for my PCMCIA module.  You may not see anything like this.  I will not discuss that here (at least initially ;-)).

Next, run apt-get to *take out the trash*, so to speak:
```
# apt-get remove --purge \
linux-headers-2.6.38-2.slh.6-aptosid-686 \
linux-image-2.6.38-2.slh.6-aptosid-686
```

Grub should be automagically updated by apt-get and you should no longer see the old stuff (because it shouldn't be there to see).

---

