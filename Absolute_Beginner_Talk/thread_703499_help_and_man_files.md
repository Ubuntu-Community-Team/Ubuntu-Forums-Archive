---
title: "help and man files"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by matey3 on 2008-02-21
man...I dont understand what all these dumb brackets are for?
cant they just put an example and get it over with?
then I guess we could customize that example to fit our needs a lot better than dealing with these <blah> and that [blah] . I dont think those brackets are used in the commands any ways?

I was able to change my IP address and netmask  on one of xen virtual nics but I be doggone if I could change my virtual mac address!
I tried every which way like HWaddr hw addr HW addr etc etc then changed their places and after half an hour I still get errors mostly it thinks HW or the addr is the host name!?

why couldnt they make their help files readable for change and stop putting those dumb brackets in there???
do an ifconfig --help and see what i am talking about
 lol
[/<<[]]/>
oh and 
]

---

### Post by jan quark on 2008-02-21
use this code

```
man ifconfig

```
to display further information

---

### Post by PeterJS on 2008-02-21
The elements given in the man pages in brackets denote flags that are optional. Specfically to changing the MAC on a card, and the man page gives this:
```

hw class address
              Set the hardware address of this interface, if the device driver
              supports this operation.  The keyword must be  followed  by  the
              name of the hardware class and the printable ASCII equivalent of
              the hardware  address.   Hardware  classes  currently  supported
              include  ether  (Ethernet), ax25 (AMPR AX.25), ARCnet and netrom
              (AMPR NET/ROM).

```
So you're going to want along the lines of:
```

sudo ifconfig ethX hw ether someMAC

```

---

### Post by freelinuxhelp on 2008-02-21
the [ and ] usually indicate that you can use any one of the command switches between them.

try this
sudo ifconfig eth0 hw ether macaddressany

---

### Post by freelinuxhelp on 2008-03-08
did you ever get your mac address changed?
if so, please mark the thread as solved under Thread Tools

---

