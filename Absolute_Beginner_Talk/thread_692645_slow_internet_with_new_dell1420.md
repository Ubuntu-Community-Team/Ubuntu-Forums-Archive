---
title: "slow internet with new dell1420"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by PJVT on 2008-02-10
I just installed Ubuntu 7.10 on my new dell inspiron 1420 and my internet is very slow and sometimes just halts and no browsing is posible, I thought it might be the internet service but when i boot with wndows vista the internet works very good.  I really dont want to use windows but desperately need good internet.  also having trouble installing the latest java sdk and netbeans.

any help will be greately appreciated

---

### Post by spiderbatdad on 2008-02-10
you might try disabling ipv6 in your browser or in /etc/modprobe.d/aliases 
for netbeans IDK but i see softpedia has a download

---

### Post by moephan on 2008-02-10
Try turning off IPV 6 if you haven't already. Open firefox, and type "about:config" in the address bar. You'll get a whole big list of settings. Type "IPV" in the filter. Then set "disableIPV6" to true (you just click on the line and it will toggle it).

HTH

Cheers, Rick

---

### Post by PJVT on 2008-02-10
Thank you for your help will be trying your recomendations

---

### Post by jan quark on 2008-02-10
what is your wireless card?
please run 

```
lspci
```
```

sudo lshw -C network
```

and post the output
thank you

---

