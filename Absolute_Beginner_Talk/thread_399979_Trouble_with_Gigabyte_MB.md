---
title: "Trouble with Gigabyte M/B"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Novacaine on 2007-04-03
Greetings all,

Finally broken myself away from windows and trying Ubuntu out, except I have run into a small problem - I have no sound or network.

My System Specs:
AMD Seperon 3000+
[Gigabyte GA-M61VME-S2 M/B]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=2381&ProductName=GA-M61VME-S2")
nVidia 7100GS
512MB ram
160Gb Sata HDD

I'm guessing that I need drivers for my board as after a bit of searching all I could find was that Ubuntu won't detect the onboard features of the motherboard, but openSUSE would. Tried it out, and worked perfectly. But I would like to use Ubuntu and actually learn something (hence the move to Linux in the first place). I'm fairly familiar with Linux, and have installed Gentoo on a machine previously - but I had some help with that from an old workmate.

So my question is: How do I go about getting my onboard ethernet working? So far I've managed to track down the drivers to [these]("http://www.nvidia.com/object/linux_nforce_1.21.html") but can't find anything to help me on my way of actually installing them without the need to buy a seperate network card and downloading a bunch of other things - which I think kinda defeats the point, as if I can install another network card then why not stick with that one?

So before I go and spend money or change to a different flavour of Linux, I was wondering if there was anything I could do?

Thanks in advance for any help given.

---

### Post by amohanty on 2007-04-03
Before installing software from source, check if you have the following packages installed via: System->Administration->Synaptic:

nvidia-kernel-common
linux-restricted-modules-generic
linux-restricted-modules-common

HTH
AM

---

