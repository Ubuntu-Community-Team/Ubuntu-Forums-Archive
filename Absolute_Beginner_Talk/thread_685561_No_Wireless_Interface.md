---
title: "No Wireless Interface"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by maineman2 on 2008-02-02
Hello I go to the local library and get on their wireless internet but this morning I was playing around with a couple of live cds and try to connect with those and now my wirelss doesnt work any more I get the message no interface found for pro wireless 3945 ABG I went to the resticted device manager it says pro wireless is enabled and in use Thanks Dan

---

### Post by rrwo on 2008-02-02
The obvious question is "what changed?".

If you are unsure, you can use something like
```
find /etc -ctime 0 -print
```
to print configuration files changed in the last 24 hours, for instance. (Increment "0" to "1" to look for files changed 24-48 hours ago, etc.)

---

### Post by maineman2 on 2008-02-02
I  tried the find / etc  and I did not see any thing about wireless.
I cannot find eth1 only eth0 How can i get it to find eth1

---

### Post by jan quark on 2008-02-02
pls post the result of the following terminal commands

```
iwconfig
```

```
sudo iwlist scan
```

---

### Post by maineman2 on 2008-02-02
Iwconfig
                       lo  no wireless extensions 
                       eth0 no wireless extensions


 sudo iwlist scan

                              lo interface does not support scanning
                              eth0 also does not support scanning

---

### Post by jan quark on 2008-02-02
it seems as if your drivers are not enabled although you say the restricted manager sets them as active...

what does
```

grep "3945" /var/log/dmesg 
```

say

---

### Post by maineman2 on 2008-02-04
Hi im back I ran out of time on the local library computer saturday. 

I tried the grep entry It now says no such file or directory.
I tried to get the wireless to work with the live open suse disk  and this is the message I got  unable to configure network card because kernel device is not present .Im at the library again  i tried to re boot the kernel pci=noacpi and just ended up at a prompt Thanks Dan

---

### Post by maineman2 on 2008-02-04
Bump Bump

---

