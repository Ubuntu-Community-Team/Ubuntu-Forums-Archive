---
title: "Apache and php"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by teknomek on 2008-02-01
I need help. I am new to ubuntu and linux but I have setup a Lamp server. I am running Joomla for my content. When i look at the site with a inter ip i can see the sit 192.168.1.100. But when I have a friend look at the site he only sees text with no php [www.teknomekinc.com](www.teknomekinc.com). is there a file i need to Edit to get my site live??? Help:confused::confused::confused:

---

### Post by emarkd on 2008-02-01
Are you behind a router's firewall?  It kinda looks that way from here.  If you are, you'll have to enable port-forwarding from your router.

---

### Post by teknomek on 2008-02-01
I have a linksys router and I have http port forwarding as well as port 22 and ftp. and the server is in the DMZ

---

### Post by emarkd on 2008-02-01
How about Ubuntu's firewall?  Honestly, if you can access the server from other machines on the network, this probably isn't it, but it's worth a shot, I guess.

By default, iptables has all the ports closed and I don't know if the LAMP packages change that or not.  If you don't want to edit iptables by hand, try installating Firestarter in Synaptic.

---

### Post by lespaul_rentals on 2008-02-01
```
sudo apt-get install php5
```

Run that and tell me what it says.

---

### Post by teknomek on 2008-02-01
states 
0 upgraded 
0 newly installed
0 to remove and 9 not upgraded

---

### Post by jaytek13 on 2008-02-01
This may be a silly question, but do you have the php mod enabled for the site?

---

### Post by PinkFloyd102489 on 2008-02-01
Apache automatically listens on port 80, meaning it opens that port in the firewall.

---

### Post by teknomek on 2008-02-01
I can see the site local if i got to 192.168.1.100 just fine .. its just outside the local network that it wont display php

---

### Post by PinkFloyd102489 on 2008-02-01
Sounds like you dont have the PHP mod for Apache installed.


```

sudo apt-get install libapache2-mod-php5

```

---

### Post by teknomek on 2008-02-01
stats am uptoo date with php mod

---

### Post by PinkFloyd102489 on 2008-02-01
Have you restarted Apache lately?

```

sudo /etc/init.d/apache2 restart

```

---

### Post by teknomek on 2008-02-01
yup  and site just shows text

---

### Post by PinkFloyd102489 on 2008-02-01
Im seeing the internal IP address of the computer, that's not supposed to happen. Major security issue you have here. :-P


I may have figured it out. Check your CSS.


EDIT: You need to remove your internal IP from everything in /var/www, so that it directs properly. Replace it with your hostname.

---

### Post by jaytek13 on 2008-02-01
Yeah... you have you're internal IP address listed as the directory for every href in your source. For instance, where you should have [http://www.teknomekinc.com/index.php](http://www.teknomekinc.com/index.php) you instead have [http://192.168.1.101/index.php](http://192.168.1.101/index.php).

I tested this out by replacing the internal IP with [http://www.teknomekinc.com/](http://www.teknomekinc.com/) in your document and then everything showed up fine.

---

### Post by PinkFloyd102489 on 2008-02-01
Looks like you have the IP thing corrected, but now you have PHP errors.

---

### Post by scxtt on 2008-02-01
> **PinkFloyd102489 said:**
> Apache automatically listens on port 80, meaning it opens that port in the firewall.the 2nd half of this statement is incorrect.

---

### Post by PinkFloyd102489 on 2008-02-01
> **scxtt said:**
> the 2nd half of this statement is incorrect.


After checking, you're correct. :-P

Sorry 'bout that.

---

