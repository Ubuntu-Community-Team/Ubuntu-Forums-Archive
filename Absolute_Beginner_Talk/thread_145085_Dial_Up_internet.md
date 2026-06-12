---
title: "Dial Up internet"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Paul Bennett on 2006-03-15
Hey. I just got my live cd in the mail, (becuase I have dail up :rolleyes: ) and Im tryuing to connect to the interent by dailing my ISP, but cant seem to figure it out. I understand I can use a program lik kPPP, but id dosent come installed, and I cant download it without getting on the internet! 

Can anyone give this complete noob a runthrough on how to dail up with my ubuntu breezy 5.10 live cd?

---

### Post by nixclusive on 2006-03-15
dial up access in quite easy if you have an external or a true hardware modem.
Check out pppconfig in the terminal:

Open the terminal and enter:
```
pppconfig
```

Follow the instructions and enter 
```
pon <provider>
```

where <provider> is the name you'll enter in 'pppconfig'

---

### Post by Paul Bennett on 2006-03-15
Thanks for the quick reply. Im going to boot and check it out!

---

### Post by Paul Bennett on 2006-03-15
Sorry for the double post. 

I am told that "you must be root to run this program"

What does this mean? I have not set a root password, as I am working off live CD atm.

---

### Post by FizDev on 2006-03-15
It simply means that you must put "sudo" before the command. For example :
```
sudo pon <provider>
```
When it will ask you for a password, just put your user password. For more info on the sudo command, go see : 
[https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo]("https://wiki.ubuntu.com/RootSudo?action=show&redirect=UsingSudo")

---

### Post by Paul Bennett on 2006-03-15
Thanks. Ok, I did that. I set up pppconfig correctly (as far as I can tell, and with 'qx' as my account) but when I do 

```
pon qx
```

nothing happens. I dont get error, like I do if I type a wrong account, it just goes to the next line and nothing happens. Any ideas?

Thanks so much for you help nixclusive and FizDev.

---

### Post by towsonu2003 on 2006-03-16
Check out the second link in my signature. 

If you have a hardware modem (works out of the box in Ubuntu usually), scroll down the page and check out wvdial. it gives output (whether you are connected or not, and if not, why). 

If you have a winmodem (not recognized out of the box), then don't scroll, start from the beginning of the page, look especially carefully at "scanModem". To see if you have a winmodem or not, if you did not install any drivers for the modem, go to System>Networking and check to see whether "Modem" is listed there. If not listed, that means ubuntu didn't see it, most probably bc you have a winmodem. it is damn hard to make it work, but some will work after some effort.

---

