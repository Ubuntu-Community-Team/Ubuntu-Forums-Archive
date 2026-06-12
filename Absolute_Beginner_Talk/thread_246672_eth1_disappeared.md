---
title: "eth1 disappeared"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-08-29
my wireless card eth1 disappeared when I tried to install my wireless drivers. what happened?

---

### Post by meng on 2006-08-29
What's the output of
iwconfig

---

### Post by friedokra on 2006-08-29
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


- it included eth1 up until about 15 minutes ago. I followed these bunk-*** instructions listed here- [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=configure+broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=configure+broadcom)

my wireless card used to work, but today it quit and I was following the instructions in the how-to above. now my eth1 has disappeared and I am in a panic cause I have to use this notebook laptop at school tomorrow

---

### Post by friedokra on 2006-08-29
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

I think this is what did the damage. Is there anyway to get my blessed eth1 back?

---

### Post by friedokra on 2006-08-29
it was here and now it is gone

---

### Post by annda on 2006-08-29
sorry, ndiswrapper is a stranger to me.

i know cross-posting is really BAD, but if it's urgent maybe you should post your problem in the networking forum - i suppose the chances of getting an answer may be a bit higher there.

---

