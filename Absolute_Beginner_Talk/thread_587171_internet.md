---
title: "internet"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by rolo41 on 2007-10-22
can somebody talk me why when i use the internet with ubuntu is very slow and in windows,same machine is fast.thank you.



                                                                  p.s. im using broadband

---

### Post by Daveth on 2007-10-22
Hi.
Welcome to the Ubuntu Forum. I think we need a bit more information from you. Are you using a wired or wireless connection, and are you using Gutsy Gibbon? Did the install go OK?

---

### Post by rolo41 on 2007-10-22
thanks for you help is awired connection and the installation when fine.

---

### Post by nchase on 2007-10-22
DNS settings maybe?

can you check your ping times to a site like google.com in ubuntu and in windows?

in each case open a terminal/command prompt and type
```
ping google.com
```

---

### Post by rolo41 on 2007-10-22
yes i can

---

### Post by rolo41 on 2007-10-22
i tried and looks fine

---

### Post by nchase on 2007-10-22
so these ping times are approximately the same for both windows and linux?

---

### Post by rolo41 on 2007-10-22
i dont know in windows but seems in linux to surf from one page to the oher takes about 40 seconds in windows about 10

---

### Post by nchase on 2007-10-22
if you wouldn't mind figuring out whether or not your ping times are significantly lower in windows compared to linux, it would really help me to figure out what is going on. 

i think it is related to your dns server settings -- can you check to make sure these are the same in linux as they are in windows?

to see the dns servers you have set up in linux, go to main menu > system > administration > network tab and look under 'dns servers'

---

### Post by frank002 on 2007-10-22
I had the same problem and after I disabled IPv6, it resolved the issue. Here is how to do it:
    To fully disable Ipv6:
       gksudo gedit /etc/modprobe.d/aliases
      Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
 By the way, This all started after I upgraded to Gutsy from Feisty. Let me know if this helps. Thanks.

---

### Post by OffAxis on 2007-10-23
There's also a spot in firefox to disable IPv6 (if you only care about it in that application).
Open firefox and go to 
```
about:config
```

and look for **network.dns.disable.IPv6**
change the value from false to true

---

