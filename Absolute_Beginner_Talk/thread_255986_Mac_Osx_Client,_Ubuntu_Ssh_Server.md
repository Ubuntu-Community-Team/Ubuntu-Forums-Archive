---
title: "Mac Osx Client, Ubuntu Ssh Server"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-09-12
after pulling out alot of hair just wanted to post a quick howto on getting mac osx to ssh into a ubuntu server...

if you are having problems doing this, as i was, the problem is not your ubuntu box... considering you have ubuntu ssh set up properly and your network is also set up properly you have to add your UBUNTU box to your NETINFO MANAGER > HOSTS...

OPEN APPS > UTILITIES > NETINFO MANAGER >HOSTS
then DUPLICATE your local.  modify local to read

ip_address      YOUR IP
name            ubuntu netbios name
serves          ./local


to make things easier, add an account on your ubuntu box with your mac username....  

then on the mac ssh -vvv ubuntu ip

IT SHOULD WORK - GOOD LUCK

---

### Post by m_bridge on 2006-11-01
works for me, thanks! i was ](*,)

---

### Post by paynito on 2007-10-28
i couldn't get it to work, mind posting screenshots of the netinfo manager? i didn't know exactly what to do there

---

