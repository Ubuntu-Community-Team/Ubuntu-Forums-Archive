---
title: "Non-working Wireless"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-06-18
Hello All:

I have a dekstop I am trying to get connected to my wireless router.  I have read numerous posts and tried some basic things.  

Using various terminal commands such as "lshw" and "iwlist" I have found that the driver is listed and working.  However when I try to ping the router address I get no response. 

I have tried router security set to WPA and disabled/open.  Nothing. Any ideas?

---

### Post by demonicdude on 2006-06-18
Well, i was having problems with my wireless router also. Your connecting from a wireless card right? What type of wireless card is it?

[http://ubuntuforums.org/showthread.php?t=198521](http://ubuntuforums.org/showthread.php?t=198521)

That was the thread i created asking people for help. Theres that one detailed post by DarkOx (thank you). I followed his instructions and i got my wireless card to work. You need ndiswrapper for that which you can install by using synaptic. Go to system/admistration/synaptic. Make sure though that you have the installation cd for ubuntu or w/e in the computeR!. Because they didn't include that in the installation, so you have to get it from the cd. That might have sounded confusing.. Lemme Rephrase a bit:

1. Put the Cd in drive
2. it should ask you to use it with synaptic just click ok.
3. Search for ndiswrapper -u(something). it'll be the only one probably..
4. Install that. and then follow the instructions posted by DarkOx in my thread.

Hope this helps :)

---

### Post by landsg on 2006-06-18
Thanks, I was able to get ndiswrapper going and install my linsys XP drivers.   When I do a "iwlist scan" I can see the router, signal strength, the whole nine yards.  When I go into my browswer, still can't connect to the internet, and I also can't successfully ping the router.

---

