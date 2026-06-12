---
title: "Help update Ubuntu in Dual Boot in MacBook Pro 5.1"
date: 2012-02-09
forum: Apple Hardware Users
---

### Post by dresde on 2012-02-09
Hello all!

I have been using Ubuntu for a couple of years but I never register ere, since I never had such a big trouble. But now I'm almost out of resources and Google is not helping anymore!

So, I have a MacBook Pro 5.1, running Leopard (OS X 10.5.8). After several attemps I gave up of installing Ubuntu 11.10 in dual boot following the instructions here ([https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)), because it never worked. After installing, I tried to go into Ubuntu and nothing happen (black screen with white cursor on top-left).

Then a blogger suggested me to try with an older version. And apperently this is working fine: I know have Ubuntu 10.10 in dual boot, and I can just choose it in rEFIt at startup and it runs. The problem is I tried to update to Ubuntu 11.04 (Ubuntu itself tells me to do it the moment I switch on the WiFi connection), and after running the update I again couldn't log into Ubuntu anymore.

I believe it ahs something to do with the GRUB thing, which I don't really understand. During the install, I set it up on /sda3 (the Ubuntu ext4 partition), and during the update to Ubuntu 11.04 it prompted a window saying that grub had changed and I had to decide what to do...

So this is my question: how can I update Ubuntu so it still works?

Thanks a lot!

---

### Post by Ms. Daisy on 2012-02-09
Putting ubuntu on an apple takes a few more steps than putting it on a PC.  I asked the mods to move your thread to the "apple" forum- those folks will know how to help you!

---

### Post by sffvba[e0rt on 2012-02-09
*Thread moved to **Apple Users**.*


404

---

### Post by dresde on 2012-02-09
Hahaha, I know, it's killing me. If they thought about dual boot for windows with Bootcamp they should have already done some easy way to install Linux too.

Thanks for moving the post.

---

### Post by mapes12 on 2012-02-10
If you need quick access between Ubu and OS X then you may like to consider what I have done on my Macbook. 

Install a Virtual Machine such as Virtualbox (open source), VMWare Fusion or my favourite Parallels 7. Then install Ubu inside the virtual machine. It's just a mouse click to switch between the 2 OS's and you can save all your files in one place.

The downside is that you need a decent amount of memory. I upgraded my Macbook to 8GB and it positively flies. But I guess 4GB would be more than sufficient.

If this works for you then you can delete the current Ubu partition and free up the space for the rest of your system.

Good luck.

---

### Post by dresde on 2012-02-10
Thanks for the tip!

I though about going with virtual machines, but right now my Mac only has 2GB of memory so running 2 OS at the same time might make everything too slow. I actually like what I have right now (from Ubuntu I can access the Mac HD), it's just I have to find the way to update Ubuntu without loosing it!

---

### Post by dresde on 2012-02-13
So it's working now!!!! What I did: I update from Ubuntu 10.10 straight to Ubuntu 11.10 through the CD. This way I can still boot into Linux!!!

Only weird thing is: now rEFIt gives me two options to boot into Linux, one from HD and one from "Partition3". I assume I still have a problem with GRUB...

---

