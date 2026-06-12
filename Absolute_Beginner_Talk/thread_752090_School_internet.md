---
title: "School internet"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Cato Censorius on 2008-04-11
Hi.
I'm trying to access the internet at my school from Ubuntu 7.10. My school has three networks. One for emplyees, one for students with a school computer and one for guests. I'm using the guest network and, and to access the internet I have to type in user name and password (which we get for some days at a time). These passwords are typed in on a page on the school network. My problem is that when I try to access the internet from ubuntu firefox doesn't find that page. It is supposed to pop up automatically, and does so in Windows. No one at my school knows anything about Ubuntu, so they can't help me.
Are any of you familiar with this kind of problem.

---

### Post by hyper_ch on 2008-04-11
are you trying to get yourself connectec through wifi or lan?

---

### Post by crjackson on 2008-04-11
> **Cato Censorius said:**
> Hi.
I'm trying to access the internet at my school from Ubuntu 7.10. My school has three networks. One for emplyees, one for students with a school computer and one for guests. I'm using the guest network and, and to access the internet I have to type in user name and password (which we get for some days at a time). These passwords are typed in on a page on the school network. My problem is that when I try to access the internet from ubuntu firefox doesn't find that page. It is supposed to pop up automatically, and does so in Windows. No one at my school knows anything about Ubuntu, so they can't help me.
Are any of you familiar with this kind of problem.

Configure the popup blocker to allow the schools login popup.

---

### Post by Maxwell7 on 2008-04-11
And make sure that you allow Javascript in your firefox. (in case you use the NoScript extension like I do)

---

### Post by sillyxone on 2008-04-11
sound like your school is using a portal for authentication, any web request will be redirected to the portal, so for example, if you go to google.com, it will display the the authentication page instead.

if that's the case, then the first step is to make sure that you have connection to the school network. You can use ifconfig to check if you have an ip address, and if it's wireless, make sure you are connecting to the right network. If you have a Windows machine on the same wireless, compare your IP with its IP to see if you are having the right one. Also, you can use the Windows machine to see what is the default gateway (using ipconfig) for that network, then on the Ubuntu machine try to see if you ping it.

please specify in more detail such as what is the message Firefox is giving you, for example, if Firefox says "Server not found" right away then it seems like connection issue.

---

### Post by aeiah on 2008-04-11
see what happens when you type:
```
traceroute google.com
```
in the terminal. it probably wont get to google, but the first one it hits will probably be the site you have to give your login details to (if it finds one at all)

---

### Post by Cato Censorius on 2008-04-22
Hi.Sorry it took me so long to answere, but I've been sick and thus could not go to school to check your suggestions. Now I have:
1. It is a wireless nettwork (which I believe is Wifi, not LAN - but I know next to nothing about such things)
2. It wasn't really a popup. I'm supposed to be redirected to a page. (My english has faults, especially when conerning computer-related terms)
3. How do I check the java script?
4. The IP-adresses, gateway and one other thing which name I don't know in english (I'll check it as soon as possible) are different. 

The message firefox sends me is "Server not found..." but I believe I am connected to the network.

5. When i type traceroute google.com in the Terinal, I'm told that I'm supposed to install something (traceroute and traceroute...). But if I try to install this thing, it fails, because it needs an internet connection.

---

### Post by Cato Censorius on 2008-04-22
The third thing, was either Bcast or mask. My problem is that my windows is in Norwegian and my Ubuntu is in english, so I have translation-problems. Any way what I'm talking about is the second of the three things that are listed when you type ipconfig (Windows) or ifconfig (Ubuntu)

---

