---
title: "SuSE and Ubuntu: Use RPMs ?"
date: 2005-08-09
forum: Absolute Beginner Talk
---

### Post by mohsin on 2005-08-09
well guyz i have all 5 cd distro of SUSE .. 

 these cd's contain many rpms well how can i use for ubuntu is ther any way .. 


 to use rpm in ubuntu .. 

 like 


 xmms player i have to download it from net .. its rpm is on suse cd can i use that suse rpm to install on ubuntu if yes then HOW . thnx aa lot for replying 


 MOHSIN

---

### Post by manicka on 2005-08-09
Any package available for SuSE should be available as a deb through the repositories. 

Just use

sudo apt-get install packagename

or use synaptic and search for the package you want.

You could use 'Alien' to try and convert these SuSE rpms to debs,  but SuSe has a different directory structure to debian/ubuntu and you'll find that most of the packages won't work properly once converted.

---

### Post by Kimm on 2005-08-09
You dont need to use SuSE rpm's in ubuntu.

if you want xmms, type:

"apt-get install xmms" 

in your console, and that'll set you up. Otherwise, if you just have to use rpms for some wierd freaked out reason you can use the program alien to convert your packages to debian packages and install those using the built in package manager.

"dpkg -i <packagename>.deb"

---

### Post by mohsin on 2005-08-09
kz geting something 

 first of all thnx for replying you both 

 well get apt method works when you connected to internet ?

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=mohsin]kz geting something 

 first of all thnx for replying you both 

 well get apt method works when you connected to internet ?[/QUOTE]

Yep. It downloads software from the internet and installs it for you in a way so that it will work.

I would read this guide some if I was you:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by mohsin on 2005-08-09
already reading .. and geting much of the answers now ;) thnx a lot

---

### Post by aysiu on 2005-08-09
Yeah apt-get or Synaptic Package Manager is good if you don't have dial-up.

---

