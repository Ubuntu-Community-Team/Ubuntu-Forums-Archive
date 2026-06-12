---
title: "Can't connect to the internet."
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by jonasd on 2006-08-20
Hi,

I have Windows XP home edition but I'm planning to migrate to Kunbunto or Ubuntu (already ordered my live cd)

I first tried Kubuntu using a live cd. I worked great!!! ... I could even connect to the internet.

I installed from that live cd and all went well. Within the hour I could log-on to my new system.

but ... I could no longer connect to the internet. I checked my setting and all seems ok. My netwerk interfaces are enabled and are configured to automatic.

Can any-one help me. 

Kinds Regards

Jonas

---

### Post by Qrk on 2006-08-20
```
sudo /etc/init.d/networking restart
```

Is a good thing to try. If it doesn't fix the problem, it will at least give information on how to troubleshoot it. You can paste the output here.

---

### Post by kebes on 2006-08-20
Does your internet require DHCP or a manual IP address? In a terminal, type the command "ifconfig" and see what it outputs (post the result here, too). This may give you some information about what is going on.

---

### Post by jonasd on 2006-08-20
thanks for your help .. i will remember your code

The solution was however simple. I have 2 ethernet thingies directly on my motherboard. I tried the 2e thingy and now it works.

Don't understand it .. because that's the port I have always been using.

I posted this reply via my working Kubuntu installation

(K)Ubuntu rules !!!!

---

