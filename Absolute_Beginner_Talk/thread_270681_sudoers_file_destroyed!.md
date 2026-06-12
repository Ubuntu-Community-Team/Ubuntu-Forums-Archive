---
title: "sudoers file destroyed!"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-10-03
somehow my sudoers file has a red x over it. i can no longer use sudo.
how can i fix/replace the file?

Thanks

---

### Post by moore.bryan on 2006-10-03
*reboot into recovery mode, then ```
aptitude reinstall sudo
```*

---

### Post by jinxjinx on 2006-10-03
didnt work. I tried it twise, but each time the sudoers file still has a little x over it...
can i manualy replace the file?

i installed a program called lessdiskes-terminal that i think caused this. but i cant uninstall it without sudo...

---

### Post by jinxjinx on 2006-10-04
ok it turns out my /etc/hostname file and /etc/hosts file are messed up.

i can change them but i dont know what to put there. my computer name is nephroid.

i dont know what a localhost is or a local domain...

please help

---

### Post by kerry_s on 2006-10-04
Here's mine->

hostname
```
KDE-JFS
```

hosts
```
127.0.0.1	localhost
127.0.1.1	KDE-JFS.opendns.com KDE-JFS

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by jinxjinx on 2006-10-04
which one is the computer name and which one is the user name?

and where did you get opendns.com?

thanks.

---

### Post by haxer on 2006-10-04
OMG need to abandom the ship malfuntion malfuntion :) just kidding all your help is here :) 8)

---

### Post by aysiu on 2006-10-04
I don't know anything about /etc/hosts, but you can fix sudo with this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by jinxjinx on 2006-10-04
the files in the link you sent me are fine. 
i need to fix my etc/hostname and etc/hosts files

but i dont know what names to put in. 
all i know is my user name and computer name.

---

