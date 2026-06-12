---
title: "Wireless Connection Not Showing In the Network Settings"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by agirlnameddanni on 2007-01-05
okay, well. I am using Ubuntu 6.06, Drapper Drake. 
And after in the terminal doing updates, I rebooted my computer, and I noticed that my internet wasn't working anymore. 
I went to the Network settings, and discovered that of the three types of connections, one (wireless connection), the one i was using was completley gone! and I can't find the interface ath0 anymore either... in the terminal, i used the commands

```
sudo iwconfig ath0 essid "network name"; sudo iwconfig ath0 key "WEP"; sudo dhclient ath0
```

after doing that, it told me that there was no such divice. I was on another forum, and some of the people there said that my updates messed one of my packages up. They told me to reinstall the package entitled **linux-restriced-modules-general**. first of all, i dont have that specific package, so i tried the next best one, (linux-restriced-modules-common), but that didn't download because it said there was a failure to connect to the required page, and i am guessing that is because i have no internet. 

I am using a Dlink card...the chipset is Atheros. 
Please help me in any way possible! Thanks so much!

---

### Post by mahy on 2007-01-06
What they told you about linux-restricted-modules is correct. What kind of updates did you perform? If it was a kernel update, chances are your old kernel is still there. Select the old one in GRUB, run 'sudo depmod -a' when it boots, reboot again (with the same kernel) and it should work again. Then fix the updates as necessary. Good luck!

---

### Post by iver2435 on 2007-01-06
When you are typing ath0.......do you mean eth0?

I know you said the chipset was Atheros, so it could very well be ath0, just trying to make sure all bases are covered...

try eth0 and see what happens...

---

### Post by mahy on 2007-01-06
> **iver2435 said:**
> When you are typing ath0.......do you mean eth0?

I know you said the chipset was Atheros, so it could very well be ath0, just trying to make sure all bases are covered...

try eth0 and see what happens...

AFAIK, eth0 as a wifi only applies to Intel chips. The guy's right.

---

### Post by agirlnameddanni on 2007-01-08
thanks so much, i got it working! 

after a few days. hahha. 
but thank you!

---

