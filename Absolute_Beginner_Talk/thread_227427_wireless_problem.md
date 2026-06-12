---
title: "wireless problem"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-08-01
I have a Intel PRO/Wireless 3945ABG Net (built-in) wireless card on a Dell Inspiron E1405. How do I configure it?

I have two operating systems on the machine. I can connect to the internet when I boot into the WindowsXP partition but not when I boot into Ubuntu Dapper.

Any ideas?

---

### Post by Ares Drake on 2006-08-01
There are various HowTos concerning Intel PRO/Wireless 3945ABG cards in this forum. Have you tried any of these?

---

### Post by aam-aadmi on 2006-08-01
I tried reading through some but got confuesd because of steps that requires one to download something from the internet. I cannot connect to the internet; so how can I download anything? Do I download the stuff from my Windows partition, burn in on a CD and then use it in Ubuntu?

Could you point out to some useful thread or website? Thanks.

---

### Post by MarkSheely on 2006-08-02
This wireless card doesn't need any additional configuration in the E1405.

Don't worry about downloading drivers, etc., from the internet.  

Do you know the steps you need to take to connect to the internet, given that your card was almost certainly configured correctly on installation?

---

### Post by wildseven on 2006-08-02
download this. worked for me. oh yeh, make sure your network connection is set to your wireless, its eth0 for me.

```
sudo aptitude install wifi-radar
```

try it, hope it works.

---

