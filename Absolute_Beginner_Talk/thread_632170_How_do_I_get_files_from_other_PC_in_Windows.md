---
title: "How do I get files from other PC in Windows?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by enjtpl on 2007-12-05
I have two computers in a router. How do I get files from other computer used Windows?

---

### Post by philinux on 2007-12-05
I've not used windows for ages but if I remember correctly you need to set up a shared folder. If you click on start help and search for shared folder it should tell you what to do. With the linux box you need samba.

---

### Post by pooper on 2007-12-05
you should be able to just right click the folder that you want to share and it will have an option in the  menu. Like share this folder or something. I did it using mac and ubuntu.
if you do it from ubuntu it should appear in windows under my network places, you will probably have to specify an address and I'm not sure how you open shared folders in ubuntu, i guess you need to find out the address again and connect to that.

---

### Post by misfitpierce on 2007-12-05
Can put into shared documents on windows and then go into network on ubuntu and find your home network router and connect to that pc, should then show shared folders.

---

### Post by Tanjer1588 on 2007-12-05
If your running on a windows xp network set up your windows system to share your files over the network, On you linux system if your useing ubuntu 7.10 you will need samba, if you Find sytem-config-samba in your synaptic package manager then you can go under system>administrator>samba and specify what folders are shared on your windows network. Then from your windows box if you go into my network places and then click view workgroup computers on the left side you should see your Ubuntu box with the samba name in it, you should be able to pull files from it. In ubuntu just have to go to networks and it should be right there.

---

### Post by jonandrews on 2007-12-05
My networking guide describes networking to move files between Windows & Ubuntu:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

---

