---
title: "How does one create an ISO?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by ed_d on 2005-11-15
I want to be able to take some bootable cds and make ISO files from them so if I need to burn one, as the original is damaged due to handeling. Any help would be great.

---

### Post by sethmahoney on 2005-11-15
[QUOTE=ed_d]I want to be able to take some bootable cds and make ISO files from them so if I need to burn one, as the original is damaged due to handeling. Any help would be great.[/QUOTE]

Gnomebaker, k3b, or Serpentine should be able to make an ISO for you.

---

### Post by davmac on 2005-11-15
From memory you can even right-click on the ISO and choose to burn it, although I tend to use GnomeBaker myself.

HTH,

Dave Mac

---

### Post by jdong on 2005-11-15
Use one of the three mentioned tools to create it. Note for simpler Data CD projects, Nautilus (the file manager) can do it for you from the Go->CD/DVD Creator menu. This can either burn directly to a recorder, or make an .ISO images of the compilation. It is not capable of making bootable ISO's, which means it'll be unsuitable for your needs.

---

### Post by Dr. Nick on 2005-11-15
I would persoanally use graveman, a gtk cd burner.

Put your bootable CD in the drive and open graveman - Go to duplicate cd option and set "duplicate from" to your cd drive and "write to" to iso file.

I havent done this before but I assume it will still be bootable when the iso is burnt back, may double check before the origional breaks :)

---

### Post by racecat on 2005-11-15
And if that isn't enough...

If you need to burn an ISO because you desperately need to move from Windows to Linux, there is a good, simple, free windows program that I've had luck with. Burnatonce.

---

### Post by kruz on 2005-11-15
open terminal

sudo apt-get install k3b
sudo apt-get -f install
sudo k3b

k3b is my fav, coming from knoppix to ubuntu

---

### Post by racecat on 2005-11-15
[QUOTE=kruz]open terminal

sudo apt-get install k3b
sudo apt-get -f install
sudo k3b

k3b is my fav, coming from knoppix to ubuntu[/QUOTE]


Amen, brother! It just works!

---

### Post by kruz on 2005-11-15
k-3-b 
the only burner on the sea

okay im not 50 cent forgive me
lol
but k3b is easy
and reminds of nero easy features and just set right up

good luck

---

### Post by jdong on 2005-11-15
(1) **apt-get -f install** is NOT necessary... though it doesn't do any harm if run without reason
(2) **sudo k3b** is incorrect. k3b is to be launched as an ordinary user, via **k3b** -- no sudo! Sudo may cause all kinds of permission hell later on when trying to run it as a normal user, and can potentially compromise the Linux security model.

---

### Post by ed_d on 2005-11-16
Found it under gnomebaker. Thanks again for all the help.

BTW, K3B is a great burner, but im finding gnome backer to be very close. I am coming off Core, and liking Ubuntu far more.

---

