---
title: "wine?!"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Chymera on 2007-07-22
It all started when i kind of got fed up with gimps 8-bit/channel colour depth and the lack of a healing tool....

so I decided to use cs3 through wine, i have read a lot of stuff about this on the forums (apparently it dosnt work), but the newbish question is: 
HOW DOES wine actually work? do i need to dl photoshops install kit and install it "through" wine, do i have to have it pre installed in windows and run it from my ntfs partition? do i need to have it installed in windows and copy it to an ext2/3 partition, do i have to copy it to the exact same partition my root is on?

And furthermore what is this VM, that can supposedly run windows under linux, and where can i find it?

---

### Post by jvc26 on 2007-07-22
VM is 'Virtual Machine' this means basically you install an operating system to a virtual disk, and then use that as if it were the operating system. I use this to run CS2, but to be honest, CS3 needs 1Gb RAM minimum, so to be able to run that in VM you will need to have pretty extensive RAM available. VM allows you to run the apps as if they were in windows (because they are, in a virtual environment) but it requires pretty high resources, especially for a hungry app like CS3. You can get vmware via the ubuntu commercial repositories in feisty (If I remember rightly it is:
```

sudo apt-get install vmware-server

```
The other possibilities for Virtualisation apps are Virtualbox, QEMU (+ is KQEMU backend). You'd need to have a look into them to see one which would work best for you - or try them out!

If you want to VM, to be honest it would make more sense for a resource heavy app like CS3 just to have a dual boot and run the windows one when you need CS3 - you'll get much better performance.

RE:: Wine and CS3 I would say its highly unlikely this will work as CS2 support in wine is pretty sketchy.

If you look at the wineHQ documentation and their list of programs which work that may well point you to whether it is possible. With regards to crossover office, I have hear rumour that that may work better, but you have to pay for that - checking on their website may also be well worth doing.

Il

---

### Post by xubu_caapn on 2007-07-22
virtualization and wine are not satisfactory solutions most of the time, especially if you want to run a resource heavy app like cs3. the best is to have another windows partition.

i don't know what you would do with a complex program like cs3, but normally in wine you just direct it to an .exe and it installs it on your linux box. it's not on a windows partition or anything like that.

---

### Post by cotcot on 2007-07-22
I do not know the answer on your question. 
I do not know to what extend you use cs3. Maybe a check of cinepaint or krita might help you. Both apps pretend to be able to deal 16 bit color.

---

### Post by geist27 on 2007-07-22
VMWare is a good program, but having used it and its alternative Virtualbox, I prefer Virtualbox.  If you are interested in either, Automatix is the best and easiest way to install both of them and lots of other useful things on your Ubuntu install.  See my sig for a link to Automatix and Virtualbox.

---

### Post by Chymera on 2007-07-23
automatix? isnt that a program on its own?

to cotcot, well yes, they both have SOME VERY BASIC support for 16-bit, but i would prefer REAL support for 32-bit. 

And regarding xubus description about how wine works, do i just open it and double click on an .exe? I have tried running w3 and cs2 from my ntfs partition like that... but to no avail. I find it weird that it doesnt run w3 just like that, since that prog hasnt got any vital registry keys. Sugestions?

Oh and finaly, i dont know who told you that cs3 is a resource-hungry app, but the truth is it hogs far less ram and cpu than cs2....

---

### Post by Mornedhel on 2007-07-23
Wine reimplements the Windows API so you can call most of it (and therefore run most Windows programs) in Linux. Installers can perfectly be run under Wine, this will create a new entry in your main menu, etc.

However :
1. Wine is always under development, trying to follow the evolution of the Windows API, etc. It will NOT run all software perfectly. See [http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php) for a list of what runs, what does not, and what has not even been tried.
2. The installers will sometimes run under Wine, sometimes not. When they don't, if you have Windows in dual boot, you can try to install the software under Windows, then try and run the installed program under Wine. Does not always work.
3. Wine-ing software from an NTFS partition is not easy either. I don't know how well NTFS R/W and Wine work together, but I suspect the combination may increase the failure rate. Overall, FAT32 is a better choice if you intend to use the partition under both OSes.

---

### Post by sailor2001 on 2007-07-23
on my box: applications/accessories/wine file opens up the wine for me to install programs. ... and there are a lot of programs not even listed in wine that will work.  For instance Sierra Print Artist

---

### Post by Chymera on 2007-07-23
ok 10x for the info.... i read somewhere that you have to copy the app you want to run in a certain folder on your root partition, and that got me kinda confused :confused:

---

