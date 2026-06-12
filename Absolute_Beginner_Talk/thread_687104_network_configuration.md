---
title: "network configuration"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by chips24 on 2008-02-03
my network configuration will not let me connect to the internet, ive reinstalled it multiple times and i know my firmwire works but it wont connect!

help please?

---

### Post by chips24 on 2008-02-04
the software that comes with ubuntu dosnt work, and if i try anything esle, the original software will disrupt it.

---

### Post by chips24 on 2008-02-04
any help?

---

### Post by borris.morris on 2008-02-04
what is your hardware setup?

---

### Post by Michl on 2008-02-04
I think you need to say more.

---

### Post by chips24 on 2008-02-04
its like firmwire or somthing alon those lines, my wireless is a restricted driver

---

### Post by chips24 on 2008-02-04
my driver works, but my software is... well, lets say corrupt, this is hard to explain when i cant conect to the internet with ubuntu , im using windows vista, **vista go bye bye** when i get my wireless working on ubuntu.

---

### Post by borris.morris on 2008-02-05
Ok, you're not making much sense. What is the exact hardware, what version of Ubuntu? What software is "corrupt?" Etc...

---

### Post by chips24 on 2008-02-05
i have a HP pavilion vd2000, Ubuntu 7.10 AMD 64 Turion,Nvidia ge force go 6150, 150 gig hard drive and daulbooting windows vista, the software that isnt working is the network configuration.

---

### Post by borris.morris on 2008-02-06
Ok, well what i suggest is to use WICD. 

"Installing Wicd in Ubuntu

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras 

where feisty is your version of Ubuntu (Dapper, Edgy, Feisty, Gutsy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd.

In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

In KDE, you'll need to make a desktop file, so see this post for the directions on how to fix it up. "

That's the exact instructions from their website, wicd.sourceforge.net

---

### Post by nmartine on 2008-02-06
Go to terminal and type lspci, copy and paste that here.

---

