---
title: "Are NoScript and AdBlock Plus nessecary?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-08
When I used XP, I grew quite paranoid and used these two FF extensions to help lock down the system. Well, the NoScript one anyway helped block stuff that actually might to harm.

Are these useful if you are running linux? Should I keep using AdBlock, but not NoScript, or is it still a good safety measure?

---

### Post by Outrunner on 2007-07-08
AdBlock Plus is definitely useful, install it as fast as possible. And as for NoScript, I highly doubt this is needed, but if it makes you feel more secure, then go for it

---

### Post by starcraft.man on 2007-07-08
I still use both. The browser may just be the most insecure thing on any linux box (since it interacts so directly with the internet), and there are some still existing exploits with firefox. I find it only prudent to stop javascript (and worse, cross site scripting, google it) at its source. That said, up to you. I find it most likely that the browser will be used as the means/vector to attack a Linux box (if an attack ever pushed into wild) rather than anything else.

---

### Post by aysiu on 2007-07-08
Considering many Firefox exploits (before they're patched) are related to JavaScript, it's probably not a terrible idea to use NoScript. I uninstalled it, though, because I got tired of whitelisting every site I visited. The truth is that I do trust the sites I visit. I'm not going to porn or pirated gaming ROM sites. 

As for AdBlock, that's your own choice. It's not for security purposes. It's mainly to just avoid the annoyance of seeing advertisements. If you don't mind advertisements, by all means, uninstall it.

---

### Post by jrusso2 on 2007-07-08
No script should be used on Linux as well as the problem is java script and that works on Linux and Windows.

I don't really understand why people use adblock and no script cause it seems like no script blocks the ads.

---

### Post by bodhi.zazen on 2007-07-08
I personally use NoScript and add sites like Ubuntu to the white list.

I use my hosts file for ad blocking rather then Adbolck as this protects more then just firefox.

Here is a link to the script :

[http://hostsfile.mine.nu/downloads/](http://hostsfile.mine.nu/downloads/)

Look at the bottom of the page for "Unix/Linux bash Hosts updater script (txt)  (m)"

Download the script and then :

```
sudo aptitude install tofrodos
sudo cp /etc/hosts /etc/hosts/org #.org for origional
chmod a+x updatehosts.sh.txt
sudo ./updatehosts.sh.txt
```

---

### Post by aysiu on 2007-07-08
> **jrusso2 said:**
> No script should be used on Linux as well as the problem is java script and that works on Linux and Windows.

I don't really understand why people use adblock and no script cause it seems like no script blocks the ads.
NoScript blocks static image ads?

I thought it blocked only Flash-based ads and such...

---

### Post by stupid head on 2007-08-11
I recommend Adblock Plus because it speeds up browsing and reduces annoyances without requiring much maintenance.

I don't recommend using NoScript because the way it works is too obtrusive. While I'm not against philosophy of blocking unnecessary scripts, the implementation is too annoying.The user has to take action every time she visits a new website and wants to take advantage of all its features.

NoScript appeals to the paranoid and is overkill for the average person. It's like surfing with cookie prompts enabled. Keeping the browser up-to-date is sufficient.

---

