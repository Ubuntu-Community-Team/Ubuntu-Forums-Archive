---
title: "Broadcom"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by thejem on 2008-04-01
HP Pavillion laptop dv6700 w/Broadcom 4315 wireless built in.
Have tried all threads in the forums that refer to Broadcom.
Cannot get the light to come on blue it remains red all the time unless I boot into Vista.
It is like Ubuntu does not even recognize it. Tried Gutsy before Hardy and it would not work either and sound didn't work there.

---

### Post by Dr Small on 2008-04-01
Broadcom cards a a piece of junk. I went out and bought a Dlink card which works perfectly instead.

---

### Post by thejem on 2008-04-03
Yea but when you have a laptop with built in and no card slots you don't have a choice

---

### Post by ghost_ryder35 on 2008-04-03
> **thejem said:**
> Yea but when you have a laptop with built in and no card slots you don't have a choice

USB

did you try
```

sudo apt-get install bcm43xx-fwcutter
sudo modprobe

```

I think there is a difference in the new 4311's

---

### Post by joshrobinson on 2008-04-03
> **Dr Small said:**
> Broadcom cards a a piece of junk. I went out and bought a Dlink card which works perfectly instead.

broadcom cards work great, you just have to know how to work them
i can get mine up and running in under 5 minutes with ndiswrapper

---

### Post by NullHead on 2008-04-03
> **joshrobinson said:**
> broadcom cards work great, you just have to know how to work them
i can get mine up and running in under 5 minutes with ndiswrapper

I second that comment. Broadcom work great in hard too. I run a 4318 and a 4306 and they both work flawlessly.

---

### Post by thejem on 2008-04-05
Thanks guys. Everthing I have tried still leavs me with "no wireless found"

---

### Post by joshrobinson on 2008-04-05
```
sudo apt-get install ndisgtk
```

```
wget http://biginoz.free.fr/linux/bcmwl5a.inf
```
```
wget http://biginoz.free.fr/linux/bcmwl5.sys
```
```
ndiswrapper -i bcmwl5a.inf
```
post the output of the command above

```
ndiswrapper -l
```
and post what this outputs

well since you didnt reply and signed off, heres what you WOULD do next, if the drivers are correct

```
sudo rmmod bcm43xx
```
```
sudo modprobe ndiswrapper
```

---

### Post by thejem on 2008-04-10
I reformated hard drive and am going to try again tomorrow. I tried so many things I am not sure if I got them all uninstalled or not. That could have been messing things up. Thanks for the replies. Will try when I get hardy reinstalled.

---

### Post by stchman on 2008-04-10
> **thejem said:**
> HP Pavillion laptop dv6700 w/Broadcom 4315 wireless built in.
Have tried all threads in the forums that refer to Broadcom.
Cannot get the light to come on blue it remains red all the time unless I boot into Vista.
It is like Ubuntu does not even recognize it. Tried Gutsy before Hardy and it would not work either and sound didn't work there.

Refer to this:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Broadcom_wireless_driver)

---

