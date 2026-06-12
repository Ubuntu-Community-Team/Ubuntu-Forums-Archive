---
title: "Slow internet connection"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Cardmaster91 on 2006-08-14
It seems like my internet connection is slowing down. When i first started up, it was goin at about 500k/s, and now its at like 10k/s. I know this only from downloads. is there a way i can manage my internet connection?

---

### Post by earobinson on 2006-08-14
could be that the servers are cloged, do a ping google.com and tell us what the results are

---

### Post by Cardmaster91 on 2006-08-14
> could be that the servers are cloged, do a ping google.com and tell us what the results are


i dont understand. do a ping google.com?

---

### Post by earobinson on 2006-08-14
in the terminal type "ping google.com" and cut and paste the first 10 or so lines

---

### Post by Cardmaster91 on 2006-08-14
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from google.com (72.14.207.99): icmp_seq=1 ttl=234 time=50.3 ms
64 bytes from google.com (72.14.207.99): icmp_seq=2 ttl=234 time=48.5 ms
64 bytes from google.com (72.14.207.99): icmp_seq=3 ttl=234 time=45.4 ms
64 bytes from google.com (72.14.207.99): icmp_seq=4 ttl=234 time=44.9 ms
64 bytes from google.com (72.14.207.99): icmp_seq=5 ttl=234 time=47.5 ms
64 bytes from google.com (72.14.207.99): icmp_seq=7 ttl=234 time=51.7 ms
64 bytes from google.com (72.14.207.99): icmp_seq=8 ttl=234 time=48.0 ms
64 bytes from google.com (72.14.207.99): icmp_seq=9 ttl=234 time=45.5 ms
64 bytes from google.com (72.14.207.99): icmp_seq=10 ttl=234 time=45.7 ms
64 bytes from google.com (72.14.207.99): icmp_seq=11 ttl=234 time=49.1 ms
64 bytes from google.com (72.14.207.99): icmp_seq=12 ttl=234 time=51.7 ms
64 bytes from google.com (72.14.207.99): icmp_seq=13 ttl=234 time=48.1 ms


p.s. it took like 5 minutes to load ubuntuforums.org

---

### Post by earobinson on 2006-08-14
ubuntu forums are being slow for me to, I think its a fourm problem, your net connection seems a bit slow (mine is 20) but that could just be your area, if people are using some kind of p2p on your network that could cause it, but if all sites but the forums are fine then its the forums servers not your computer

---

### Post by Cardmaster91 on 2006-08-14
ok, thanks

---

### Post by earobinson on 2006-08-14
np

---

### Post by Kurt` on 2006-08-14
Open Firefox.

Type about:config into address bar, and hit enter.

Scroll down to network.dns.disableIPv6 and set it to TRUE

Restart Firefox.

Enjoy.

If you're psycho and want to go one step further: [http://ubuntuforums.org/showpost.php?p=1276469&postcount=7](http://ubuntuforums.org/showpost.php?p=1276469&postcount=7)

---

