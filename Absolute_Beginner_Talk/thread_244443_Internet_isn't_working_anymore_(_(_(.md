---
title: "Internet isn't working anymore :( :( :("
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2006-08-26
Hello, all.

Presently, I live in a place that has four different ethernet connections available for connecting to the internet.  I recently moved my computer from one room to another, and thus plugged my computer to a different connection.  For some reason, I am now unable to access the internet in Ubuntu.  Is this perhaps because Ubunutu is somehow looking for the old IP address?  I know that the internet connection in the new room is fine, because I am presenly accessing the internet in Windows through the same connection.  

Thanks for any help, folks!

---

### Post by v1ct0r on 2006-08-26
I guess this is a DHCP issue...
Please give us more detalis [oh, and no real IP's please! :P]

---

### Post by limberlegs on 2006-08-26
Forgive me, as I am quite a noob when it comes to these things.  What other information would be useful?  How might I go about getting it?

Thanks for your response.

---

### Post by Kobalt on 2006-08-26
Hi,

please post us the result of this command line (to enter in a Terminal) : 
```
ifconfig
```

You could try this to get your connection back : 
```
sudo ifdown eth0
```
```
sudo ifup eth0
```

Cheerios !

---

