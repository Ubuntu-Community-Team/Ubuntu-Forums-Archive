---
title: "internet"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by don3390 on 2007-03-31
I have dial up and thanks to your help have been able to get connected to the internet. No matter which web site I try to log on to I get "sever not found" Do I have to install something else to be able to search the web?  Ubuntu is on it's own hard drive

---

### Post by oilchangeguy on 2007-03-31
why would you use dial up? check out highspeed offers in your area. they start at under 20.00.  [http://comcast.usdirect.com/ar-warren-comcast-cable.html](http://comcast.usdirect.com/ar-warren-comcast-cable.html)

---

### Post by r4ik on 2007-03-31
Try disable ipv6,

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

Good luck.

---

### Post by don3390 on 2007-03-31
To disable IPV6 do I go to the termal? I went to the link and got the info. I'm not use to commands but trying. As for broadband I'd give anything if I had it. They have it on one side of a highway and my side no service as of yet. It's strange I can connect but not get any web site.Have a lot to learn about Linux, 72 now maybe by 100. thanks for your patience

---

### Post by Maestro23 on 2007-03-31
> **don3390 said:**
> To disable IPV6 do I go to the termal? I went to the link and got the info. I'm not use to commands but trying. As for broadband I'd give anything if I had it. They have it on one side of a highway and my side no service as of yet. It's strange I can connect but not get any web site.Have a lot to learn about Linux, 72 now maybe by 100. thanks for your patience

In your browser address window type:

about:config

scroll down until you see something like network dns IPv6... Click on it and it should say "True"

Restart Firefox and see if that helps.

This just disables it for firefox, not system wide.

---

### Post by don3390 on 2007-04-02
I just have one more question sorry to be such a pest. I have tried everything to get to a web site and nothing works, I disable IPv6 and all the other and still nothing. I'm at wits end I love what I see in all the sites I have gone to on Ubuntu. Question would it help if  installed another version of ubuntu than drapper? maybe kubuntu? Thanks for all your help so far. I know people older than I (72) who use linux so it can't be age thing.

---

### Post by airtonix on 2007-04-02
open your terminal program of choice....and post the response of : 

> ifconfigalso try this : 

> ping google.comif thats not give you a continual stream of information that include milliseconds then maybe try this to confirm your actualy connecting via your ISP's servers.(if you know what the dns server IP addresses are....you should becuase this is essential to finding any hoston the internet.) any way run this to see if you can touch your ISP..:

> ping xxx.xxx.xxx.xxxreplace the 'x's with your ISPs DNS server IP address.

ps: age is a state of mind.....anyone who tells you otherwise is a hallucination. rofl

---

