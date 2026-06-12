---
title: "Broadcom 4318 dapper..?"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by shane.reid on 2006-03-30
```
user@narnia:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"HSI_Conf"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off

sit0      no wireless extensions.
```

It comes up in the netowrk settings.. but nothing happens... plus when I leave it on, the computer freezes for a second every few seconds...  there is an error message in the log saying somethign about MAC sleep failing...

I already used fwcutter on the working .sys file from my windows drive and copied them accordingly.

---

### Post by shane.reid on 2006-03-30
Puhlease help meee!!!!

i want to use Ubuntu on my work laptop... but without wifi... it is useless

---

### Post by johnnymac on 2006-03-30
Okay....so in the Dapper support forum there's a forum specific to this issue.  You actually will have two choices...

1)  use ndiswrapper
2)  use the real driver 'cause it's provided now

Here's the post for it...

[https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx?action=show&redirect=WiFiBroadcomDriver)

---

### Post by shane.reid on 2006-03-31
I love you.  Ndiswrapper worked for my 4318 card...:KS

---

