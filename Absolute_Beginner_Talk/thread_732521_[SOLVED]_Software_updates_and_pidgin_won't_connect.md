---
title: "[SOLVED] Software updates and pidgin won't connect"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by pronihil on 2008-03-23
I know that my problem has something to do with tor, privoxy, and/or peerguardian. I feel like an idiot. I'm not that well versed in proxies or personal computer security in general, but a few days ago I was determined to install tor and peerguardian and protect myself more in the internet. Well... I tried installing vidalia as well as tor and privoxy, but for some reason, my computer cannot execute the "./configure" command, and since it's not offered in the repositories I already had, I decided to do without. Anyway, I installed an add-on for firefox called FoxyProxy, and it worked. But it was so slow, which I was expecting, but I had no idea how to modify the choice of proxies, or even why/how it worked. Eventually I decided not to use it, that it wasn't worth the trouble, especially since I had no idea what I was doing. So I removed tor and privoxy and peerguardian and restarted the computer. Now pidgin cannot connect and I can't update my software packages - it doesn't even start downloading, just mentions that the connection failed. 

Does anyone have... err.. any idea what I did and how I might fix it?

Also... weirdly, firefox works perfectly. It's just pidgin (and probably any other chat program) and software updating that cannot connect, which puzzles me more.

Please help!

---

### Post by dcstar on 2008-03-23
> **pronihil said:**
> I know that my problem has something to do with tor, privoxy, and/or peerguardian. I feel like an idiot. I'm not that well versed in proxies or personal computer security in general, but a few days ago I was determined to install tor and peerguardian and protect myself more in the internet. Well... I tried installing vidalia as well as tor and privoxy, but for some reason, my computer cannot execute the "./configure" command, and since it's not offered in the repositories I already had, I decided to do without. Anyway, I installed an add-on for firefox called FoxyProxy, and it worked. But it was so slow, which I was expecting, but I had no idea how to modify the choice of proxies, or even why/how it worked. Eventually I decided not to use it, that it wasn't worth the trouble, especially since I had no idea what I was doing. So I removed tor and privoxy and peerguardian and restarted the computer. Now pidgin cannot connect and I can't update my software packages - it doesn't even start downloading, just mentions that the connection failed. 

Does anyone have... err.. any idea what I did and how I might fix it?

Also... weirdly, firefox works perfectly. It's just pidgin (and probably any other chat program) and software updating that cannot connect, which puzzles me more.

Please help!

Ubuntu has proxy settings for general apps and also in Synaptic, check them.

---

### Post by pronihil on 2008-03-23
> **dcstar said:**
> Ubuntu has proxy settings for general apps and also in Synaptic, check them.

Umm... how would I check those settings? I've turned on Synaptic Package Manager and I'm not sure where proxy settings might be. 
Thanks for the advice though!

---

### Post by pronihil on 2008-03-23
Thank you! I've fixed it by going to System->Preferences->Network Proxy and choosing direct connection. I assume this is what you meant for me to do. :)

---

