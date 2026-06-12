---
title: "trying to login as root..."
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-19
Hi,

I just installed breezy yesterday and I'm a total newb, obviously, and apologize for my lack of skill at this point...

I'm trying to login as root to edit the /etc/hosts file.  I have two problems:

1.  In a terminal window, when I type "su root" then enter a pwd I get a failure.
2.  I don't recall entering a pwd for root during the install and am taking shots in the dark at the pwd.  Can I edit a user file somwhere to reset my pwd?

gs

---

### Post by taurus on 2006-03-19
Root account is disable in Ubuntu.  So if you want to edit /etc/hosts, use sudo and when it asks you for a password, use the same on that you log in with.  In other words, if you need to modify system files, use sudo instead...
```

sudo gedit /etc/hosts

```

---

### Post by jrib on 2006-03-19
You should be using sudo instead of trying to login as root.  See [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by guysmiley on 2006-03-19
Alright... I've dug deeper but am still at a lost...

I found [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions) but receive error:
"unable to lookup  via gethostbyname()"

Help, please!

---

### Post by taurus on 2006-03-19
What command did you run when you got that error?  And what does /etc/hosts look like anyway?
```

more /etc/hosts

```

---

### Post by walvirch on 2006-03-19
Had the same problem. You have to install with "expert" mode when the initial screen (window) comes up after booting with the "install" CD. Then you will get the option to enter a Root password as part of the install. This will allow you to use the terminal mode as "su". Additional permissions for administration functions have to be set in the "visuo" file.See the documentation for sudo for more info. This applies to Kubuntu also.   -Walt

---

### Post by taurus on 2006-03-19
[QUOTE=walvirch]Had the same problem. You have to install with "expert" mode when the initial screen (window) comes up after booting with the "install" CD. Then you will get the option to enter a Root password as part of the install. This will allow you to use the terminal mode as "su". Additional permissions for administration functions have to be set in the "visuo" file.See the documentation for sudo for more info. This applies to Kubuntu also.   -Walt[/QUOTE]
You don't need to pick the "expert" mode during installing process.  Give root a password if you REALLY want to as
```

sudo passwd root

```

---

### Post by guysmiley on 2006-03-19
Typing in "more /etc/hosts" gives me the guts of the file but I need to edit it in order to put my "host name" back in.  I can no longer edit it through System -> Administration -> Networking (no window comes up at all - speaking of which, no window comes up for Users and Groups either).

I get that error when I type "sudo gedit /etc/hosts" or even just "sudo gedit".

Thanks for the help!

---

### Post by taurus on 2006-03-19
I guess your /etc/hosts is hosed!!!  Therefore, you may want to boot your machine into single mode or recover mode and edit your /etc/hosts with nano then...
```

nano /etc/hosts

```

---

### Post by guysmiley on 2006-03-19
Actually, "sudo" alone gives me error "sudo: unable to lookup  via gethostbyname".

Is this because I changed my Host Name from what it was to nothing at all?

---

### Post by taurus on 2006-03-19
[QUOTE=guysmiley]Actually, "sudo" alone gives me error "sudo: unable to lookup  via gethostbyname".

Is this because I changed my Host Name from what it was to nothing at all?[/QUOTE]
Yip.  So, reboot your machine and at the GRUB menu, pick the recover mode and boot from that.  After booting, you will see a prompt so no need to log in or anything but be careful, you are root.  Modify your /etc/hosts with nano (text editor, not GUI editor like gedit because you are not using any X right now).  Save it and reboot to mornal and see what happens...

---

### Post by guysmiley on 2006-03-19
K,

So that's not it...  Now my boot process is painfully slow and every click I make takes 3 minutes to respond...

I'm going to change my hosts file back.  Any other ideas why I might get the "sudo: unable to lookup via gethostbyname()"?

---

### Post by taurus on 2006-03-19
Again, what does your /etc/hosts look like???  May want to check your /etc/resolv.conf as well...

---

### Post by guysmiley on 2006-03-19
127.0.0.1 localhost.localdomain webserver

#The following lines...
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcaastprefix
ff02::1 ip6-allnodes
ff002::2 ip6-allrouters
ff002::3 ip6-allhosts

..

resolv.conf:
search basement
nameserver 192.168.1.1

[COLOR="Blue"]What do you make of this?[/COLOR]

---

