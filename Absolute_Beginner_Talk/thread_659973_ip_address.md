---
title: "ip address"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by arvindenrique on 2008-01-06
how to check my ip address via command line?

---

### Post by stump138 on 2008-01-06
```
ifconfig
```

---

### Post by boban on 2008-01-06
```

ifconfig

```

---

### Post by arvindenrique on 2008-01-06
when i checked it using "whatismyip.com" it shows [COLOR="Red"]59.92.xx.xx[/COLOR].but the cmd ifconfig doesnt show that ip.why?is there any other cmd?

---

### Post by boban on 2008-01-06
You can have 2 different ip addresses: one public (that what [www.whatismyip.com](www.whatismyip.com) is howing you) and one in your private network (you see it via the ifconfig command).

---

### Post by thelatinist on 2008-01-06
> **arvindenrique said:**
> when i checked it using "whatismyip.com" it shows [COLOR="Red"]59.92.xx.xx[/COLOR].but the cmd ifconfig doesnt show that ip.why?is there any other cmd?

Perhaps you are behind a router or firewall?

---

### Post by arvindenrique on 2008-01-06
then  how 2 check private address using cmd line?

---

### Post by Dr Small on 2008-01-06
If you are behind a router, when running the command:
```
ifconfig
```

Will show your internal IP address.
By directly accessing Whatismyip.com, it will output your external IP, provided to you by your ISP.

Dr Small

---

### Post by boban on 2008-01-06
> **arvindenrique said:**
> then  how 2 check private address using cmd line?
By ifconfig command. It will list all your network cards with ip addresses.

---

### Post by Dr Small on 2008-01-06
To read your external IP address from the terminal, make a script to do it:
Make a script named ip.sh and put the following contents into it:

```
#!/bin/sh
wget -q http://whatismyip.org
IP=$(cat index.html)
rm index.html
echo ''
echo $IP
echo ''
exit 0
```

Then, in the terminal, run:
```
sh ip.sh
```

---

