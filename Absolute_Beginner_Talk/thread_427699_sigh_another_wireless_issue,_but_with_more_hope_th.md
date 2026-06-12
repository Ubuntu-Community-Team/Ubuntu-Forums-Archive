---
title: "*sigh* another wireless issue, but with more hope than most people here"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by schmidtbag on 2007-04-29
This is probably obvious, but I'm using Feisty.

I own a TRENDnet TEW-424UB.  It's a USB adapter and it doesn't work at all.  Linux knows its there but thats it.  I used Crossover/Wine  to try installing the (Windows) software that came with it but got no luck.  I tried ndiswrapper but I have no idea how to use it.  I downloaded it, extracted it, and then wondered what to do seeing as how there were no instructions.

So, I gave up on my adapter and borrowed a friends'.  He has a D-Link DWL-122.  This time, it showed up in the network settings but it won't do anything else.  I tried Wifi-Radar to see if that would get me connected but it only made things more confusing.  Is there any tutorial on how to set up a wireless network?  Are both adapters incompatible?  Is there a tutorial on how to use ndiswrapper that isn't just for broadcom chipsets?

I researched for maybe 4 hours and can't find any answers, and I don't want to buy a new adapter because I'm not even sure if all my software and games will work (Nearly all of them are for Windows).  I would try downloading Edgy but for some weird reason, the Ubuntu homepage only has Dapper (if that's what 6.06 is) and Feisty.

---

### Post by orb9220 on 2007-04-29
Searched forums using TEW-424UB and saw this [http://ubuntuforums.org/showthread.php?t=383504&highlight=TEW-424UB](http://ubuntuforums.org/showthread.php?t=383504&highlight=TEW-424UB)

---

### Post by schmidtbag on 2007-04-29
Thanks for the quick reply, but all of those people were having issues, so I still need a tutorial to know how to use NDISwrapper and a tutorial on how to set up wireless networks.  If theres an automatic connection finder that's useless to me because there are 4 networks in the area.

---

### Post by bobplano on 2007-04-29
well firstly if you don't have access to the internet on the ubuntu side then [packages.ubuntu.com]("packages.ubuntu.com") is your friend. for the newest version of ndiswrapper you need to "make" it. if you have internet on ubuntu then use this command:
```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```
other wise you need to get the packages cpp, gcc, build-essential, linux-header-(kernel; use uname -r to find it out). then go to the terminal and go to the extracted directory and run 
```
sudo make
sudo make install
```
then you can run
```
sudo ndiswrapper -i */path/to/driver* *driver name*
```
you may need to copy system files which you can get off the cd and then run 
```
 ndiswrapper -l
```
and 
```
 sudo ndiswrapper -m
```
btw does anyone know how to compile source code into a .deb file because this seems to be a common problem and i wouldn't mind compiling the source code if i knew how

---

### Post by octoberdan on 2007-04-29
> **bobplano said:**
> 
btw does anyone know how to compile source code into a .deb file because this seems to be a common problem and i wouldn't mind compiling the source code if i knew how

Checkinstall: [http://packages.ubuntulinux.org/feisty/admin/checkinstall](http://packages.ubuntulinux.org/feisty/admin/checkinstall)
Be warned though, the packages it creates are far from production quality and are only for system management

---

### Post by digital_sabotage on 2007-04-29
...here's how i think i installed and used ndiswrapper ...easy way i thought

..start synaptic package manager ...search for "ndis" ...install the latest version of ndiswrapper ...should be "ndiswrapper-utils-1.8" ...that will also install the dependency "ndiswrapper-common" automatically.
...next install "ndisgtk" ...that's the graphical front-end for ndiswrapper ...after that is installed you should be able to go to >System>Administration>Windows wireless drivers ...a window will open allowing you to install a driver ...navigate to where your .inf file is and you should be good to go

...after that you should see your wireless card in >System>Administration>Networking ...you will need to specify the ssid and wep password there ...just type "any" beside ssid if you want to use un-encrypted signals (coffee shop etc.) ...then make sure wireless check boxes are "enabled" ...should configure and connect ...hope this helps ...good luck

---

### Post by schmidtbag on 2007-04-30
digital_sabotage - NDIS isn't in my package manager.

bobplanto - Your instructions didn't work, and for some reason, maybe because every single build-essential won't install.  I did nothing to prevent them from working.

---

### Post by bobplano on 2007-04-30
if you don't have to compile it, then don't. 1.8 works for a lot of things and you just need (i think) ndiswrapper-common and ndiswrapper-utils and then you can get ndiswrapper working

---

### Post by schmidtbag on 2007-04-30
Ok so I installed ndiscommon, ndisutils, and ndisgtk and they all successfully installed.  I see the Control Center option to set up the Windows Wireless stuff and that opens up but if I select the .inf file it won't add the device.  What do I do now?  Am I supposed to install the rest of ndiswrapper.tar.gz?  If so what am I supposed to do?  bobplanto's instructions only gave errors.

---

