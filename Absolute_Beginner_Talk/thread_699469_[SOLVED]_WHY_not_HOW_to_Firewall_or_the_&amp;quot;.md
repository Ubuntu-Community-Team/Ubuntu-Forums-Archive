---
title: "[SOLVED] WHY not HOW to Firewall or the &amp;quot;best&amp;quot; way to firewall"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-02-17
I apologize. I know everybody else must understand how to firewall. I would use Firestarter if I only knew what I was doing.

Below is the Ubuntu Community Firestarter document link (help)

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

in it, I see how easy it is to use. Great. 

What do I want to do(?), I can see how to do it.

Does it start by blocking NO connections? Or ALL connections? Does it have some "smarts" and know to block those that are on a 'blacklist'? 

I "share" a wireless connection. That is, this computer and another share a DSL via a wireless modem. We may add another party to this modem, too. This is an AT&T 2Wire device.

If I set up Firestarter on this computer, will it affect others on the network?

I'm sorry to ask what seem like dumb questions as I type them, but all too often the How-To(s) say How, but not Why!

---

### Post by oilchangeguy on 2008-02-17
you've been around long enough to know ubuntu has a built in firewall, iptables. and firestarter is simply an un-needed gui.

---

### Post by Mark_in_Hollywood on 2008-02-17
> **oilchangeguy said:**
> you've been around long enough to know ubuntu has a built in firewall, iptables. and firestarter is simply an un-needed gui.

You are completely wrong about this. I have used Ubuntu for about 3 years, but am completely unversed in the technology. I had no idea that a firewall was "in-built" in Ubuntu. 

P.S. Dear Administrators

This post is an excellent example of why it isn't a good idea to award "beans" for people who post a lot. Almost without exception I'm the one who posts a question or needs a response, not vice versa.

---

### Post by sb12 on 2008-02-17
> **Mark_in_Hollywood said:**
> You are completely wrong about this. I have used Ubuntu for about 3 years, but am completely unversed in the technology. I had no idea that a firewall was "in-built" in Ubuntu. 

P.S. Dear Administrators

This post is an excellent example of why it isn't a good idea to award "beans" for people who post a lot. Almost without exception I'm the one who posts a question or needs a response, not vice versa.

considering your bean count is hidden I am guessing he went by the fact that you registered in Mar of 06.  My question is if you didnt know there was a firewall built in and have obviously had no need to research it, why do you need one now?

---

### Post by ibanez on 2008-02-17
For me theres only oneword for firewall......  SMOOTHWALL.

use this for a while and you'll soon learn all you need.

Plus its pretty secure out of the box, Once familiar with it then start looking at the community addons for the perfect customised firewall.

Smoothwall.org

---

### Post by jaytek13 on 2008-02-17
> **sb12 said:**
> considering your bean count is hidden I am guessing he went by the fact that you registered in Mar of 06.  My question is if you didnt know there was a firewall built in and have obviously had no need to research it, why do you need one now?

This is the beginner forum. If you don't have something to contribute to the question asked you should refrain from posting, not post questions about "why do you want to do this." 

In any case, for the OP, yes, there is a built in firewall called IP tables. The use of something like firestarter is completely unnecessary and reserved for people who want more control or need added security for running things like servers. Otherwise, the normal configuration for iptables is fine for most normal users. It blocks all ports by default, and will open up ports as requested by applications you've installed on an as-needed basis, and close them once the port is no longer in use.

---

### Post by Mark_in_Hollywood on 2008-02-17
> **sb12 said:**
> considering your bean count is hidden I am guessing he went by the fact that you registered in Mar of 06.  My question is if you didnt know there was a firewall built in and have obviously had no need to research it, why do you need one now?

1-I'm embarrassed by me "bean count". 
2-Please know that the link does not specify M$, which we ALL know is the source of so much virus, trojan, service packs, BSOD, etc.

*Google dons the cape of justice (slight exaggeration)*
[http://www.arsgeek.com/?p=3561](http://www.arsgeek.com/?p=3561)

I'm concerned, and probably everybody should be concerned about what  Dawn Masuoka talks about in this post. I have no knowledge that Linux is less vulnerable to such attacks, except that we are a fraction of computer users compared with M$. As I understand this, what she is speaking of is OS independent. Also recently I read about Java being the new vector for attack, and again, I'm not well versed technologically-wise, but I am under the impression that Java is OS independent as to these mal-wares, too.

Thanks for your response and questions.

---

### Post by sb12 on 2008-02-17
> **Mark_in_Hollywood said:**
> 1-I'm embarrassed by me "bean count". 
2-Please know that the link does not specify M$, which we ALL know is the source of so much virus, trojan, service packs, BSOD, etc.

*Google dons the cape of justice (slight exaggeration)*
[http://www.arsgeek.com/?p=3561](http://www.arsgeek.com/?p=3561)

I'm concerned, and probably everybody should be concerned about what  Dawn Masuoka talks about in this post. I have no knowledge that Linux is less vulnerable to such attacks, except that we are a fraction of computer users compared with M$. As I understand this, what she is speaking of is OS independent. Also recently I read about Java being the new vector for attack, and again, I'm not well versed technologically-wise, but I am under the impression that Java is OS independent as to these mal-wares, too.

Thanks for your response and questions.

if it is a java exploit your best bet would be to run noscript in firefox, it blocks most java/flash/etc unless you tell it not to specifically.  also, if you connect through a router they normally have a hardware firewall built in.  and to the other poster who decided it would be a good idea to try and flame me, I asked a valid question and I dont appreciate you trying to act as though I didnt.  kthxbai

---

### Post by Mark_in_Hollywood on 2008-02-17
Thanks, I'm marking this a solved to prevent any flaming.

Thank, community.

---

### Post by r4ik on 2008-02-17
You have mail :)

---

