---
title: "what not to type in console"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-10-08
**sudo rm /*/*.***

I have a folder that contains a lot of folders, and I wanted to delete every file in every folder that was in the folder i was currently in.

Then I typed **ls** to see if it worked... and bash: can't find /bin/ls.

so I reinstall and here I am. *wipes sweat*

anyone ever do anything similar?

---

### Post by tehwa on 2005-10-08
> sudo rm /*/*.*
nice.

I've never done anything similar, but I think it's only a matter of time before I do.

---

### Post by xmastree on 2005-10-08
:roll: 
Next time, type:```
sudo nautilus
```then browse to the relevant folder, select all, and delete that way.

---

### Post by nerdman on 2005-10-08
I wanted to, but evidently since this was the folder "My Documents" pointed to when I used this drive in windows, there's funny permissions on it and I can't modify it. however, my best friend ubuntuguide.org has a section on running nautius as root and I should be able to do it then, no?

---

### Post by heimo on 2005-10-08
When configuring firewall remotely using ssh, consider twice before:
```
iptables -F INPUT
iptables -P INPUT DROP

``` 
It's kind of a good security practice... Kind of.

For those who don't know iptables, abowe two lines first flush the input chain rules (incoming / ingress) and then sets default policy to drop all incoming packets. Usually it's a good idea to configure firewall this way (idea is to then allow all the valid traffic instead of other way around), but not if you're 300 miles away and using remote connection. :D (ok, it's not a smart idea to do anything on production servers before testing somewhere else)

Funny thing is - you almost always realise that you're doing something stupid just a split second before hitting enter.

---

