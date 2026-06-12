---
title: "Internet Connection - a very frustrating problem"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-05-25
I keep reinstalling Ubuntu and it works fine after a fresh install. I am very careful to add just one program at a time and reboot and test to see if I can still access the internet.  Every thing works fine until the next day and then no matter what I do I cannot access the internet or the repositories.  It is a dual boot and when I boot into Windows I can connect to the internet just fine, but Ubuntu will not connect.  Then I have to reinstall and start all over again.  I am using 7.04 (64) on a PC Chips A33G motherboard with an amd64 processor - to which I have added a GeForce MX4000 graphics adapter.  When I ping from the terminal everything shows that I am connected to the internet.  When I replace the nameserver ip in the /etc/resolv.conf I cannot even connect to the network at all.

---

### Post by lilro on 2007-05-25
dont turn it off everyday. it shortens your computers lifespan.

---

### Post by ffderrick on 2007-05-25
From what I have gathered, the 64 bit ubuntu doesn't perform better than the 32 bit version. (except in specific areas)  I haven't had much luck with any 64 bit distro.   Try using the 32 bit version.   That's what I use and it seems to run as fast as the 64 bit without the headaches.
There are driver problems associated with 64 bit Operating Systems and 32 bit drivers.

---

### Post by WhiteSphinx on 2007-05-25
I must add that I never had any network problems with Edgy.  I did have an internet problem but that was a DNS problem.  This is something different.:(

---

### Post by lazyart on 2007-05-25
Have you tried setting a static IP?  I have this problem from time to time-- my windows boxes all run fine with DHCP, one ubuntu box is happy also, but the other two won't work unless i go static.

Odd because they do receive addresses by DHCP but they can't seem to communicate to the outside world with them.

---

### Post by vanadium on 2007-05-25
Try the following: edit /etc/network/interfaces and remove all but the next two lines. Before doing that, copy your current file as a backup

In a command prompt

sudo cp /etc/network/interfaces /etc/network/interfaces.org
gksudo gedit /etc/network/interfaces 

gedit will start. Delete all lines except for:
```

auto lo
iface lo inet loopback


```

Restart the machine and see if it works well.

Network manager will write stuff in that file. For me, this was a problem when I moved locations. At work, I can only connect with a fixed IP. The configuration is then written into /etc/config. When starting up at home, the gnome desktop would take ages to appear. Cleaning up etc/config solves the problem.

In order to automatically start with a "clean" /etc/network/interfaces I did the following:

Create a clean /etc/network/interfaces called /etc/network/interfaces,default

Then I edited /etc/init/networking which is the script that initialises networking at boot time. In the beginning of the file, after the PATH statement, I added

cp /etc/network/interfaces.default /etc/network/interfaces 

Thus, before the network was fired up, the existing /etc/network/interfaces is replaced with a "virgin" copy containing only the automatic lo, and it is all left to network manager to autodetect networks (at my home) or to me to change location to "work" usng network manager when I am at work.

By the way, this way, the network does not cause delays during booting.

---

### Post by WhiteSphinx on 2007-05-25
None of the above suggestions worked.  It turns out that it is a nameserver problem.  I can get google and I can link to some sites from goggle but I cannot get yahoo at all and I cannot get most of the sites on my favorites list.  Even though they show up on google I still can't get them.  But I can get them with Windows. Changing the nameservers in /etc/resolv.conf does not work either

When I ping yahoo.com from the terminal screen I get all my packets returned with no errors and no losses. But still neither of the browsers will work for at least half of the internet.

---

### Post by sso71 on 2007-05-25
I am having the same problem but using 32bit i386 version. I have the same machine dual boot to Edgy and Feisty, Edgy connects perfectly, but not the Feisty. I don't know how to fix it. I think I start seeing this problem after I one time put it to hibernate mode. Someone might know better. Thanks!

---

### Post by bottleneck on 2007-05-26
I have the same problem. My internet connection with feisty (on AMD64) goes very slowly after 5-6 min of good connection. With edgy I never had this kind of problem..
Is this problem concerned with kernel??

---

### Post by Austin_KW on 2007-05-26
try disabling ipv6 ?
edit /etc/modprobe.d/aliases and change the ipv6 line to
alias net-pf-10 off #ipv6

then reboot.

---

### Post by WhiteSphinx on 2007-06-06
This did not work either

---

### Post by WhiteSphinx on 2007-10-28
Okay this is too cool.  Problem solved.  This should work for anyone with an A33G PC Chips Motherboard or for anyone with an SiS190/191 ethernet.

First do this:

```
export EDITOR=gedit && sudo visudo
```

This will bring up the sudoers file.

Replace the following line (because of a bug)

> Defaults !lecture,tty_tickets,!fqdn

with:

> #Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

Add this line to the end of the sudoers file:

> username ALL=NOPASSWD: /sbin/ifconfig
Be sure to replace "username" with your own username.

Then open System>Preference>Sessions

Click Add

_N_ame > Configure LAN
_C_ommand > sudo ifconfig eth0 mtu 1492

Now you will be able to access the internet with you SiS190 Ethernet after you restart.

---

