---
title: "Aiirport Extreme"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by vixinu on 2006-09-03
I just got Ubuntu, and my airport Extreme isn't supported.  I think the problem is that I don't have ndiswrapper, but I don't know.  If that is the problem, how do I get it?

---

### Post by kidders on 2006-09-04
You don't need ndiswrapper (which afaik is for wrapping Windoze drivers anyway) to talk to an Airport Extreme card ... they're Broadcom cards, which (again, afaik) are natively supported in by the kernel now.

You'll need to get hold of a recent firmware to actually make it go, though.

---

### Post by vixinu on 2006-09-05
how do i do that?  and what do i do once i get it?

---

### Post by vixinu on 2006-09-05
I need something for bcm4318, I think

---

### Post by kidders on 2006-09-05
Have you taken a look at [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) ?

---

### Post by vixinu on 2006-09-05
"It seems that if you get the following string back: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) that this guide is VERY unlikly to work for you" 

That is what I have

---

### Post by kidders on 2006-09-05
Oh no :(

Exactly what kind of Mac do you have? (I must check my one!)

There are quite a number of Airport-related howtos around ... there *has* to be one that'll work for you. I'll do some research :-P

---

### Post by vixinu on 2006-09-05
iBook G4, bought in August '05.

I'll do research too

---

### Post by kidders on 2006-09-05
Hmm... apparently, the BCM43xx drivers built into the kernel *do* support your Airport card. I did notice one snag though:

Support for your specific card only appears to be officially available from kernel version 2.6.17-RC2 and above (RC = release candidate).

I'm a long-time Linux user, but have only recently started playing with Ubuntu, so I'm assuming my install is pretty up-to-date. My kernel version is only 2.6.15 though. (Kernel 2.6.18 is currently in testing.)

Check yours by typing:

```

uname -r

```

If, like me, you're using a pre-2.6.17 kernel, the easiest way to get your Airport working would be to first upgrade your kernel, and then follow a HOWTO from a more up-to-date Linux distro regarding what to do with fwcutter, and so forth.

So, four alternatives:

1 - Dump Ubuntu and switch to another Linux (such as Gentoo) that uses (often ill-advisedly) newer kernels
2 - Keep Ubuntu and update your kernel manually
3 - Wait for Ubuntu to upgrade its kernels officially
4 - Do nothing

What do you think?

---

### Post by kidders on 2006-09-05
One additional personal note:

If it were me, I'd keep Ubuntu ('cause it's pretty :-) ) and manually upgrade my kernel. It's not a trivial task though -- unless you've done it before, you'd need help.

---

### Post by vixinu on 2006-09-06
2.6.15-26

Yikes.

How do I update that

---

### Post by kidders on 2006-09-06
The theory is as follows:

I. Download and unpack the source code for the newest available kernel.
```

mkdir /usr/src    [ this directory may already exist ]
cd !$
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.17.11.tar.bz2
tar -xjf linux-2.6.17.11.tar.bz2
ln -s linux-2.6.17.11 linux

```

II. Tweak it to match your current kernel's configuration as closely as possible.
```

cd /usr/src/linux
cp /boot/config-`uname -r` ./.config
make oldconfig

```

III. Run the kernel configurator to make sure everything's okay, not forgetting to build in support for Broadcom WLAN adapters.
```

make xconfig

```

IV. Compile the kernel. (And have a coffee break!)
```

make

```

V. Install the new kernel.
```

make modules_install
cp arch/i386/boot/bzImage /boot/kernel-2.6.17.11

```

VI. Update your bootloader.
```

nano -w /boot/grub/menu.lst

```

VII. Pray
```

CTRL+ALT+DEL

```

In practice, there are a few extra bits, wrinkles and Ubuntu-specific things that you would need to do, to avoid messes, but that's the general shape of things.

Assuming you pulled it off though, your wireless card would spring to life as if by magic :-P

Easy? Perhaps not...

---

### Post by vixinu on 2006-09-06
That didn't work.

[This website]("http://ubuntuforums.org/showthread.php?t=217657") seems to work, but make-kpkg doesn't work.

And I don't know how to:

"Simply unset the following (change from module to nothing)

Device Drivers -> Multimedia Devices -> Digital Broadcasting Devices -> 

Budget cards
Budget cards with onboard CI connector
Budget cards with Budget Patch
AV7110 cards with BudgetParch"

I think that *might* be why make-kpkg doesn't work

---

### Post by kidders on 2006-09-07
What do you mean by "doesn't work"?

---

### Post by vixinu on 2006-09-07
bash: make-kpkg: command not found

---

### Post by kidders on 2006-09-08
You're missing something important ... an "apt-get install" will fix this for you.

---

### Post by vixinu on 2006-09-08
what do I apt-get install?

---

### Post by vixinu on 2006-09-12
I tried but just

```
apt-get install
```

didn't work.

---

### Post by kidders on 2006-09-14
Hi there,

Sorry for the delay in responding. The package you're missing is probably **kernel-package** ... [http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=kernel-package&version=dapper&arch=all](http://packages.ubuntulinux.org/cgi-bin/search_contents.pl?searchmode=filelist&word=kernel-package&version=dapper&arch=all)

---

### Post by vixinu on 2006-09-14
I tried kernel-package.  It didn't work

---

### Post by vixinu on 2006-09-14
The error it gives me is:

```

Package kernel-package is not available, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source

```

---

### Post by kidders on 2006-09-15
How strange. Is your package database up-to-date? (Your internet connection is okay, etc., I suppose.)

---

### Post by vixinu on 2006-09-15
Actually, I'm using Internet from my mom's computer.  I transfer files w/ an external HD.  I downloaded  Ubuntu 2 weeks ago, but I don't know if my package database is up-to-date or not.

---

