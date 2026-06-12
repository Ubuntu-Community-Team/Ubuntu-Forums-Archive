---
title: "My Wi-Fi connection doesn't &quot;work&quot;"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Toxic-Waste on 2007-03-14
Hello people!

Ok, now I am getting more and more pissed of every day with the Ubuntu Distro! It is the only one between the 4 I have tested and WinXp that is the least “plug and play”! I have tried PCLinuxOS, OPENSuse, Sabayon and Ubuntu.

Now I can't configure my Wi-Fi to work! I have located my Wi-Fi modem, I have connected to it, all readings show me that everything is super but I can't use the Internet. What do I have to do this time. Read one page of How-to's? Why can't these things be easier?!?! The live CD's of all the other Linux Distros worked with my Wi-Fi flawlessly, so why can't an Installed Ubuntu Distro do the same?!?!? WinXp works automatically, why doesn't Ubuntu!?!?

Can somebody please help me? I am growing tired of wasting my precious time with tasks that other OSs do with ease!!!

Thanks!

---

### Post by oilchangeguy on 2007-03-14
then quit crying about ubuntu. if you've found other distros that work without any problems, USE ONE!

---

### Post by christhemonkey on 2007-03-14
Is this a request for help or just a whinge about ubuntu?

If its a request for help, then some more information would be nice (chipset, model, usb/pci, wep/wpa etc)

If its not, well then do what oilchangeguy suggested and use the distro that works *for you!*

---

### Post by JAwuku on 2007-03-14
Hi toxic-waste,

Sorry about your problems getting your wireless to work. It took me a few months to work out finally how to set up my USB wireless in Ubuntu and Sabayon! Only PCLinuxOS 2007automatically sets up my wireless out of the box.

Fortunately, there are many solutions depending on what type of chipset your wireless works.

Try the Ubuntu Help Documents, which have guides for setting up various devices:

[https://help.ubuntu.com/community/WifiDocs/Device](https://help.ubuntu.com/community/WifiDocs/Device)

If you type in a terminal:

```
lsusb
```

and

```
lspci
```

and post your results to the forums, this gives the IDs of the devices, and the chipsets can be worked out, hopefully from there.

---

### Post by Toxic-Waste on 2007-03-14
Thanks JAwuku, 
I will follow your advice.

---

### Post by Toxic-Waste on 2007-03-17
Dear Friends,

Ironic as it is I found the solution to many problems and not just the Wi-Fi one, simply by installing another distro! I removed Ubuntu moved on to OpenSuse 10.2 and everything just sets up so smooth I feel great! My Wi-Fi connection for example needed no extra program installed and no "special" setting up. As soon as the OS loaded it asked me for my WEP and Wham Bam I was online in less than a minute. Similar easiness with installing ATI drivers and anything so far. I only have to follow the official wiki guidelines and everything works. I can also install special keyboard shortcuts for my TOSHIBA laptop!!! :) 

Thanks again for all your help, turns out Ubuntu 6.10 isn't the distro for me. I will be trying out Ubuntu Feisty Fawn when out. Hope it is better than the current version. Again this is only my opinion, I am not trying to make anybody agree with me, just speaking my mind.

Later...:grin:

---

### Post by AndeAnderson on 2007-03-17
What ISO of OpenSUSE did you install?  I too have a Toshiba Laptop and so far the only Linux Distro that found my network card without making me wade through a lot of Gibberish was Debian Sarge.

ubuntu was highly recommended but failed to even find either my wired or wireless LAN devices and the documentation is sorely lacking for the set-up of my Toshiba Laptop Atheros network cards.  I did find basic instructions for my Buffalo Air Station.  But those are worthless if I can't get the LAN cards set-up.

I was looking forward to using the ubuntu Christian Version.  But, the incompatibility is really disappointing, especially since I see it is based on Debian but lacks the versatility of the Debian Distro.  :lolflag:

---

### Post by Toxic-Waste on 2007-03-17
Dear AndeAnderson,
OpenSuSe 10.2 is the distro I used. You can find the CD and DVD ISO files you need at this link [**here**]("http://en.opensuse.org/Released_Version"). My Toshiba laptop works perfectly with OpenSuSe 10.2 and if you go to the [**OpenSuSe Toshiba page**]("http://en.opensuse.org/HCL/Laptops/Toshiba"), you can see if your laptop is supported before you even set it up.
Hope I helped you out.

---

### Post by AndeAnderson on 2007-03-17
Thanks!

I wish all distro's had that kind of a compatibility chart.  Unfortunately, my laptop is only supported by the 10.0 Beta 4 Distro.

So, I just went back to Debian Sarge.

---

