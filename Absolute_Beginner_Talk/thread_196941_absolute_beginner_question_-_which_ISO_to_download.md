---
title: "absolute beginner question - which ISO to download for an AMD?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by rocka on 2006-06-15
Hi,

I tried the live CD a while back and liked it. Just yesterday I "inherited" a little AMD system so I thought I'd install the "real" Ubuntu on it. When I went to the "download" link there's a list of files there but no explanation of what's what.

The processor in the machine is an AMD 2800 - which file do I have to download and burn?

Thanks in advance for any help...
cheers :)

---

### Post by Jagot on 2006-06-15
x86 version - It's the one with i386 in the file name.

---

### Post by user1397 on 2006-06-15
this one: [PC (Intel x86) desktop CD]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso")
or if you prefer to download it via bittorrent, this one: [ubuntu-6.06-desktop-i386.iso.torrent]("http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso.torrent")

---

### Post by Koybe on 2006-06-15
You should install with the i386 ISO file. After the installation you'll be able to upgrade your kernel to K7 version.

```
sudo apt-get install linux-image-2.6.15-23-k7
```

---

### Post by frail on 2006-06-15
[QUOTE=Koybe]You should install with the i386 ISO file. After the installation you'll be able to upgrade your kernel to K7 version.
[/QUOTE]

I have an AMD Sempron 3000+ but it's not recognized as such by Ubuntu. uname -p returns "unknown." Right now I'm running the i686 kernel. Would it be still be benficial to run the k7 kernel or should I just stick with the i686?

---

### Post by Jagot on 2006-06-15
[QUOTE=frail]I have an AMD Sempron 3000+ but it's not recognized as such by Ubuntu. uname -p returns "unknown." Right now I'm running the i686 kernel. Would it be still be benficial to run the k7 kernel or should I just stick with the i686?[/QUOTE]

In all likelihood you probably won't get any performance increase from using the k7 kernel, so, unless you need it for a specific reason, sticking with the i686 should be fine.

---

### Post by frail on 2006-06-15
[QUOTE=Jagot]In all likelihood you probably won't get any performance increase from using the k7 kernel, so, unless you need it for a specific reason, sticking with the i686 should be fine.[/QUOTE]

Will do. Thanks.

---

### Post by user1397 on 2006-06-15
i thought the k7 kernel was only for 64-bit machines?

---

### Post by Jagot on 2006-06-15
[QUOTE=erik1397]i thought the k7 kernel was only for 64-bit machines?[/QUOTE]

Nope, k7 is for Athlon and newer AMD processors.  64-bit machines can use this as well in the 32-bit version of Ubuntu.

---

### Post by dcstar on 2006-06-15
[QUOTE=erik1397]i thought the k7 kernel was only for 64-bit machines?[/QUOTE]
I believe the K8 kernel is for the AMD 64 bit CPUs.

---

### Post by rocka on 2006-06-15
Thanks a lot to all those who answered - the downloading has started :)

I appreciate the help!

Look out for more questions soon, I'm sure LOL

---

