---
title: "Wine install question"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by fiskking on 2007-09-16
just recently tried to get  the repository's key for the wine program:

sudo wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

where ,after a couple of minutes, I recieved this message:

gpg: no valid OpenPGP data found

what happened?

---

### Post by Hospadar on 2007-09-16
I'm not really sure what the problem here is, but i've always had some wierd issues with the pgp key for the wine repo.  I either add the key right before I update/install wine, or just manually download the .deb from their repository.  If you manually download the deb, you can either a) install from the command line with ```
 dpkg -i <filename of .deb>
```or b) double click it, or c) move it to your package cache and then use apt-get or synaptic as normal.  It'll look something like this:
```
wget http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb
sudo cp wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb /var/cache/apt/archives
sudo apt-get update
sudo apt-get install wine
```you could replace the last line with "sudo apt-get install upgrade" if you already have wine installed or you could use synaptic, browse to wine and install upgrade the package from there.

just fyi so you know, /var/cache/apt/archives is where all packages are downloaded before they are installed, so if you put a package there that is in one of the repos that you have, apt will just install it from there as opposed to downloading it.

I almost forgot, the site to manually download the packages is: [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

