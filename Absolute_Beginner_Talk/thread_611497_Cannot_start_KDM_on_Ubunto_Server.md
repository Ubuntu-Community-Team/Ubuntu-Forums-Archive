---
title: "Cannot start KDM on Ubunto Server"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by sin_bad on 2007-11-13
hi all , I  need help please 

on ubuntu server I installed  KDE  using this command :
sudo apt-  install  KDE
when it came back I tried to start it 
etc/init.d $  sudo start kdm 
nothing came out 

install KDM  and tried but nothing change . still in command line mode  , 

Can any one help

---

### Post by mkoehler on 2007-11-13
You should run```
/etc/init.d/kdm start
```

Cheers!

---

### Post by sin_bad on 2007-11-13
> /etc/init.d/kdm start

thats what I did ,, it comes back with no response

---

### Post by jordanmthomas on 2007-11-13
Installing kde does not install kdm I don't believe.
try installing kdm
```
sudo apt-get install kdm
```
followed by
```
sudo /etc/init.d/kdm start
```
good luck.

---

### Post by sin_bad on 2007-11-13
> **jordanmthomas said:**
> Installing kde does not install kdm I don't believe.
try installing kdm
```
sudo apt-get install kdm
```
followed by
```
sudo /etc/init.d/kdm start
```
good luck.

I did exact the same , it shows nothig ...  I am going to reinstall it again and  see if it does works or  not ...

I am very confused by the system folders , I dont know which is for which...  

is there any documentation available for the directories ..

---

### Post by jordanmthomas on 2007-11-13
first, try pressing ctrl - alt - f7 to see if it shows kdm.
If not, ctr - alt - f1 will bring you back.
Well, it's also still possible you don't have X installed.
If you're unsure of what packages to install, this will get you everything you need
```
sudo aptitude install kubuntu-desktop
```
You'll still have all your server stuff, along with the standard install of kubuntu.

---

### Post by sin_bad on 2007-11-13
> **jordanmthomas said:**
> first, try pressing ctrl - alt - f7 to see if it shows kdm.
If not, ctr - alt - f1 will bring you back.
Well, it's also still possible you don't have X installed.
If you're unsure of what packages to install, this will get you everything you need
```
sudo aptitude install kubuntu-desktop
```
You'll still have all your server stuff, along with the standard install of kubuntu.

thanks for help ....
I did reinstall it again , and reinstall kde then I checked its existence through aptitude ,, it is sitting there in installed programs area ...

I tried alt-ctrl-F7  ..... no way 

I want the system to be equipped by the minimum  requirements  , so I dont know is it necessary to install KDM and kubuntu-desktop or not 

help.. still needed

---

### Post by jordanmthomas on 2007-11-13
kubuntu-desktop is not required, I just thought you might like it.
You'll want to install this so that you have X (KDE must have X to run, but it is not a dependency of the kde package)
```
sudo apt-get install x-window-system-core
```

---

### Post by sin_bad on 2007-11-13
Ok ..   stay with me
I did  install x-window-system-core   , but  the problem still there , 
etc/init.d $ sudo  kdm  start 
  

-bash kdm: command not found 

other sugesstions ?????????

---

### Post by maybeway36 on 2007-11-13
Make sure xorg and kdm are installed, then type
```
sudo /etc/init.d/kdm start
```

---

### Post by jordanmthomas on 2007-11-13
If you insist on changing into the directory to run kdm, you will need to put ./ in front of the kdm command.
```
cd /etc/init.d
sudo ./kdm start
```

However, this is an unusual method and most people just use the full path to kdm.
If you can't figure it out, I believe kdm will start itself when you reboot.

---

### Post by sin_bad on 2007-11-13
thank you guys .... Im in now  ..

for beginners .................................

1.sudo  apt-get install kde
2. [COLOR="Red"]sudo apt-get install x-window-system-cor[/COLOR]    //added after Jordan post No.15
3.sudo  apt-get install kdm
4. sudo  /etc/init.d/kdm start
5.enjoy  your desktop..

thats all folks ..................................

---

### Post by jordanmthomas on 2007-11-13
Don't forget the xserver package as well (especially since it's what turned out to be your problem).

---

### Post by sin_bad on 2007-11-13
> **jordanmthomas said:**
> Don't forget the xserver package as well (especially since it's what turned out to be your problem).

[B]Hey  ...  Jordan

What is that xserver  ??
do I need it   ??[/B]

---

### Post by jordanmthomas on 2007-11-13
Yes, remember this?
```
sudo apt-get install x-window-system-core
```
Without it, kdm will not start.

---

