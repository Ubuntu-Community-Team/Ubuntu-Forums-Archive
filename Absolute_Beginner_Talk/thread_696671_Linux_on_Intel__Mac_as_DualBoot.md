---
title: "Linux on Intel  Mac as DualBoot"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by pstoaling on 2008-02-14
Hi to everyone!

I am new to Linux, so please excuse my ignorance. I am very interested in learing how it works however. I currently own a MacBookPro using the latest version of Tiger. I would like to install a GUI Linux so that I can dual Boot. I would also like at some point in the near future to install windows on the machine, because there are some applications that I can only run in windows. So - this means triple booting.

After some investigation I realise that this is no easy task. I gather that I need to use rEFIt in order to do this. I just have a couple of question to help me get started.

1) What is the best GUI linux for me to use, considering I know no linux command codes

2) Is it possible to install Linux first, then windows at a later date.

3) Any handy tips would be great

Thanks in advance to everyone, hopefully you can help me to learn Linux quickly :)

---

### Post by Crooksey on 2008-02-14
1) I take it you mean distro, Ubuntu is great for new Linux users

2) Yes, but its not advisable

3) Read sevral tutorials before installing

---

### Post by rkd on 2008-02-15
I don't know how well they work, but both Parallels and VMware offer virtual machine products that run on OS X and let you install and run other operating systems in parallel with OS X applications. The open source Virtualbox does the same.

If you haven't evaluated these approaches as compared to dual or triple booting, I think they are worth a little bit of your time. They have a number of advantages over dual booting. One is that you don't have to partition your disk -- they use a large OS X file as a simulated disk for the guest OS. I believe the size of that file can grow as your guest OS needs increase without disruption of the guest OS.  Another advantage is that the guest OS and applications run together with OS X and its applications, so you don't have to shut down one environment to bring up another. I imagine that could be extremely convenient.

There are some disadvantages. The video performance usually isn't good enough for fast action games (this is true of virtualization on Windows PC; I believe I've read that the situation is better on Macs, but I don't know how much better). You need a lot of RAM to run each guest OS in order for the performance to be smooth. Devices are not directly accessed by the guest OS -- they are in a simulated machine -- so the devices the guest sees are simulations done by Parallels, VMware, or Virtualbox, so some software doesn't work in a virtual machine. I've read that USB devices are particularly sensitive to this.

I don't know how suitable any of the virtual machine products are for you. I just wanted to point them out as possibilities, in case you were unaware of them.

---

