---
title: "browser issue"
date: 2012-04-12
forum: Any Other OS
---

### Post by winzip on 2012-04-12
I am on windows xp box.
I do a ssh to machineA. (using putty)
From machineA I do ssh to connect another machineB.
I start jboss server in machineB at port 8080.

When I try to access http :/ / machineB:8080/myapps in IE browser in windows xp it does not open.
How do I view the web page ?
Can I do tunneling in browser?
Do you have any solution. 
machineA , machineB is ubuntu 10.04 Os server edition.

---

### Post by dragonfly41 on 2012-04-12
Machine A and B are local?

You might need dynamic dns to access machine B via internet

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

[http://www.zoneedit.com/doc/dynamic.html#faq1](http://www.zoneedit.com/doc/dynamic.html#faq1)

---

### Post by winzip on 2012-04-12
> **dragonfly41 said:**
> Machine A and B are local?

You might need dynamic dns to access machine B via internet

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

[http://www.zoneedit.com/doc/dynamic.html#faq1](http://www.zoneedit.com/doc/dynamic.html#faq1)
Yes. They are local.
LAN has no internet.
Whats the solution?

---

### Post by winzip on 2012-04-12
Comments please.

---

### Post by coffeecat on 2012-04-12
> **winzip said:**
> Comments please.

Please be patient. Everyone here is a volunteer and will respond when they can. If you need to bump a thread to get attention, please do not do so more than once every 24 hours.

---

### Post by Linux_junkie on 2012-04-12
> **winzip said:**
> I am on windows xp box.
I do a ssh to machineA. (using putty)
From machineA I do ssh to connect another machineB.
I start jboss server in machineB at port 8080.

When I try to access http :/ / machineB:8080/myapps in IE browser in windows xp it does not open.
How do I view the web page ?
Can I do tunneling in browser?
Do you have any solution. 
machineA , machineB is ubuntu 10.04 Os server edition.

I don't think you need to type in the port number in to the address field like you have just the address of machineB followed by the path to the html pages you want to view.

The address you quoted above would seem to me that you want to run linux apps on your xp box. XP won't be able to run linux apps.

---

### Post by winzip on 2012-04-12
> **Linux_junkie said:**
> I don't think you need to type in the port number in to the address field like you have just the address of machineB followed by the path to the html pages you want to view.

The address you quoted above would seem to me that you want to run linux apps on your xp box. XP won't be able to run linux apps.

Linux box is the server host.You can access a web apllication from any browser of any machine in the LAN.
Do you have a solution ?

---

### Post by wojox on 2012-04-12
Does the jboss server know to listen on port 8080?

You say you can't connect with xp, does it work on other computers?

PuTTy into server A and run 

```
w3m -v http://192.168.0.0
```

Fix that to point to jboss.

---

### Post by winzip on 2012-04-15
> **wojox said:**
> Does the jboss server know to listen on port 8080?

You say you can't connect with xp, does it work on other computers?

PuTTy into server A and run 

```
w3m -v http://192.168.0.0
```

Fix that to point to jboss.

Never mind. I have found solution. Try using putty and ssh tunneling. You will be able to open url  in the browser.
Problem Solved.

---

