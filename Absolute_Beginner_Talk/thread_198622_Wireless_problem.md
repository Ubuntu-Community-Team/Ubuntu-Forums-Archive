---
title: "Wireless problem"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by czambran on 2006-06-17
At home I use a wireless connection which has been working without a problem, but yesterday I took my laptop to B&N, an I used the wireless connection there. When I brought my computer home, and try to once again use my wireless connection(I have a wireless router) at home, it seemed like it got an ip just fine but still I dont have internet connection. When I run dmesg I found a message saying:

No IPv6 router found.

Why is it giving me that error? Is that the reason why I might be getting an ip but yet not being able to use the internet? My wife's computer has windows and she has no problems getting a wireless connection.

Thanks

---

### Post by czambran on 2006-06-17
*bump*

---

### Post by tronica on 2006-06-17
i'm no expert on this, but it seems to be looking for a IPv6 router and yours at home it IPv4. so you need to find a way to change it back. just a thought.

---

### Post by czambran on 2006-06-17
That much I know, but the question is how?

---

### Post by czambran on 2006-06-17
sorry for bumping it but I really need to get back online.

---

### Post by brentoboy on 2006-06-17
all I can say is that you should try opening the network settings area and disabling wireless, then edit the preferences,  change them drasitcally (give yourself a fake static ip address or something)

save it, and then activate the interface again.

it might take 30 seconds to timeout and give up.
then, deactivate it again, and set things back to sane settings.
reactivage it (cross your fingers)

if that doesnt work, you can force change settings for network interfaces using ifconfig.  I havent done it in long enough that I dont dare give advice.  but, open a terminal, and call up the documentation for ifconfig with:
```
 man ifconfig 
```
or, if you want a prettier gui version of the same thing, click alt+f2 and in the "run" dialog type:
```
 man:ifconfig 
```

good luck with that.

---

