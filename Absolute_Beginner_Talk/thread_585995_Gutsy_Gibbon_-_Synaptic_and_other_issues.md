---
title: "Gutsy Gibbon - Synaptic and other issues"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by steelklvr on 2007-10-21
Hello,

I have recently installed Gutsy Gibbon on my PC and since doing so I have been unable to download any information regarding the Synaptic Package Manager's sources from either my local server (New Zealand) or the main server. I constantly keep getting time out errors when trying to download from the servers.

Also when using Pidgin, I cannot connect to my MSN account. I can connect through webmessenger or through Windows XP with no issues however I, once again, get time out errors when trying to connect through Pidgin. (I don't know if it affects all IM transmissions because i only use MSN)

Initially I was also unable to load web pages, however, changing the network.dns.disableIPv6 value to true in about:config for firefox fixed this error.

All of the above issues were non-existent for me in Feisty Fawn and any help resolving these issues would be appreciated.

Further information:

[LIST]
[*]I have a wired internet connection.
[*]I upgraded to Gutsy Gibbon, so this is not a fresh install.
[/LIST]

Thanks.

---

### Post by callum_G on 2007-10-24
I have this exact problem as well (and also in NZ), except my install was new. I find this strange as my previous ubuntu installations (6.06--7.04) always connected without a problem.

---

### Post by BroadArrow on 2007-10-24
I've had a few of the sources coming up "failed" for a while now on Feisty in New Zealand. Don't know if this it's related. I'm upgrading to Gutsy now so will see if all the sources will fall over...

---

### Post by realvz on 2007-10-24
can you try another mirror for repos in synaptics?

---

### Post by Caffeine_Junky on 2007-10-24
hey guys,   I was having simular issues as well in the begining, ...and my Sources.list was really messed up because of mirrors not responding.

I found this list posted on the forums by one of our Mod's (there personal list)  ...so I have replaced my original list with this one:
(and backed up the original of course)

```
# Base.
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

# Security.
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
```

This is working for me at the moment, ...I have looked over it many times and compared it too my orignal Sources list and I am pretty sure it contains all that is needed as to cover the main lists for Gutsy.

If anyone can see something is missing from it that is required for the Basic repo's please point it out :)

---

### Post by steelklvr on 2007-10-24
I managed to fix the issue I was having here.

The solution is in this thread.

[http://ubuntuforums.org/showthread.php?t=587225&page=2](http://ubuntuforums.org/showthread.php?t=587225&page=2)

This might help the rest of you as well.

---

