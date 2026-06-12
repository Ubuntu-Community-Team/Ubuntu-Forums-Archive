---
title: "Sudo command broken?"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by CookieOrc on 2006-02-11
Evey time I try to do somthing in root like sudo ap-get I get this error
> sudo: unable to lookup Peri.example.com via gethostbyname()

or in gui mode I get somthing about an 'su' error occured. Everything else is workin fine. This occured after I installed a few new packages. I do not remember what they were. I cant even get into the package manager.

---

### Post by CookieOrc on 2006-02-11
Well is there anyway to roll back my computer or anything? So I can restore my settings. I am getting really fustrated and am just going to reinstall I do not know what else to do.

---

### Post by taurus on 2006-02-11
Look in your /etc/hosts to see what do you have in there!!!

---

### Post by CookieOrc on 2006-02-11
I am going to replace it with my old Hosts file but how can I without root privilages?

---

### Post by taurus on 2006-02-11
Here is what I have in my /etc/hosts

127.0.0.1       localhost.localdomain   localhost       taurus

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by CookieOrc on 2006-02-11
I have am trying that but I need the root privilages and with no Sudo command... I tried editing it and going throught the GUI


should i boot in recover mode and copy it?

---

### Post by jpkotta on 2006-02-11
[QUOTE=CookieOrc]I have am trying that but I need the root privilages and with no Sudo command... I tried editing it and going throught the GUI


should i boot in recover mode and copy it?[/QUOTE]
Yes.

You can see what packages you installed last from synaptic, in File -> History.  If you can determine that one of these caused the trouble, submit a bug report.

Another user messed up their hostname by deleting it from the network-admin dialog, so it could certainly happen without manual editing.

---

### Post by taurus on 2006-02-11
If you can't log into your system anymore for whatever reason, boot into single user mode (or init 1) and fix it.  ;)

---

### Post by CookieOrc on 2006-02-11
well i do not know if i can believe this ___ I did it in recovery mode and yet when I boot I am still under the old configuration... I rebooted and am now going to ctrl alt backspace

---

