---
title: "Smartlink Modem"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by DoeRayMe on 2005-09-22
I used the guide on this site to install the smartlink modem deb files with daemen

but it did not create /dev/slamr0 *i think the file is called*

am i missing something?

i have a SmartLink PCI562 modem

---

### Post by DoeRayMe on 2005-09-22
[QUOTE=DoeRayMe]I used the guide on this site to install the smartlink modem deb files with daemen

but it did not create /dev/ttySLO1 *i think the file is called*

am i missing something?

i have a SmartLink PCI562 modem[/QUOTE]
 anyone? please i could really do with some help

thanks in advance

---

### Post by Kapre on 2005-09-22
[QUOTE=DoeRayMe]anyone? please i could really do with some help

thanks in advance[/QUOTE]

DoeRayMe - I was just looking on the Ubuntu Guide and found a section regarding the  Modem Driver for Smartlink. The guide is down for repairs but on my printed copy (which I keep handy) this is what is said:

1. Make sure extra repositories are added to the list
uname - r (must be 2.6.10-5-386)
wget -c [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9).
sudo dpkg -i sl-modem-modules-*.deb
sudo apt-get install sl-modem-daemon

Hope this can help.

K

---

### Post by DoeRayMe on 2005-09-22
[QUOTE=Kapre]DoeRayMe - I was just looking on the Ubuntu Guide and found a section regarding the  Modem Driver for Smartlink. The guide is down for repairs but on my printed copy (which I keep handy) this is what is said:

1. Make sure extra repositories are added to the list
uname - r (must be 2.6.10-5-386)
wget -c [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9).
sudo dpkg -i sl-modem-modules-*.deb
sudo apt-get install sl-modem-daemon

Hope this can help.

K[/QUOTE]
EDIT: you missed part of the url, found the download anyway

thanks, will see if it works

---

### Post by DoeRayMe on 2005-09-22
right modem works now, thanks alot

just penggy having problems with connecting, know anything about penggy?

---

### Post by DoeRayMe on 2005-09-23
[QUOTE=DoeRayMe]right modem works now, thanks alot

just penggy having problems with connecting, know anything about penggy?[/QUOTE]
 Very strange, i re-booted and now my modem does not work

something to do with sl-modem-daemon i think

any ideas?

---

### Post by DoeRayMe on 2005-09-23
[QUOTE=DoeRayMe]Very strange, i re-booted and now my modem does not work

something to do with sl-modem-daemon i think

any ideas?[/QUOTE]
 Anyone have any ideas?

---

### Post by DoeRayMe on 2005-09-23
Please help me someone

---

### Post by foxiness on 2005-09-24
[http://ubuntuforums.org/showthread.php?t=65409&page=2&highlight=modem](http://ubuntuforums.org/showthread.php?t=65409&page=2&highlight=modem)

---

### Post by DoeRayMe on 2005-09-24
[QUOTE=foxiness][http://ubuntuforums.org/showthread.php?t=65409&page=2&highlight=modem](http://ubuntuforums.org/showthread.php?t=65409&page=2&highlight=modem)[/QUOTE]
 that worked, untill i re-booted then modem vanished

---

### Post by foxiness on 2005-09-24
[QUOTE=DoeRayMe]that worked, untill i re-booted then modem vanished[/QUOTE]
 this driver notworking on hibernate mode if not this than i think because you install this driver from more one source!

---

### Post by DoeRayMe on 2005-09-24
[QUOTE=foxiness]this driver notworking on hibernate mode if not this than i think because you install this driver from more one source![/QUOTE]
 Doesnt matter, got ADSL modem installed and using it to connect to AOL

---

### Post by Adalgisel-Grimo on 2005-10-20
Same problem :

1. installed sl-modem-daemon
2. changed  SLMODEMD_COUNTRY=GERMANY in /etc/default/sl-modem-daemon 
3. setup and autodetection worked
4. connected via Thunderbird :) 

5. Reboot: modem vanished :( 
6. Reboot: after a few sedonds the modem activated itself :confused: 

NOW ?

Synaptic shows in the dependencies-section for sl-modem-daemon:
in conflict with: sl-modem-modules  [translated from german, hope it's correct  ]

any idea ?

---

### Post by foxiness on 2005-10-28
did any one get it work with Breezy ? 

i get it work but with out sound and now after some change on "reinstall linux-'uname -r' and other start with linux-xxxx .

how can i get it work like before and when ubuntu team will start support modem ?

---

