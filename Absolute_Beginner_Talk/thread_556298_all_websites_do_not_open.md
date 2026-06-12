---
title: "all websites do not open"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by havencruise on 2007-09-21
Hi guys, i've recently downloaded the 7.04 version and have managed to setup an internet connection succesfully. Although i can load webpages like google, yahoo, orkut, imdb, i'm not able to open sites like ubuntuforums, youtube, metacafe, etc.(Please note: not able to open ubuntuforums,so am posting this from windows. :-( .. ).. Is this a common problem with anyone else out there? 
Please help for a solution!

---

### Post by Voland on 2007-09-21
Try ```
ping ubuntuforums.org
``` and watch result. Check DNS settings.

---

### Post by UbuntuniX on 2007-09-21
Are you sure your internet connection is setup properly?

---

### Post by mikewhatever on 2007-09-21
> **havencruise said:**
> Hi guys, i've recently downloaded the 7.04 version and have managed to setup an internet connection succesfully.

Was there any problem with it? How do you connect (modem, router, dial up)?

> Although i can load webpages like google, yahoo, orkut, imdb, i'm not able to open sites like ubuntuforums, youtube, metacafe, etc.(Please note: not able to open ubuntuforums,so am posting this from windows. :-( .. )..

What happens when you go to ubuntuforums.org? Does it crash, blank screen, what?

> Is this a common problem with anyone else out there? 

Why, do you want to start a club? Of cause it is not common.

---

### Post by hyper_ch on 2007-09-21
Are you sure you are loading webpages like google or are they just in your cache. What happens if you run a search on google? You get results?

---

### Post by havencruise on 2007-09-21
Here's the description on how i did it from start to answer a few questions.

Downloaded ubuntu from the official download link and then burnt it on a cd. Ran a cd check after burning it, and after finding no errors, proceeded to install it on my system. The installation reported that it was completed succesfully. Logged into my user after reboot and configured my internet connection using "pppoeconf" command. It requested me to enter my username and password and so i did. It said run the command "pon dsl-provider" to start the connection and "poff dsl-provider" to disconnect. I 'connected' and typed google's address into the address bar, n the webpage loaded well. Ran a few searches just to confirm that i was happily connected. Tried to open a few of my favourite websites like youtube, and ubuntuforums, but in vain.
It connects and the status bar reads "waiting for blah blah" indefinitely although i have a connection speed of 2mbps. And surprisingly, google takes hardly a second to load.
I have tried searching for various things and all the search pages load almost instantly.

---

### Post by havencruise on 2007-09-21
> **Voland said:**
> Try ```
ping ubuntuforums.org
``` and watch result. Check DNS settings.

i tried pinging.. it pinged succesfully(reply from blah blah) What DNS settings should i check??

---

### Post by Voland on 2007-09-21
It's very strange that you can ping sites,but can not reach them using browser...Are you using DHCP to get your IP adress?

---

### Post by havencruise on 2007-09-21
Yes i do use dhcp.

---

### Post by havencruise on 2007-09-21
Please have a look at a post from google groups forum posted by "vanmorg...@gmai.com" 
The link is :
```
http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/d422c9de5644d711/6a4d747f7bf812fd"]http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/d422c9de5644d711/6a4d747f7bf812fd
```

I'm not sure if its a problem of mozilla, as i have downloaded the latest version of mozilla on windows , and it works picture perfect.
Its not the exact same problem that i have, but it somewhere points out to a problem with ubuntu and webpages not loading although internet's connected.

---

### Post by havencruise on 2007-09-21
> **Voland said:**
>  Check DNS settings.

How do i change my dns server address?? .. It might give me a solution.

---

### Post by Voland on 2007-09-21
system>administration>network settings. I do not remember exactly name of tab, but I'm sure you'll find it ;)

---

### Post by havencruise on 2007-09-22
Nope. I tried tweaking with everythin i know about networking and its settings for a day now and nothing has worked. Somebody please strike a lightning.

---

### Post by Voland on 2007-09-22
Do you have USB ADSL modem? Or something different?

---

### Post by havencruise on 2007-09-22
> **Voland said:**
> Do you have USB ADSL modem? Or something different?

I have an ethernet card on board.. Its the one which had problems finding drivers 6 months back.. ;) .. I run an asus k8smx motherboard. My router is directly connected to the on board ethernet card.

---

### Post by hyper_ch on 2007-09-24
you could try openDNS:

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

---

### Post by prshah on 2008-02-25
> **havencruise said:**
> I have an ethernet card on board.. Its the one which had problems finding drivers 6 months back.. ;) .. I run an asus k8smx motherboard. My router is directly connected to the on board ethernet card.

Hi, same problem... did you find a solution?

Cheers,
PRShah

---

### Post by prshah on 2008-03-17
> **havencruise said:**
> I have an ethernet card on board.. Its the one which had problems finding drivers 6 months back.. ;) .. I run an asus k8smx motherboard. My router is directly connected to the on board ethernet card.

Finally, found the solution. My MTU on the router was set to 1500... to high, dropped it to 1492 and everything worked great! For more details, see [http://ubuntuforums.org/showthread.php?t=718709&highlight=prshah](http://ubuntuforums.org/showthread.php?t=718709&highlight=prshah)

---

