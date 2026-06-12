---
title: "networking 2 ubuntu computers"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-03-17
Hello! :)  I have 2 computers running ubuntu the first one is running ubuntu dapper with a kubuntu desktop. The second computer is running ubuntu dapper. They both have ethernet cards. I also have a 25 foot ethernet crossover cable. how do I configure the ubuntu computers to share a internet connection or files? The first computer is the one connected to the internet it is a Gateway GP6 with a 4000655 motherboard, 566 Mhz processor, 512 sdram, 80 GB western digital HD and a Nvidia Geforce MX4000 video card, liteon DVD burner. It is connected to the internet by a Zoom v92 serial modem. The second computer is a Dell XPS T500 500 Mhz, 512 sdram, IBM-deskstar 15 GB HD, Nvidia geforce MX 4000 and a liteon DVD rom CD-RW, no modem. 
 I would like to connect computer 1 to computer 2 where computer 1 will share internet connection with computer 2. I have tried many different times to get the computer to share connection. I set the IP on computer one to 192.168.0.1 subnet gateway 255.255.255.0 gateway address "blank".  I set computer 2 IP to 192.168.0.2 subnet gateway 255.255.255.0 gate way address 192.168.0.1. I am completely lost and cannot make it work........:confused:  Am i doing it wrong? if so how do i correct it?

---

### Post by Fataltragedy2 on 2007-03-17
Are they in the same work group? 

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
gksudo gedit /etc/samba/smb.conf

Find: workgroup = <name>

replace with:   workgroup = new_domain_or_workgroup

sudo testparm
sudo /etc/init.d/samba restart

---

### Post by cookieforyou on 2007-03-17
'Firestarter' (firewall GUI tool) has internet sharing setup included.

---

### Post by stonerrob420 on 2007-03-17
firestater doesnt work for me......and the samba config thingy doesnt work......I know the card and the cable work because i can hook a windows machine up and share internet connection......
 The way i first done it was to use sudo ifconfig eth0 192.168.0.1 on machine 1
and then sudo ifconfig eth0 192.168.0.2 on machine 2. I can ping each machine from the other machine but cannot stil share internet connection. They are communicating but not sharing files or connection to the internet. I'm still lost:confused: :) :lolflag:

---

### Post by drs305 on 2007-03-17
I use FTP file sharing. I am a new Linux user and it was easy to set up via this link:

[http://ubuntuforums.org/showthread.php?t=218630%20](http://ubuntuforums.org/showthread.php?t=218630%20) 

Good luck.

---

