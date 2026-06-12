---
title: "pidgin buddy icon problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by marojahan on 2007-11-01
hi all.. 

first i'm sorry, i don't know if this is the right forum, but i dont know where else to ask..

before i use fietsy an use with gaim as it default messenger app

before i able to display the buddy icon .. but since i use gutsy . with pidgin 2.2.1 as it IM app.. i cannot display buddy icon of my yahoo contacts..

i've search all over the internet (maybe not all :)) but a cannot find the answer.. 

so please if any of you can give me a solution for my problem..


thanx..

---

### Post by marojahan on 2007-11-06
does anyone in this universe know how to soleve my problem (pidgin 2.2.1 buddy icon problem)..

or only GOD knows????

i love ubuntu.. everything.. but this one.. it's pain in the neck.... this make my ubuntu sucks.. 

so just please..

---

### Post by kstella on 2008-01-26
Wow, I feel bad that no one's replied to you yet.

Do you access the Internet through a proxy?  Some people who do (like me) can't see the buddy images because of the way the proxy is configured.

[One guy said this worked for him]("https://answers.launchpad.net/ubuntu/+source/pidgin/+question/18187"), but it doesn't work for everybody; still maybe you might want to try:

In Pidgin, Tools > Preference > Network then set to "No Proxy."

---

### Post by monsieurrigsby on 2008-03-07
Having the same problem and read through the linked question (18187).

Unless they're using an old distro or self-compiled newer Pidgin, I'm confused since Pidgin 2.2.1 (the default on Gutsy) doesn't have any proxy settings on the main Tools preferences (only on the per account settings).

I'm at work where I need to use a proxy for HTTP, but need to set the No Proxy in the Yahoo account on Pidgin so it can use port 5050 for the main connection (otherwise I can't connect at all with a "proxy won't allow tunnelling port 5050" type msg).

So, from the error msgs on mine, I'm assuming that the problem is because I'm using no proxy, but need to use port 80 (HTTP) for the file transfers and buddy icon gets, which is being blocked because I'm not using a proxy (does that make sense?!)

i.e. I need to use no proxy for the port 5050 messaging but an HTTP proxy for the rest. I will see what our proxy admin thinks next week and let you know any developments (obviously best if can use proxy for both, but don't know what the HTTP proxy option on the Yahoo prefs means in this context). Maybe it's a bug in Pidgin that you can't set proxies separately for HTTP and "everything else".... for Yahoo (or that, if you set HTTP proxy, it should avoid the proxy for all non port 80 traffic)?

I could be completely wrong of course but the log shows HTTP failures which makes total sense. If any better sys admin can help, please jump in!

Cheers,
MonsieurRigsby

---

### Post by fireworksshow on 2008-06-15
I'm having the same problem. Played around for about an hour with various proxy settings nothing seems to do the trick. Any other suggestions?

---

### Post by monsieurrigsby on 2008-06-16
See [Ubuntu bug #164301]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/164301/") - I've added comments to that largely as per my comment here (but with log detail). May be of use.

---

