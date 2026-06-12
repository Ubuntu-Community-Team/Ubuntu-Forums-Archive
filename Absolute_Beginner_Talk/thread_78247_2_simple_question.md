---
title: "2 simple question"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by bigboss2200 on 2005-10-18
hi guyz..

well.. as a new NoOoOoB.. i have 2 simple questions..

1- how can i install .rpm files into ubuntu..?

2- where can i download ubuntu files..? such as "video/audio players and codecs"..?!

thanks :)

---

### Post by Pablo_Escobar on 2005-10-18
1. apt-get "alien" package and then alien -D package.rpm

It's better to look for a deb package instead of rpm. Rpms weren't made for Ubuntu :)

2. Through Synaptic or apt-get, whichever You prefer.

---

### Post by Gustav on 2005-10-18
You should be quite careful installing stuff that does not belong to ubuntu and always search synaptic before installing it.

To be able to install all the packages you can add the universe and multiverse repositories. Look at [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Some multimediapackages are not availible there due to legal reasons, how to install them can be found here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Perfect Storm on 2005-10-18
1) It's not adviseble to install .rpm files on Ubuntu. Ubuntu is based on Debian which uses .deb. Though the Alien application can convert .rpm to .deb, there's no guarentee that it works and might screw up your system.

2) To install stuff on ubuntu, there's several way. The first thing is to look in the synaptic Package Manager. You'll find it in the **System** tab ---> Adminstration.
To install a .deb file which you have downloaded somewhere, open the terminal and write either:

cd /where/the/.deb/file/is
sudo dpkg -i XXXXXXXX.deb

or 

sudo dpkg -i /where/the/.deb/file/is/XXXXXXXXX.deb

(X shall be replace with the name odf the file you downloaded)

To get the codecs: [ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb](ftp://cipherfunk.org/pub/packages/ubuntu/pool/main/w/w32codecs/w32codecs_20050412-0unofficialubuntu2_i386.deb)

To make Ubuntu play DVD: [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)

---

### Post by bigboss2200 on 2005-10-18
thanks for ur quick reply.. but..

i dont have an internet connection in Ubuntu coz im using an internal creative 56KB modem.. so it wont work in Ubuntu..

so.. any other suggestions..?!

---

### Post by Pablo_Escobar on 2005-10-18
About modem - the best way is to buy an external modem I'm afraid. They're very cheap, so that shouldn't be a problem.

---

### Post by bigboss2200 on 2005-10-18
thanks all for the answer..


Pablo_Escobar .. unfortunatily i dont have any internal modem.. so these commands will not work :(

Gustav .. Thanks for the links.. but they r all based also in an internet connection wich i dont have in my Ubuntu

Artificial Intelligence .. Thanks aaaaaaaaaaaaaaaaaaaaaalot for the links.. and im downloading some .rpm for Fedora Core & .deb for my ubuntu.. thanks again :D

Pablo_Escobar .. i think in gonna buy one soon :)..

thanks all

---

