---
title: "not going to runlevel 2"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by GLMnet on 2007-12-25
Hi, i´ve been played with a machine I have and I dont know what exactly I´ve done but my ubuntu now boots to runlevel S, that its: root@pc: prompt

i have to write init 2 so it loads the rest of it.

What I really wanted to do was to start without loading X so I used the service manager sysv-rc-conf and removed serveral X 

any ideas?

---

### Post by taurus on 2007-12-25
One option is to remove gdm so it won't boot into GUI login screen.

```
sudo apt-get remove gdm
```
And if you want to start X, just type

```
startx
```
from the prompt.

---

### Post by GLMnet on 2007-12-25
yes, the problem now is that it doesnt go to runlevel 2 so it wont load services and I have to write init 2 and all services loads.

---

### Post by taurus on 2007-12-25
Are you booting into recovery mode?

---

### Post by wormser on 2007-12-25
This will work.  I got it from [here]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html").   There is a lot more info on runlevels there.

> If you wanted runlevel 3 to be the default, then you need to edit /etc/inittab.

# The default runlevel.

id:2:initdefault:

You&#8217;d change the &#8216;2&#8242; to a &#8216;3&#8242;.

```
gksudo gedit /etc/inittab
```

---

### Post by GLMnet on 2007-12-25
> **taurus said:**
> Are you booting into recovery mode?

May be. I am not so sure.
I did change this in grub.conf
What I did is to add a new set title/root/kernel/initrd/quiet at the top of them, is top one default?

change from this: 
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3010627a-db60-4f31-9443-77c5216f2893 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

to this

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3010627a-db60-4f31-9443-77c5216f2893 ro single acpi=force
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

I just wanted to remove splash (what an ..) may this be my problem?

---

### Post by taurus on 2007-12-25
You are booting into recovery mode; that's why you have to start all the services by hand.  If you don't want to see the splash, just remove **quiet splash** at the end of the kernel and the **quiet** after initrd line.

```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3010627a-db60-4f31-9443-77c5216f2893 ro 
initrd /boot/initrd.img-2.6.22-14-generic


```

---

### Post by GLMnet on 2007-12-25
it worked :) Thank you

---

