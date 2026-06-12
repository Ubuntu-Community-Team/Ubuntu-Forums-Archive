---
title: "really have a lot of questions"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by cmrober on 2007-04-28
Hi, I have some questions about Windows programs compatibility and others so I'll try and be as concise as possible. Can I run Windows programs thru an emulator or something? Can I install Ubuntu on the same partition  as Windows? Does Ubuntu create it's own partition? What about startup? Is a start up option created to boot to Windows or Ubuntu? That's enuf for now. Thanks

---

### Post by PartisanEntity on 2007-04-28
You can use a program called Wine to run Windows applications in Linux but you will have to see if the those programs will work with Wine (not all do).

Ubuntu will make its own partition and install itself *next to* whatever OS you had on your HDD. It will also install a boot loader which will allow you to choose which OS to load.

Ubuntu will not destroy your already installed OS if that is what you are worried about :)

---

### Post by Seisen on 2007-04-28
You can use Wine to run Windows programs in Ubuntu, but not all programs will run in Wine.
You can install Ubuntu on the same harddrive but not the same partition, it will create a seperate partion for it.
When you install Ubuntu it will install Grub which is a bootloader and will give you the option of  either running Ubuntu or Windows.

---

### Post by xboxbman on 2007-04-28
> **cmrober said:**
> Hi, I have some questions about Windows programs compatibility and others so I'll try and be as concise as possible. Can I run Windows programs thru an emulator or something? Can I install Ubuntu on the same partition  as Windows? Does Ubuntu create it's own partition? What about startup? Is a start up option created to boot to Windows or Ubuntu? That's enuf for now. Thanks

Ok.  Ubuntu installs on a seperate partition.  First install Windows, then install Ubuntu, and Ubuntu will install GRUB, which is a menu that pops up when you first boot your pc that let's you select which OS you want to run.  Finally there is two emulators for windows apps.  The first is WIne, which free, but has compatibility issues.  There is also cedega, which you have to pay a monthly fee for, but has more compatibility than Wine.

---

### Post by psionyk on 2007-04-28
The other option would be to use virtualization software like VMware or Virtualbox and install windows and the programs you need to use in it, and then you can run Windows right inside Linux.  There are also ways to convert a physical Windows partition into a virtual one, however, this can create problems with Windows detecting that your computer configuration has changed and requesting reactivation.

Let us know what Windows programs you are wanting to run, as there are more than likely some Linux alternatives that could be just as good if not better, thus saving you the time and effort of going through setting up a wine or virtual environment.

Good luck! :)

---

### Post by Nythain on 2007-04-28
yeah... if truly considering the switch, dont rule out a virtual install of windows inside ubuntu via vmware and virtualbox. great for just about everythign but gaming.

Wine (Wine Is Not an Emulator) is great for running a decent amount of windows apps including excellent game support

Cedega started as a fork of wine called WineX, the first to have decent directx capability... Some say it has the BEST game support, though its very buggy... it also has a nice pretty GUI, wich wine lacks... its commerciall... 15$ for 3 months, gets you the main client, the latest engine for it, access to thier support and forums... and any engine updates that come out within that time period... can renew for another 15$ for three more months if you like the service

CrossOver is a commercial winebased application that boasts the ability to better run certain windows apps than wine does... namely office, photoshop, and a few others i cant remember off the top of my head... game support is limited, but i think it can be done.

To summarize... if you want to keep windows around for gaming, then dual booting is probably for you... of shelling out the money and patience to deal with cedega.

If its just certain windows apps you need to run... consider wine or crossover and forgetting about windows all together, its just a waste of space.

If you still want that windows operating system, but dont care much for modern games... i would recommend running it virutal inside ubuntu via vmware or virtualbox

hope at least some of that helps

---

