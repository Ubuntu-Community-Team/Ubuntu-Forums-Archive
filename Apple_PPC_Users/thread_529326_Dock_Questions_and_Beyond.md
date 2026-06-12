---
title: "Dock Questions and Beyond"
date: 2007-08-19
forum: Apple PPC Users
---

### Post by Interstellar on 2007-08-19
I'm fairly new to Ubuntu, but I installed it on my ibook g4, and I got beryl installed and a few other non essential things installed. I am now trying to install the Kiba dock and my main question is if it can even be installed on a PPC Ubuntu box. I think the problem is with my Repos, because every time I try to apt-get update I get this error message 

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/fiesty/eyecandy/binary-powerpc/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/fiesty/eyecandy/binary-powerpc/Packages.gz)  

Which I understand is needed to install the Kiba dock, (what they actually do is a little fuzzy, but I think I get it). Anyways after I run the the other couple of commands to install it, it tells me that the Kiba dock can't be found. Since I'm so new, I'm not sure if you need more information or what the problem might be, but any help would be very wonderful.  Thank you.

---

### Post by Dark Star on 2007-08-19
**A small How to for installing a  dock **: Follow the steps and u will install Kiba Dock

```
sudo gedit /etc/apt/sources.list
```

Add the following lines to the end of the file:
```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Save and exit.Run from terminal window:
```

wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install kiba-dock kiba-dock-dev kiba-plugins
```

Configure and launch kiba dock from the applications menu. :clap: 

If this process fails then install the dock Using Synaptic manager.. Just Search Kiba in Manager and Right click it and Select Mark for Installation.. Click Apply and u are done :hap2: 

Hope its done now :)

Peas Ds

I also get that error but do continue the process everything work fine.. But am unable to know how to add applications in Kiba dock :):lolflag:

---

### Post by aantn on 2007-08-20
Isn't Trevinho's repository for i386 and amd64 only (and not ppc). Either way, I'm planning on making my own repository for ppc in a few days. I don't mind adding a few extra programs into it. I'll put kiba dock in if you'd like. See this for more information [http://ubuntuforums.org/showpost.php?p=3217926&postcount=4](http://ubuntuforums.org/showpost.php?p=3217926&postcount=4)

---

