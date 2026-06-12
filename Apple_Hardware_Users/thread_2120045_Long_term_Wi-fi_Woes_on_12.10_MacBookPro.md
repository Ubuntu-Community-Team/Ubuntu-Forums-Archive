---
title: "Long term Wi-fi Woes on 12.10 MacBookPro"
date: 2013-02-25
forum: Apple Hardware Users
---

### Post by neverbelievedf on 2013-02-25
Hello,

I am running Ubuntu 12.10 on a MacBookPro (8,2 I believe) with a Broadcom 4331 chip. Although I cannot remember the exact date, I am pretty sure that after the 12.10 upgrade (which was a clean install) I have has major Internet connection issues, mainly at the university I attend. My wifi is not only extremely slow in comparison to my Mac OS X partition and other people's computers, but it also disconnects randomly as well. I usually have more trouble in more crowded spaces, but if I switch over to my OS X partition, everything works absolutely fine and no different then if I am in a crowded area or not. Also this might be a coincidence with the timing of day (and it being crowded), my Internet will start off being excellent and slowly get worse and worse. After searching the Internet for months and having patience to see if this issue might be fixed it easily, I am now getting fed up with my lack of Internet during the day. Can anyone help me figure out what is going on?

I can post anything you want me to post that'll help and Ill try to get back to you ASAP. 

The Internet type here at school is a PeaP network. Though there are some access point here that aren't and I can connect to having the same issue.

Thanks in advance!

---

### Post by Jancis on 2013-03-06
try fiddling with wifi interface powersave setting:

disable powersave:
iwconfig eth1 power off

or enable it when you don't need big range, but want to save battery:
iwconfig eth1 power on

---

