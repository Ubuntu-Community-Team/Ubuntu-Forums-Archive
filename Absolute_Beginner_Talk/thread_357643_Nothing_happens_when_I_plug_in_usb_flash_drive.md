---
title: "Nothing happens when I plug in usb flash drive"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by havedampton on 2007-02-09
I have a HP Pavilion dv6253cl, AMD Turion 64, nVidia GeForce Go 6150 graphics card

running 6.06

I would like to automatically mount by usb flash drive whenever I plug it in.  Right now, absolutely nothing happens when I plug it in.

thanks

---

### Post by amd-64 on 2007-02-09
At the prompt type

sudo apt-get install usbmount 

this should do the trick and it is the one I use. Alternatively, you can also try 

sudo apt-get install autofs

If you need to remove either of these packages, replace install with remove in the commands above

---

### Post by havedampton on 2007-02-09
ok

I tried both:

root@cicely:~# sudo apt-get install usbmount
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package usbmount
root@cicely:~# sudo apt-get install autofs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package autofs
root@cicely:~#

nothing.

suggestions??

---

### Post by amd-64 on 2007-02-10
Hmm. You may need to enable the universe repositories for apt-get. You will need to append one line to the sources.list file as shown below. Another alternative is to install synaptic and enable the repos and install from there. 

```

sudo -s  

echo deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe >> /etc/apt/sources.list

apt-get update

exit

```

Now try once more to install one of the two packages as in my message above.


If you want to try synaptic, use this

sudo apt-get install synaptic

---

### Post by mr.v. on 2007-02-10
havedampton--

after plugging in the flashdrive can you go to Places|Computer and see if it's there? (Places is  the middle menu at the top left of the upper panel).

---

