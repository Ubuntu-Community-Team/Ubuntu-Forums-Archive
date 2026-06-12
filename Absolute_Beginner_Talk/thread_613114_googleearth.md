---
title: "googleearth"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by leo1 on 2007-11-14
trying to install googleearth on ubuntu 7.10, 32 bit.could not . dounloaded the bin file from google and have it on my desktop. what would be the apropriate next step.
i have read the other google posts and am still confused.

---

### Post by Inxsible on 2007-11-14
Open a terminal and cd to the directory where you have you file.
Installing bin files is a 2 step process.

1) Make the file an executable```
sudo chmod +x *filename*
```2)Run it```
./*filename*
```

---

### Post by taurus on 2007-11-14
Try installing it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **GoogleEarthLinux.bin**
./**GoogleEarthLinux.bin**
```

---

### Post by jken146 on 2007-11-14
Read these:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by loyaleagle on 2007-11-14
You could also use Automatix 2.
It does it all for you!

---

### Post by loyaleagle on 2007-11-14
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by erfahren on 2007-11-14
Gutsy has googleearth in the repositories, in the Medibuntu repos I think.

*(Edited out instructions. jryprt's are better.)*


or just search Synaptic for it after adding the repositiry 
[Ubuntuguide Wiki - How to add extra repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

... no need for Automatix, especially now using Gutsy. Most everything is available in the repos.

---

### Post by jryprt on 2007-11-14
Look at this thread [http://ubuntuforums.org/showthread.php?t=588962&highlight=googleearth](http://ubuntuforums.org/showthread.php?t=588962&highlight=googleearth)  look at # 7 
for Feisty do these

Code:

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

Code:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

for Gutsy

Code:

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

Code:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

then try to install googleearth again

Code:

sudo apt-get install googleearth googleearth-data


it works great

---

