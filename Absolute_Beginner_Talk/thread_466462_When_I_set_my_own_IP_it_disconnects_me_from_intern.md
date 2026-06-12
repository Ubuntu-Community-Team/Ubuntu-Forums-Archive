---
title: "When I set my own IP it disconnects me from internet"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-06
I'm lost . I know i'v got it configured right . I'v done this a hundred times with windows with out a hitch can. Someone give me some advice please?

---

### Post by nonewmsgs on 2007-06-06
do you have a static ip?  wireless or ethernet?  how are you changing your ip?  is this for a server?

---

### Post by swoll1980 on 2007-06-06
i Had a windows cpu and a ubuntu cpu networked together. I liked the ubuntu so much i put it on both. the problem im having is both ubuntu cpus want to use the same address, 192.168.1.64 when I try to change this to a static ip 192.168.1.63 it will not let me get on the internet

---

### Post by swoll1980 on 2007-06-06
I,m going to network changing to static ip and putting in the config manually

---

### Post by DBStevens on 2007-06-06
192.168.0.0 - 192.168.255.255  are private ip addresses and can't be used for a direct internet address.

That address range is normally used on the lan side of a router.

Could you describe your hardware setup from the outside to each computer.

---

### Post by swoll1980 on 2007-06-06
dsl modem (192.168.0.1 ) then 100 mbps router then a erthernet cable to both cpu

---

### Post by DBStevens on 2007-06-06
How is the router configured?

Brand and model might also be of help.

---

### Post by swoll1980 on 2007-06-06
it's a network everywhere linksys 2.0 I don't know how it's configured or how to configure it I never had to mess with it before

---

### Post by meng on 2007-06-06
Most likely the router is assigning IPs to each computer it is connected to. These should be different IPs, it shouldn't be able to give both computers the same IP. You can't assign an IP to your computer and expect the router to continue to accept that connection.

---

### Post by swoll1980 on 2007-06-06
ip 192.168.1.63
gateway 192.168.0.1 ( modems ip address)
dns 68.94.159.1
alternet dns 68.94.157.1 (these were given to me by sbc < my service provider > )
i can't find a place to enter a broadcast but if i could it would be 192.168.255.255

---

### Post by swoll1980 on 2007-06-06
I'm sorry it's a hub not a router

---

### Post by swoll1980 on 2007-06-06
Does my hub have its own ip address?

---

### Post by DBStevens on 2007-06-06
That hub isn't going to help you at all with the ip address situation now how about the configuring capabilities of the the dsl modem can it act as a dhcp server which would be one requirement.

---

### Post by swoll1980 on 2007-06-06
My cumputers are the one asighning there own ips and they both want to use 192.168.1.64
stupid cpus don't care that theres allready a cpu using that address. they only work when i set them on romeing if i use any other option they disconnect

---

### Post by swoll1980 on 2007-06-06
i dont know ill find out give me a few minutes

---

### Post by DBStevens on 2007-06-06
Does your DSL modem allow any configuration?

I'll catch you later, I have some work to get done. so I'm out of here for a bit.

---

