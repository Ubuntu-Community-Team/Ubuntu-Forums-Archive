---
title: "port forwarding?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by FunkyMunky on 2006-10-09
hi. i'm new to ubuntu and till now i've found almost everything i needed on internet, but i really cant figure out what to do now. what i want to do is forward my amule ports so that it will work normally. i'm using linksys wrt54g router. on windows i did that by opening mozilla firefox and typing 192.168.1.1. into it. well i tried the same here on ubuntu and it says that server can't be found, just like i was trying to acces a website that is unavailable. besides that, even if i reached the router setup page i wouldnt know what port to forward to. so basicly i need a tutorial/explanation/anything that could help someone who barely knows anything about routers set it up correctly and forward the needed ports.

cu and please answer :confused:

---

### Post by wieman01 on 2006-10-09
Please open a terminal windows and type:
> route
This will reveal your gateway's IP address (= router). Then use the browser to access the router's web-interface in the used manner. I have got a WRT54G as well and there is no difference from what you are used to in Windows. The router remains unaffected by Ubuntu, the web-interface looks just the same. :-)

As for port forwarding, I can help you immediately if you tell me what ports "amule" requires. Don't know the program. You can enable "port forwarding" under "Applications & Gaming" (router) but you may need a static IP for it. But that's the next step.

---

### Post by Aberrix on 2006-10-09
> **FunkyMunky said:**
> i'm using linksys wrt54g router. on windows i did that by opening mozilla firefox and typing 192.168.1.1. into it. well i tried the same here on ubuntu and it says that server can't be found, just like i was trying to acces a website that is unavailable.

try; 192.168.0.1

login:
password: password

(that's the default as far as I know)


"Applications & Gaming", in there you should be able to setup the port and op you want it to forward to.

---

### Post by jorn on 2006-10-09
I've got a wrt54 too and I access it by typing 192.168.1.1 in to the browser's address bar.
Always turn on in the following order:
Modem
Router
Pc
If you cannot access your router restart it.
I don't know what port amule is running on but there is a guide here:
[http://www.portforward.com/](http://www.portforward.com/)

---

### Post by TheWizzard on 2006-10-09
> on windows i did that by opening mozilla firefox and typing 192.168.1.1. into it.
this should work in ubuntu too. i cannot imagine you can acces the internet, but not your router (i have the same model). what is your output of route? and ifconfig? 
it can also have something to do with your firefox settings. try another browser. 

> besides that, even if i reached the router setup page i wouldnt know what port to forward to.

works the same as emule in windows. ports are: 4662 (TCP) en 4672 (UDP). 
you also need to configure your local firewall to open these ports. do a search for firestarter. 

the amule howto: 
[http://www.amule.org/wiki/index.php/Getting_Started](http://www.amule.org/wiki/index.php/Getting_Started)

---

### Post by FunkyMunky on 2006-10-10
alright thx i finally did it. the router setup page didnt open cuz there was a dot at the end of the address where it shouldnt be.

---

