---
title: "No Internet Connection on Startup...."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Artistar on 2007-06-08
since i've installed Feisty i have no internet connection on startup. a thought after setting-up my connection that it'll load with my system, but that's not happening. When i log to my system i can see my notification icon in tray that link is OK, but when i open Firefox i can't open any page.
My modem/router is Elcon 2253EU, and this morning i tried to solve this by putting Elcon in router mode. Then I set up static IP to 192.168.1.200, and also entered DNS servers that my provider gave me. But NO! The problem still persists.
Entering "sudo poff dsl-provider" and "sudo pon dsl-provider" in terminal does not help. All that helps is unplugging the wire form my ethernet card (Realtek  8139), then shutting it down, turning it on, and putting the wire back in it - after the router connects to my provider, everything is suddenly working..... Doing this all the time is very annoying so i need help to find another solution..... I just want Internet to be up and running when i boot up my system.

Thanx in advance. :)

---

### Post by Regel on 2007-06-08
Sometimes this helps:
```
sudo ifdown eth0 #replace eth0 with whatever you have 
```Now you dont have internet connection.
then:
```
sudo ifup eth0
```and wait for a few seconds before you check your connection with 'ifconfig' and/or 'ping google.com'.

---

### Post by Vaidya on 2007-06-08
I am having the same frustration myself.

I have a ADSL connection, with a router.

On startup, I have to always go to Network Connections, select desktop settings (it is always greyed out) to its default.

This has the effect of changing my DNS settings to what my provider has given me and when this happens, I get my internet connection working. I always have to do this every time....

I have gone up and down the various posts and am FINALLY writing in for help.

I have used pppeconf (I get a time out waiting for prad or something like that error)

I have tried setting network manager to use static ip..

---

### Post by Artistar on 2007-06-08
> **Regel said:**
> Sometimes this helps:
```
sudo ifdown eth0 #replace eth0 with whatever you have 
```

sorry, but i don't understand this one - replace eth0 with what exactly?
isn't there any permanent solution on this matter?
this plugging and unplugging the wire is getting more and more frustrating every time i do it.... ](*,)

am i doing anything wrong?

---

