---
title: "Making your Linux box safer."
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-06-08
Do any of you guys have any good security tips that I could use to make my system more secure.

---

### Post by Najand on 2007-06-08
What do you mean by "security" and what do you want exactly?

---

### Post by jonward0690 on 2007-06-08
Well I know Ubuntu is secure overall but how could I tighten the security up overall.

---

### Post by EXCiD3 on 2007-06-08
whatevar you do, DONT INSTALL WINDOWS. That would ruin everything ;)

Well, are you looking for firewalls, av software?

---

### Post by miggols99 on 2007-06-08
Well if you want complete control over what comes in and what goes out, I recommend getting a firewall, although iptables (the one built in) should be ok for most people.

---

### Post by jonward0690 on 2007-06-08
> **EXCiD3 said:**
> whatevar you do, DONT INSTALL WINDOWS. That would ruin everything ;)

Well, are you looking for firewalls, av software?

Well I have firestarter installed and I know that buy default your whole system has all its ports closed but hey if you know anything better than firestarter I am all ears.

---

### Post by starcraft.man on 2007-06-08
> **jonward0690 said:**
> Well I know Ubuntu is secure overall but how could I tighten the security up overall.

The most insecure thing in Ubuntu, I think, is the browser. If there ever is an infection (should there ever be one to attack Ubuntu), the browser will likely be the vector for it. I use [No Script]("https://addons.mozilla.org/en-US/firefox/addon/722"), [Ad Block Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865") and [Cookie Safe]("https://addons.mozilla.org/en-US/firefox/addon/2497") to lock down firefox. I think thats it. IP Tables is good enough for almost everyone. I even more than that have a NAT firewall with no holes that makes me stealthed.

---

### Post by hyper_ch on 2007-06-08
detach it from the network :) that should do the job ;)

---

### Post by Rotaj on 2007-06-08
From what I understand, Firestarter is the front end for the internal firewall. the IP tabes are controlled from the kernel.

Maybe this document explain security from within Ubuntu.
[http://psychocats.net/ubuntu/security#firewallantivirus]("http://psychocats.net/ubuntu/security#firewallantivirus")

---

### Post by starcraft.man on 2007-06-08
> **hyper_ch said:**
> detach it from the network :) that should do the job ;)

LOL! Thats not practical, how ya gonna post on forums then? By magic? :p

In all seriousness though, do try my 3 extensions... they are just a bit inconvenient but once you set them for the site you view, you never have to deal with it again.

---

### Post by Najand on 2007-06-08
I think there is no need for more security if you just want to use the network for daily use.

---

### Post by TriggerHappyChewie on 2007-06-08
[http://www.bastille-linux.org/](http://www.bastille-linux.org/)

---

### Post by jonward0690 on 2007-06-08
> **hyper_ch said:**
> detach it from the network :) that should do the job ;)

Yea maybe but you know I kind of like to use the internet.

---

### Post by drascus on 2007-06-08
What I would suggest is like others said run Firestarter it is a good firewall config. tool. Then There is a little program called Avast which is a free Virus scanning software for linux and windows. I don't think virus scanning is overly necessary but it helps you to not infect a windows computer should you get an infection. I think that Ubuntu is overall pretty safe but there could always be that day when things change so its best to be careful.
~Mike~

---

