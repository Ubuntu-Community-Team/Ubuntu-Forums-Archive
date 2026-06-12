---
title: "IP configuration"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by vtechstu on 2006-10-30
I was wondering if there was command that looks up a computers IP information.  More specifically, I'm looking for something that checks the type of IP of the system, either static or DHCP.  Is there a command that does this, or a series of commands that would do this?  I looked in the linux commands index and didn't come across anything.

Thanks in advance.

---

### Post by coolbian57 on 2006-10-30
> **vtechstu said:**
> I was wondering if there was command that looks up a computers IP information.  More specifically, I'm looking for something that checks the type of IP of the system, either static or DHCP.  Is there a command that does this, or a series of commands that would do this?  I looked in the linux commands index and didn't come across anything.

Thanks in advance.

Do you mean a program that will give you an IP adress?  Check out ```
dhclient
``` in the terminal.

---

### Post by wieman01 on 2006-10-30
A few other useful commands:
> ifconfig
> iwconfig
> route
> sudo gedit /etc/network/interfaces

---

### Post by vtechstu on 2006-10-30
Thanks to the both of you.  dhclient will not work, i've used before. I'm writing a script that finds out whether or not the systems is static or DHCP, if DHCP, assign it a static IP.  

unfortunately, i'm not running ubuntu, this will be done on FC3 equiv. systems, so the above commands do not work.  though i thought those commands would be universal to an extent, they don't seem to be.  this is my first time using fedora, so yea.  

thanks again

---

### Post by bsussman on 2006-10-30
> **wieman01 said:**
> A few other useful commands:

```
                              sudo gedit /etc/network/interfaces
```

```
gedit /etc/network/interfaces
```**(no sudo)**

or

```
cat /etc/network/interfaces
```or

```
less /etc/network/interfaces
```might be better commands to use - don't use an editor unless you intend to change files - especially system files.  The first altenative is less desirable since it relies on the assumption that you are not in a state that allows changing the file.

---

### Post by wieman01 on 2006-10-30
> **bsussman said:**
> might be better commands to use - don't use an editor unless you intend to change files - especially system files.  The first altenative is less desirable since it relies on the assumption that you are not in a state that allows changing the file.
Valid point. Since I am helping most people configure their (wireless) networks I am so much used to "sudo gedit". :-) But point taken...

The results is the same, however.

---

### Post by bsussman on 2006-10-30
> **wieman01 said:**
> Valid point. Since I am helping most people configure their (wireless) networks I am so much used to "sudo gedit". :-) But point taken...


...been a sysadm type waaay too long ...  :mrgreen:

My personal story of leap before look is not pretty 8)

---

### Post by Mr_Bond_UK on 2006-10-30
I found 

sudo pppoeconf

The only way i could set up my systems internet

---

### Post by vtechstu on 2006-10-31
I found some scripts that I can use for this that gives some good info about the system.  

Now that I can find out whether the system is static or DHCP, what's the command to set a network device to a certain IP? 

Thanks

---

