---
title: "WiFi Security"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by killaray on 2006-11-19
how do i secure my WiFi? so when others try to connect to it it asks them for a password?

---

### Post by DSn0wMan on 2006-11-19
You need to enable WPA on your access point.

---

### Post by Atomic Dog on 2006-11-19
Well WPA doesn't work so easily on Ubuntu.  You can also use WEP -not as secure, but will keep out 99.9% of people.

I use WEP, we also use WEP for our wireless client network at my work.

---

### Post by msak007 on 2006-11-19
> **Atomic Dog said:**
> Well WPA doesn't work so easily on Ubuntu.  You can also use WEP -not as secure, but will keep out 99.9% of people.

I use WEP, we also use WEP for our wireless client network at my work.
What's wrong with WPA in Ubuntu? I've never had any problems with it in Kubuntu. Quite the contrary, my bro had to revert our router to WEP because his and my sister's computers running (at the time) Windows XP couldn't connect, but my system running Kubuntu (using KNetworkManager) had no problems connecting :).

---

### Post by DSn0wMan on 2006-11-19
I agree with msak007. WPA works perfectly on Ubuntu, while the XP machine downstairs has difficulties from time to time.

Here is a decent tutorial for WPA on Ubuntu. [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

---

### Post by msak007 on 2006-11-19
I know this is a serious subject, but I read in Popular Science about an [alternative method]("http://www.ex-parrot.com/peter/upside-down-ternet.html") of getting people to stop using your Internet connection. It's not quite the same as securing it, but seems more fun...:D.

---

### Post by towsonu2003 on 2006-11-19
> **Atomic Dog said:**
> 
I use WEP, we also use WEP for our wireless client network at my work.

Sometimes ou won't have a choice (the device your isp gives you, for instance, may not support wap). 

If you do use wep instead of wpa (just like I do), don't input data you don't want to be stolen (just like I do). Also don't go to sites that you don't want any probability for others to login as you. see [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Flaws) and [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Remedies](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy#Remedies)

What I do: 
use ethernet for stuff I don't want others to see -incl'ding user+password (such as check personal email)
use wireless when I don't care whether others will see -incl'ding user+password (such as post at ubuntuforums)

---

### Post by David Corrales on 2006-11-19
Use network-manager to connect to WPA networks. It's out-of-the-box magic.

---

### Post by Daremo on 2006-11-19
For added security:
rename the SSID on the access point and then turn off SSId broadcasting. This way your access point will not "announce" its presence to the world. This is not hard security but just one extra piece of the puzzle.

---

### Post by Brynster on 2006-11-19
I use 3 things
1 NO broadcast of (e)ssid, nothing can see it they aint gonna log onto it
2 WEP need the key. No key no entry
3 MAC filtering, If the device aint listed it cannot connect

Never ever had somebody log in without my knowing about it.

---

### Post by PartisanEntity on 2006-11-19
I am using wpa on Dapper, also

MAC address filtering
IP range is limited to the number of pc's in the network
Each IP is reserved for a specific MAC address
Turn off SSID

---

