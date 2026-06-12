---
title: "Accessing wireless through a proxy"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-12-06
Hey folks,
I can't access wireless in college through Ubunutu. The proxy address is 10.1.1.7 which I've configured both swiftfox and my computer to access but it won't do it. I figure this is something simple. My WiFi manager (wireless assistant 0.5.5) has never worked and this is no exeption, is there some configuration neccassary for this application? and troubleshooting/suggestions greatly appreciated,
Thanks
Peter

---

### Post by sonny on 2006-12-06
My university's wireless has a proxy server too... as I understand the connexion to the wireless network shouldn't be a problem because is just an other network, if you can connect to the wireless you're 2/3 of the way... in Firefox 2.0 you have to make it go thorugh the proxy, just go to Edit>Preferences then go to the Advance Settings tab and then to the Network tab, click on the option button, then check the manual proxy configuration option, specify the proxy address (in your case 10.1.1.7) and in the port column put 80 and check the use the same proxy for all protocols option. That should do it.

---

