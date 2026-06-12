---
title: "How to use wired instead of wireless connection?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by frafu on 2008-02-17
Hello, 

I am installing ubuntu on a computer with an ethernet card and a wifi card. 

I have configured a static ip for the wired connection to my router; but internet does not work: it seems that ubuntu tries to connect through the wireless connection, but my router does not have wifi. 

How can I make ubuntu use the wired connection? 

Thanks in advance for your help? 

Francesco

---

### Post by Crooksey on 2008-02-17
In the menu..

```

sysem >> admin >> network
```

Disable the wireless card, and enable the ethernet card.

---

### Post by jan quark on 2008-02-17
see pic 
just uncheck the wireless 
and check the wired connection then click on properties and configure it

---

### Post by frafu on 2008-02-21
Hello, 

First of all, thanks for the replies. 

By disabling "roaming" in the wireless card properties, the OK button gets greyed. To reenable it, simply enter data in the fields of the wireless card properties. 

After closing the properties dialog of the wireless card, disable it in the Network main window. 

Have a nice day. 

Francesco

---

### Post by frafu on 2008-02-21
Hello again, 

Now I wonder whether it is possible to have both cards (wired and wireless) simultaneously working? 

I am asking because I was not able to make Internet work through the wired connection attached to a  router until I disabled the wireless card. 

(The router was properly configured because other computers connected to it had Internet. Moreover, I suppose that the fact that dhcp-server being disabled is not a problem; the computers are confugured with static ips.) 

Thanks in advance. 

Francesco

---

