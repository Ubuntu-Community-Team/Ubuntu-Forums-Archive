---
title: "network"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by bmenge on 2007-02-21
ok I was trying to get galleon set up on my box and messed things up beyond what I can fix.  
I know what I did wrong I think but I can't fix it.  I had read that I need to change the /etc/host The to the "actual" ip address not 127.0.01 that apperently is wrong I can now not connect to the internet.  I went to change the file back to what it was and got this in the terminal.  
"unable to lookup brian-desktop via gethostbyname"

I tried to then change it by opening it from places and was able to but could not save any  changes.. Can I get into the file this way and save it or is it only possible to get there in the terminal via sudo?  I also tried to get to the network settings via system/administration/networking.  and it would not open anything just spin disk and bring up new tabs on bottom tool bar that never materialize to anything then disaper.


I am running off a live cd right now and can connect to the internet that way

---

### Post by tgalati4 on 2007-02-22
Well you discovered what the Live CD is good for.  Can you mount the disk and then edit the host file?
sudo mount /dev/hda1
cd /etc/hosts
sudo nano hosts

127.0.0.1 localhost (this is required)
127.0.1.1 yourhostname (use this line if DHCP--auto IP assignment)
192.168.0.whatever  yourhostname  (use this line for static assignment)


You have discovered one of the few things in Linux that will really screw you up.  Mess with the host table and you have lost your identity in everything you do.  Try deleting /usr with the command sudo rm -R /usr and see how long your system stays up before it takes dump.

I'm sure there's a page with stupid Linux tricks.  You stumbled upon one of them.

---

### Post by bmenge on 2007-02-22
I hadn't thought to mount the drive from the Live CD I guess that quick thinking will come with time

Thanks but I had a fresh install with only a couple of packages installed so I took the easy way out and reinstalled.

---

