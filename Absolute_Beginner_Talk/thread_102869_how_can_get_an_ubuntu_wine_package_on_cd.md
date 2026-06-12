---
title: "how can get an ubuntu wine package on cd"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by tay on 2005-12-13
their is only info for repositories, and i need something for my computer without a networking card.

---

### Post by aysiu on 2005-12-13
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by tay on 2005-12-13
sahai@sahaihost:~$ cp /var/cache/apt/archives/wine_0.9 .2-winehq-1_i386.deb /home/sahai/Desktop
sahai@sahaihost:~$ cd ./Desktop
sahai@sahaihost:~/Desktop$ ls
desktop2    Screenshot.png                wine vagcom
driver      VAG-COM Release 311-2.lnk
Incomplete  wine_0.9.2-winehq-1_i386.deb
sahai@sahaihost:~/Desktop$

thanks. you helped me there.

i'm putting a together an add on cd for this old computer that has a rs232 port.

---

### Post by tay on 2005-12-13
help!!   i need libstdc++6 for wine
this is not in my archives..

what do i do know?

---

### Post by tay on 2005-12-13
i did'nt know you could download packages 
from [http://packages.ubuntu.com/hoary/libs/](http://packages.ubuntu.com/hoary/libs/)

---

### Post by tay on 2005-12-13
and i planned to use my usb drive

is their way to use apt-get to install this small file from a usb flash drive

if i burn a cd it will work, because synaptic has the add from cd option.

i used dpkg to install wine.

---

### Post by bfonseca on 2005-12-13
[QUOTE=tay]help!!   i need libstdc++6 for wine
this is not in my archives..

what do i do know?[/QUOTE]

hi you should be able to get the libstdc++6 from synaptic. I got mine there and my wine works great...Although i remember not finding it there when i first looked ...when i firsted looked I typed the full name(that didnt work) then I tried just part of the name like libstd and it gave me a number of packages with that including the libstdc++6...I hope that works for you
Brian

---

### Post by tay on 2005-12-14
thanks, i just finished setting up wine and vag com and my ubuntu pc that does'nt have a networking card.

because libstdc++6 was not in my archives, i reinstalled it again, and i got it to be in the archives, i also had to get gcc-base somtin.. but that was it.. whew.

---

