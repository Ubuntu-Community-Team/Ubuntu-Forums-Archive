---
title: "nVidia GT540M CUDA 1GB graphics card, what drivers to use on 11.10?"
date: 2011-10-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by muzikayise on 2011-10-16
hi all,

I just got an Asus N53SV-S1830X laptop with core i7 2670QM. I installed ubuntu 11.10 and everything is working smoothly but when i navigate to System Settings -> System Info -> the graphics comes up as ''Unknown" when i boot into the "other" OS i can see the nVidia card alongside with nVidia software and so on. 

I downloaded the latest drivers from the nVidia site for Linux but couldn't install them.

The i came across bumblebee , Ironhide and 'The Bumblebee-Project' I've gone thru all and i just havent been able to win with this.Therefore i was wondering if someone may please kindly assist by pointing me to the correct location for setting up nVidia graphics card on ubuntu 11.10.

---

### Post by HellesAngel on 2011-10-17
Unfortunately support for the switchable on board low power Intel graphics and the higher performance and higher power external NVidia chips in Linux is haphazard at best at the moment.  The good thing is that Bumblebee is working fine on this laptop (Asus X53S with 2Gb NVidia GT540M and Intel Sandy Bridge i5 with on board graphics), but still the Additional Drivers dialog shows the NVidia drivers are not being used.  The easy switching, ie. that gives the easy control between performance and battery life,  that Windows 7 users enjoy hasn't made it to Linux yet.

While installing Unubtu 11.04 I had a mixed experience - the Windows installer worked fine, giving me the fancy desktop which means it was using the NVidia chip, when I tried to upgrade the NVidia drivers the whole thing collapsed, Ubuntu first wouldn't boot, and then wouldn't go back to the old drivers that worked, and I couldn't fix it.  A clean install on a proper bootable partition didn't use the NVidia chip at all without Bumblebee, but now it seems more stable and is working fine.  I can't speak to battery life as this laptop is almost always plugged in.

Lots of words to say, in short, I'd leave it as it is, follow the recommended upgrades only and be a version old but happy ;)

---

### Post by muzikayise on 2011-10-17
> **HellesAngel said:**
> Unfortunately support for the switchable on board low power Intel graphics and the higher performance and higher power external NVidia chips in Linux is haphazard at best at the moment.  The good thing is that Bumblebee is working fine on this laptop (Asus X53S with 2Gb NVidia GT540M and Intel Sandy Bridge i5 with on board graphics), but still the Additional Drivers dialog shows the NVidia drivers are not being used.  The easy switching, ie. that gives the easy control between performance and battery life,  that Windows 7 users enjoy hasn't made it to Linux yet.

While installing Unubtu 11.04 I had a mixed experience - the Windows installer worked fine, giving me the fancy desktop which means it was using the NVidia chip, when I tried to upgrade the NVidia drivers the whole thing collapsed, Ubuntu first wouldn't boot, and then wouldn't go back to the old drivers that worked, and I couldn't fix it.  A clean install on a proper bootable partition didn't use the NVidia chip at all without Bumblebee, but now it seems more stable and is working fine.  I can't speak to battery life as this laptop is almost always plugged in.

Lots of words to say, in short, I'd leave it as it is, follow the recommended upgrades only and be a version old but happy ;)

Thanks buddy for kindly getting back to me. I must say i can live without automatic switching for now, I'm not really using the laptop for games yet more for work and running multiple VMs, and in terms of battery life, well also not important at the moment because I've always got the laptop plugged in.  But I just want to make sure that everything is running well. I will have a look at "the Bumblebee project" again.
thanks

---

### Post by gavdari on 2011-10-17
Same problem here. I have a Lenovo Y570 with switchable graphic between GT555 1GB and Intel HD3000. I tried 11.10 (which works fine on my other laptop with Geforce 8400 by the way) and it couldn't detect the Nvidia chipset. It works when I force install the nvidia-current package, but then the GPU fan was always working, so I had to fall back to Windows on this one. Also on the battery life, a full battery works for 6 hours in windows but only 2h30m on Ubuntu. It's a pity that automatic switching doesn't work on Ubuntu.

Besides, on windows I can get the optimum resolution ( 1366x768 ) even with Intel graphics, but on Ubuntu the resolution was much lower.

---

### Post by muzikayise on 2011-10-20
herewith an update

Ok as i said in my previous post there 3 bumblebee projects and i finally understand which one is which

[LIST=1]
[*][bumblebee]("https://github.com/MrMEEE/bumblebee") (with lowercase b) this is the original one created by [Martin Juhl]("http://www.martin-juhl.dk")
[*][ironhide]("https://github.com/MrMEEE/ironhide") this was the continuation from bumblebee
[*][Bumblebee (Bumblebee-Project)]("https://github.com/Bumblebee-Project/Bumblebee") this is the new one you should use this one if you need to install bumblebbee
[/LIST]
I used instructions from the [Linux Hybrid Graphics]("http://linux-hybrid-graphics.blogspot.com/") to install bumblebee but i used the [Bumblebee-Project git repository]("https://github.com/Bumblebee-Project/Bumblebee") instead of bumblebee because the PPA didn't work for me. PPA installs but optirun doesnt work and there are initial installation errors.

```

##This Didn't work for me!!!
sudo apt-add-repository ppa:mj-casalogic/ironhide
sudo apt-get update && sudo apt-get install ironhide
```I've got it installed and i tested it using this following test, there's huge difference when i run this test with out nvidia card on.
```

Installation instructions for getting the code from git:
    $ git clone git://github.com/Bumblebee-Project/Bumblebee.git
Users who want to test the development code should run:
    $ git clone git://github.com/Bumblebee-Project/Bumblebee.git -b develop --depth 1
Then in order to install:
    $ cd Bumblebee
    $ sudo ./install

Then Test
    optirun google-chrome http://webglsamples.googlecode.com/hg/aquarium/aquarium.html
    # close window
    google-chrome http://webglsamples.googlecode.com/hg/aquarium/aquarium.html

```or tho i get following errors when i run "optirun"
```

muzi@muzi-N53SV-LL:~$ optirun google-chrome http://webglsamples.googlecode.com/hg/aquarium/aquarium.html
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.

(google-chrome:2873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(google-chrome:2873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(google-chrome:2873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(google-chrome:2873): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[3:3:4278958341:ERROR:nss_util.cc(397)] Error initializing NSS without a persistent database: libsoftokn3.so: cannot open shared object file: Permission denied
ERROR: ld.so: object 'libdlfaker.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'librrfaker.so' from LD_PRELOAD cannot be preloaded: ignored.

```the errors don't look serious and the test works quite well

Test Images - Screen Resolution (1920 x 1080) both displays laptop and BenQ24" LCD. But laptop looks way better.:D
[IMG]http://mfbproject.co.za/images/Screenshot%20at%202011-10-20%2023:31:05.png[/IMG]

[IMG]http://mfbproject.co.za/images/Screenshot%20at%202011-10-20%2023:31:27.png[/IMG]

---

### Post by lorebett on 2011-12-20
so bumblebee is not completely replaced by ironhide, is it?
Because I tried ironhide and the configuration never completed successfully...

---

