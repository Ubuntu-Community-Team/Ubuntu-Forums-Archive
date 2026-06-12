---
title: "setting swappiness in sysctl.conf doesn't seem to change anything"
date: 2014-03-18
forum: Any Other OS
---

### Post by donarntz on 2014-03-18
HI,

I'm setting the swappiness in debian jessie to vm.swappiness = 1 but its still 60 on reboot. I've never had this problem before and I've set the swappiness many many times (including my wife's ubuntu laptop just the other day).  Anyone know what is going on?

Don

---

### Post by Bashing-om on 2014-03-20
donarntz; Hi !

How did you effect the change in swappiness ?
Did you edit "/etc/sysctl.conf" ? For the desired change in value to be persistent.
See:
[http://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)


[INDENT]just my little bit
[INDENT][INDENT][INDENT]to help
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by donarntz on 2014-03-21
I got it here:

[http://forums.debian.net/viewtopic.php?f=5&t=112669&sid=0b18aad5407b58b4c0c5869a0bd3b364&p=534439#p534439](http://forums.debian.net/viewtopic.php?f=5&t=112669&sid=0b18aad5407b58b4c0c5869a0bd3b364&p=534439#p534439)

They've changed it in Debian.  They weren't very clear about it though.

> **Bashing-om said:**
> donarntz; Hi !

How did you effect the change in swappiness ?
Did you edit "/etc/sysctl.conf" ? For the desired change in value to be persistent.
See:
[http://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

[INDENT]just my little bit[INDENT][INDENT][INDENT]to help
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


---

### Post by Bashing-om on 2014-03-21
donarntz; Hey ,

Glad you found the solution, and as well provided to the community what it took for the Debian distro.
You did good work.

Please mark this thread solved as an aid to others seeking a similar solution, and to help keep the forum tidy. 1st post -> thread tools -

All is well
[INDENT][INDENT]that ends well[/INDENT][/INDENT]

---

