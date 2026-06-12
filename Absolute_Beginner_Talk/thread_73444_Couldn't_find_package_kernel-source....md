---
title: "Couldn't find package kernel-source..."
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by TraderEyal on 2005-10-09
Hi, I'm trying to install a network driver and in order to do that I need the kernel source. I'm trying 

apt-get install kernel-source-2.16.12-9

but getting couldn't find package error.. the headers were installed fine in /usr/src

any advise?

I do not have access to the net from that machine so will need a solution that takes that into consideration..

Thanks
Eyal

---

### Post by Knome_fan on 2005-10-09
I think it's called linux-source and if you don't have acces to the net from your ubuntu machine, you can download it to an other computer from here:
[http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12](http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12)

Then transfer it to your ubuntu machine and install it with ```
 sudo dpkg -i linux-source-2.6.12_2.6.12-9.22_all.deb 
```

---

### Post by TraderEyal on 2005-10-09
Hey Knome, Thanks!

I can see now in /usr/src a linux...bz2 

What is this file? Do I need to "unzip" it?




[QUOTE=Knome_fan]I think it's called linux-source and if you don't have acces to the net from your ubuntu machine, you can download it to an other computer from here:
[http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12](http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12)

Then transfer it to your ubuntu machine and install it with ```
 sudo dpkg -i linux-source-2.6.12_2.6.12-9.22_all.deb 
```[/QUOTE]

---

### Post by Perfect Storm on 2005-10-09
Unzip it.

```

cd /usr/src
sudo tar --bzip2 -xvf <insert name>

```

---

