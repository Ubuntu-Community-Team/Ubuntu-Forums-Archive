---
title: "Help with getbyhostname error"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-08-06
Hi, I just changed my hostname, And now I get the getbyhostname error whenever I use sudo.

Here are my logs:

/etc/hosts
```
127.0.0.1 localhost Ubuntu
127.0.1.1 Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

/etc/hostame
```
Ubuntu
```

---

### Post by hagfish on 2006-10-25
arrgh - I just did this to my system, too, by fiddling with /etc/hosts. I no longer have access to sudo, so I can't fix it. I have tried booting in restore mode and using [alt]+[ctrl]+[f1], to no avail. I tried booting using the live CD, but did not have permission to mount my root partition.

I am about to try a rescue CD. If that doesn't give me access to my hosts file, I will have to nuke the install from orbit. In future, i will *respect* the hosts file...
Cheers
Fraser

---

### Post by studentism on 2006-10-25
I'm assuming you used "sudo hostname foo" to change it, and you're trying to change it back with the same method?  Just tested that out on my own machine, and while it borks things over, you can execute "sudo bash" and then "hostname blah" to change it back.  Make sure you exit out of the root shell when you're done.

---

### Post by hagfish on 2006-10-26
SUCCESS! Booting into restore/safe mode never seemed to give me root access - I could never write the changes to my poor old /etc/hosts file. So I tried downloading, burning, and booting from [SystemRescueCd]("http://www.sysresccd.org/Main_Page"). I made a directory for my root Ubuntu partition:
```
mkdir /mnt/drive1
```
Then found my partition in dev - from memory it was hda6 - and mounted it:
```
mount /dev/hda6 /mnt/drive1
```
Dug in there and i was away!
```
vi /mnt/drive1/etc/hosts
```
It let me save my changes. Rebooting into Ubuntu and my sudo privileges are back. Much relieved that i don't have to reinstall 8)
The top line of /etc/hosts now reads:
```
127.0.0.1 localhost.localdomain localhost Gangees
```
where 'Gangees' is the same as /etc/hostname

---

### Post by CatKiller on 2006-10-26
For what it's worth, had you used a **sudo -i** first, you could have used exactly the commands above on the Ubuntu live cd.

---

### Post by hagfish on 2006-10-26
Ha! Oh well - live and learn.. And I did learn quite a bit during this fiasco. Thanks to studentism and CatKiller for your help with this. I shall now 'man sudo' :-D

---

