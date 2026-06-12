---
title: "wireless network connection problem?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by cw_yong on 2007-12-20
My system show that my wireless network connection is established at 72% but i am not able to surf the web at all using firefox. Can someone out there please HELP ME. THANK YOU VERY MUCH IN ADVANCE

---

### Post by solar george on 2007-12-20
Open a terminal and type,
```
tracert bbc.co.uk
```
and post the output.

---

### Post by cw_yong on 2007-12-20
When i key in as instructed. It informed me that tracert command is not found and recommended me to sudo apt-get install traceroute. I did that and it informed me that package traceroute is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. foloowed by E: Package traceroute has no installation candidate

---

### Post by solar george on 2007-12-20
Sorry, use tracepath instead of tracert

---

### Post by cw_yong on 2007-12-20
The error received were "getbyhostname2: Unknown host". I hope you can help me out with this....MY FRIEND

---

### Post by cw_yong on 2007-12-20
Sorry, i made a mistake...It should be "gethostbyname2: unknown error"...very sorry

---

### Post by solar george on 2007-12-20
Could you post your /etc/resolv.conf file.
Try 
```
nslookup bbc.co.uk
ping -c 5  bbc.co.uk
```

---

