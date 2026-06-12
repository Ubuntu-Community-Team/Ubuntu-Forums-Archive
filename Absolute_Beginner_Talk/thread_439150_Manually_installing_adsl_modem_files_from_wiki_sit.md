---
title: "Manually installing adsl modem files from wiki site"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by DigitalRanger on 2007-05-10
Hi,
I'm still experimenting to see if I can get my Fujitsu FDX310 USB ADSL modem working with the Live CD. (I'm not installing Ubuntu until I know I can make this work).

Browsing the Ubuntu wiki I found the packages, and those they depend on, that I need:[LIST]
[*][eciadsl (0.11-3)]("http://packages.ubuntu.com/feisty/net/eciadsl")
[*][pppoe (3.8-1.1)]("http://packages.ubuntu.com/feisty/net/pppoe")
[*][libc6 (2.5-0ubuntu14)]("http://packages.ubuntu.com/feisty/base/libc6")
[*][ppp (2.4.4rel-4.1ubuntu2)]("http://packages.ubuntu.com/feisty/base/ppp")
[*][udev (108-0ubuntu4)]("http://packages.ubuntu.com/feisty/admin/udev")[/LIST]At the bottom of each page, there's the three types of file I can download: **.dsc**, **.targ.gz**, and **.diff.gz**.

I just need to know what to do with these files. Do need to download all of them, or just one of them?

Then which command line command do I need to use on them to get them installed?

One last question, will whatever you advise me to do also work with Kubuntu ?

Thanks for reading.

[SIZE=1]P.S.
I know already that ethernet based devices are highly preferable for Linux based operating systems, I really do get that. So please please please do not tell me that I should get an ethernet based device rather than trying to make this work. I'm in the unfortunate position of having to make do with the hardware I have, for the time being.[/SIZE]

---

### Post by Najand on 2007-05-10
All of the above softwares are included in the Universe Repository.
So, just enable the Universe & Multiverse Repositories and then type:
```

sudo apt-get update && sudo apt-get install eciadsl pppoe libc6 ppp udev

```

---

### Post by DigitalRanger on 2007-05-10
> **Najand said:**
> All of the above softwares are included in the Universe Repository.
So, just enable the Universe & Multiverse Repositories and then type:
```

sudo apt-get update && sudo apt-get install eciadsl pppoe libc6 ppp udev

```

That won't help me because my modem is my only means of accessing the internet. Chicken and the egg, until I have that software installed, I can't get online to apt-get or anything else.

I'm online now in Windows XP, so I will be putting the packages onto USB stick, then when I know what to do with them, I'll reboot off the Live CD and get to work.

---

### Post by Najand on 2007-05-10
You need .DEB files.... 
When going to the packages page click on the name of your architecture (i.e. amd64, i386, powerpc, etc) and then download the files from ther closest mirror.

You can use your installation CD to install those packages too.

---

### Post by DigitalRanger on 2007-05-10
Aha, thank you. I didn't realise the architecture titles were actually links, so I kept just ending up with the file lists.

I've got the .deb files now. I'll reboot and see what I can do :)

---

### Post by Najand on 2007-05-10
you will probably need some other packages: dependencies...
Also for installing the packages you need to run:```

sudo dpkg -i PACKAGE1 PACKAGE2 ETC

```

---

### Post by DigitalRanger on 2007-05-10
Okay thanks,

Is there any way I can get Synaptic to look at my USB stick and let that handle the installation and dependences for me? (As I can just download all the possible dependencies onto my stick now and let Synaptic handle it).

---

### Post by Najand on 2007-05-10
Synaptic PM is made on APT like apt-get, aptitude, etc. You can use the following APT help for that:
[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)
But I personally think it is much easier to install packages using "dpkg -i" command.
You can install all packages on your usb memory using (DIRECTORY is your mount point):
```

cd DIRECTORY
sudo dpkg -i *.deb

```

---

### Post by DigitalRanger on 2007-05-10
Okay then.

I'll go get some more dependencies, *just in case* and do the command line thing on my usb stick.

Thanks for your help and I'll post back to let you know how I got on.

---

### Post by DigitalRanger on 2007-05-10
Okay, this is kind of funny.

I downloaded all (probably more than necessary) the .deb files I could need, put them on my USB stick and booted from the Live CD.

Opened terminal, navigated to the directory they were stored in, and ran
> sudo dpkg -i *.deb

Everything proceeded without any errors, I was very happy.

Although when I tried typing in "eciadsl", I just got an error that the command "eciadsl" was not found. So wondering if I should think of eciadsl as more of a driver or daemon, I tried running pppoeconf, which ran ok, but only detected what I assume was my Ethernet and WiFi cards.

I even tried disconnecting and reconnecting my modem, but still nothing happened.

So, once they're installed, what should I do next?

---

### Post by DigitalRanger on 2007-05-11
Still don't know what to do next :)

---

