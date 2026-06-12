---
title: "Ethernet internet not working (newbie help!)"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Srirangan on 2006-10-03
So.. I managed to install Ubuntu! :cool: 

So this is the scene, it boots and starts perfectly. I have ethernet based internet, which I'm using right now to post in this community forum (on Windows XP)!

Anyway, in Ubuntu, I goto Administration -> Network and eth0 says it is 'active'.

But then, when I goto Mozilla Firefox, and type [www.google.com](www.google.com) it says "connecting to server" and just stays then that's it. Nothing else!

Internet doesn't even work for Gaim and Add/Remove S/W. Thanks for putting up, I'm a noob! 

Any ideas?

- Sri

---

### Post by deadgobby on 2006-10-03
Did you try this.
[https://help.ubuntu.com/community/DapperUpgrades?action=fullsearch&context=180&value=ethernet&titlesearch=Titles](https://help.ubuntu.com/community/DapperUpgrades?action=fullsearch&context=180&value=ethernet&titlesearch=Titles)

---

### Post by Srirangan on 2006-10-03
I got the link via Google that was somewhat similar. That's how I found this forum. Anyhow, any ideas?

---

### Post by deadgobby on 2006-10-03
You are on a net work yes? Like live in a dorm in college or in a apt builing? Or you may be in a hotel? Which one????

---

### Post by Iowan on 2006-10-03
> **Srirangan said:**
> But then, when I goto Mozilla Firefox, and type [www.google.com](www.google.com) it says "connecting to server" and just stays then that's it. Nothing else!

What happens if you:
Open a terminal (Top left menu, then Accessories, then Terminal - or something like that (I'm working from a Windows box))
Enter **ping [www.google.com](www.google.com)**

I'm wondering if the DNS is messed up - or perhaps IPV6 is causing trouble...
Also, DHCP or static address?

---

### Post by Srirangan on 2006-10-03
I got Mozilla to work. Found the about:config IPV6 trick on the forum. Am trying to get the rest of the s/w's to work too.

Thanks!

---

### Post by deadgobby on 2006-10-03
That is good news. Please let the forum know if you still have probs
Gobby

---

### Post by ewingam on 2006-10-03
> **Srirangan said:**
> I got Mozilla to work. Found the about:config IPV6 trick on the forum. Am trying to get the rest of the s/w's to work too.

Thanks!

It sounds like I've been having the same problem, but I can't find this trick you mention.  Could you point me in the right direction?

---

### Post by Srirangan on 2006-10-03
> **ewingam said:**
> It sounds like I've been having the same problem, but I can't find this trick you mention.  Could you point me in the right direction?
Start Firefox, type in "about:config" into the url bar. Hit go.

Scroll down, look for:
network.dns.disableIPV6

By default this will be false, yo'll have to double click to set it to true. Do that and restart Firefox.

Now Firefox should be working.

---

### Post by ewingam on 2006-10-03
> **Srirangan said:**
> Start Firefox, type in "about:config" into the url bar. Hit go.

Scroll down, look for:
network.dns.disableIPV6

By default this will be false, yo'll have to double click to set it to true. Do that and restart Firefox.

Now Firefox should be working.

Thanks so much!  That worked like a charm!

---

### Post by Srirangan on 2006-10-03
> **ewingam said:**
> Thanks so much!  That worked like a charm!
Ye, but I ended up screwing up big time. With all my haste in fixing the netwroking issue, I ended up changing my hostname. Now my default account doesn't have admin access, and I'm handicapped. :(

---

