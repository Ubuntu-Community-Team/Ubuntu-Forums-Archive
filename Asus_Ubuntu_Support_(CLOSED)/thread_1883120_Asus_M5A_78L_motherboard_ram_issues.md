---
title: "Asus M5A 78L motherboard ram issues"
date: 2011-11-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Espera on 2011-11-18
Hi,

My current set up is: Asus M5A 78l USB3 motherboard
                      4gb Gskill ddr3 ram
                      AMD Athlon 640 x4
                      Zotac Geforce 210
its obviously not the most *** kicking machine going and the geforce 210 is a pretty out of date card (its a stop-gap card till i can afford a better one) but i thought i should post my system before i asked my question which is.

As you can see I'm running 4gb of ram and in windows the 4gb in the 64bit dxdiag shows up as 4gb, now I'm currently running the 64 bit natty and i only get 2gb ive tried moving the ram dimms into different dimm slots and have even tried going to 64bit oneiric and running Fedora 15 in 64 bit everytime each systems says i'm running 2gb. 

i had a look around these forums scoured the internet, asked fedora users (during the brief time i was a fedora user) played about with the BIOS settings and done a couple of full installs of 64bit systems and only the windows partition and the BIOS saw that i had 4gb on the board.

I'm just wondering now if this is a Mobo problem or a kernel problem or what as I'm now truly bloody stumped as to what it can be.
If anyone has experienced anything even remotely similar how did you go about solving it? as i would really like to get my full 4gb for obvious reasons.


Thanks in advance.

p.s I'm currently running natty in 64bit with gnome 2

---

### Post by BillyBoa on 2011-11-18
You checked the System Monitor and the RAM recognized is 2G only?

I'm sure that even Ubuntu 32bit recognize 4G without problem. You don't even have to install 64bit system to do that.

---

### Post by BillyBoa on 2011-11-18
There is a solution if everything is ok with your hardware

install the linux server


```
sudo apt-get install linux-server
```

Then boot choose from Grub menu the new kernel.

---

### Post by Espera on 2011-11-18
> **BillyBoa said:**
> There is a solution if everything is ok with your hardware

install the linux server


```
sudo apt-get install linux-server
```

Then boot choose from Grub menu the new kernel.

just grabbed the linux-server so i'll try it just now :)

---

### Post by Espera on 2011-11-18
Oh dear.... still says 2gb.
this is wholly dissapointing.

---

### Post by davetv on 2011-11-18
Is the BIOS detecting the RAM? That would be the first place I would look.

---

### Post by Espera on 2011-11-19
yeah the bios detects two ram dimms and also before i wiped my win7 partition (for various reasons) if i ran 64bit dxdiag it would register 4gig

---

