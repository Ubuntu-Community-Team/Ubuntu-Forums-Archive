---
title: "[SOLVED] Configure ethernet using router as DNS server!"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by khurrum1990 on 2007-12-13
Ok, I will be as brief when I explain my problem. I am using a speed touch router to connect to dsl. I configured my ethernet connection using the command "sudo pppoeconf". Now the problem is that I can't visit my router webpage which is speedtouch.lan to make changes in the router configuration.

Some one here told me:
"If you have a router, what are you running ppp on the PC. This will tunnel thru the router and you will not use the router as your dns server. You will use the ISP dns which does not know speedytouch.lan.

Configure pppoe on the router and then use the router to share this ppp connection to all your PCs and devices."

Is he right? Then how can I configure pppoe on my router, I remember I never had a problem like this in Fiesty.

---

### Post by leonidas666 on 2007-12-13
Your Router consists of two parts: a normal router (i.e. a device where you can plug in multiple network devices, and then all the network devices can "see" each other), and a dsl modem. 
Normally, people setup the router so that the router takes care of making the connection to the internet, that is, if some device plugged into the router part wants to make a connection to the internet, then the router itself tells the modem to make the connection. This means that you have to tell the router about your username and password of the ISP (normally through the web-interface).
If you are using pppoe, then you are bypassing this, and your computer is talking directly to the modem part. obviously, internet also works this way, but there are certain disadvantages. It's much better to let the router handle the modem.
So you should do the following:
- don't run pppoe on your computer (start from a fresh reboot).
- make sure that your computer is getting a ip- adress from your router via dhcp(this should work by default in ubuntu, unless you have changed something).
- to check the ip-address, you can use ifconfig (from the terminal). One of the lines of the output should say soemthing like
inet Adresse:192.168.2.33
The number might be different in your case. Then you enter this number in your browser, but you replace the last number with 1, so in this case it would be 192.168.2.1
Then you should see the web-interface of your browser, Now you have to configure your router so that it will handle the internal modem. For this you'll have to read your router's documentation, maybe your isp has also given you a nice quickstart-paper or something, everything should be written there.

---

### Post by khurrum1990 on 2007-12-13
Thanks I will try this and let u know.

---

### Post by khurrum1990 on 2007-12-13
I fixed it, all I need to type in is sudo dhclient eth0. That gives me the correct address and Ubuntu starts talking with the router.

---

