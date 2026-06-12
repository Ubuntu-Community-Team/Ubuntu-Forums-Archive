---
title: "wireless on hp dv6000"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by PatrickMoore on 2008-03-08
Im installing ubuntu 7.10 on my hp dv 6109 laptop. i need to establish a wireless connection to get the apprpriate drivers to get everything to work.

 i have a broadcom 802.11 b/g

i'm also looking for other suggestions for installation. i'm new to linux and will be dual booting until i get the hang of it. any help would be much appreciated

---

### Post by st33med on 2008-03-08
Could you please do:
```
lspci
```

and:

```
iwconfig
```

in the terminal. Post the output here.

---

### Post by timbounceback on 2008-03-08
also:```
sudo lshw -C network
```

---

### Post by PatrickMoore on 2008-03-08
i'm going to try that now thanks guys

---

### Post by PatrickMoore on 2008-03-08
> **st33med said:**
> Could you please do:
```
lspci
```

and:

```
iwconfig
```

in the terminal. Post the output here.

lspci listed my graphics card i believe there was alot listed about my nvidia driver.

iwconfig listed the following
 
lo= no wireless ext
eth0= no wireless ext
eth1= IEEE802.11 B/G ESSSID:off/am
nickname broadcom 4311
mode managed access pnt invalid
rtsthr:off fragmentthr:off
link quality 0/100 signal level 256 dbm noise level 256dbm

 sudo lshw -c network did me no good

---

### Post by Marcolin on 2008-03-10
Hi, I just loaded up Ubuntu 7.1 on my HP dv6000 last week and spent several hours trying to get my wireless card working. (I should also mention that I am very new to linux...) I followed instructions from other posts about using ndiswrapper among other things. I finally realized that I never enabled the restricted driver for my wireless card (System -> Administration -> Restricted Drivers Manager). Once I did that, it worked great.

Sorry if Im stating the obvious. I just realized that it wasn't mentioned in this thread.

---

### Post by PatrickMoore on 2008-03-11
oh no you are awesome i'm going to try that as soon as i can.

---

### Post by PatrickMoore on 2008-03-15
still having issues with wireless. i tried to derestrict the driver. it stated was missing bcm 43xx fwcutter downloaded online still could not load the driver. any suggestions

---

### Post by Marcolin on 2008-03-16
I had to boot using the live CD last night and I went to use my wireless connection but got the same error you did. I tried activating the restricted driver and again, got the same error you did. 

It was then that I realized that I did download a firmware driver in my initial attempt to fix it before I did all that ndiswrapper stuff. I did a google search and found this site that explains downloading the driver and extracting it. I had to use a wired connection to do so; hopefully you can do the same. Here is the link:
[http://jaux.net/2007-11-10/linksys-wpc54gsbcm43xx-in-debian-40/#comments](http://jaux.net/2007-11-10/linksys-wpc54gsbcm43xx-in-debian-40/#comments)

It instructs you to download that file (its the same one I downloaded and used) and tells you how to install it.

Hope that works for you.

---

