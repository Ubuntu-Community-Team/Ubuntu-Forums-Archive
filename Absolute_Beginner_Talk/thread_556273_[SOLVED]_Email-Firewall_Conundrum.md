---
title: "[SOLVED] Email-Firewall Conundrum"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-09-21
Okay, I'm in a catch-22.

My ISP just blocked port 25, so I shifted to 465. 465 needs SSL. Guarddog 2.5 doesn't have a setting for SMTPS, so I still couldn't send. Guarddog 2.6 does have SMTPS so I thought of going to Gutsy early, but it turns out that Gutsy still uses 2.5... 

If you've ever watched a noob troubleshoot, you know that much took a few hours to figure out.

I'm running Firestarter at the moment so I can send mail, but I was using Guarddog because my LAN doesn't work under Firestarter. 

The LAN isn't exotic - two boxes, both with network cards to the net, and both with second network cards to each other. Why? Because I have cards, because it's very easy to configure securely, and neither box relies on the other being booted to get online. It's handy, but it's outside of what Firestarter can handle.

So... does anyone see an option I missed along the way? I'm kinda surprised to be cornered.

---

### Post by ayenack on 2007-09-21
You could download the [2.6]("http://www.simonzone.com/software/guarddog/#download") version and install that.

ayenack.

---

### Post by ofb on 2007-09-21
May do, but that's unattractive.

A great deal of what I like about Ubuntu is Synaptic keeping track of patches, and some updates.

The mess with ClamAV kinda warned me off installing major programs on my own. First there's the little issue that I'll have to keep an eye for security patches myself thereafter. And, if I understand the ClamAV saga correctly, dependencies can become a real problem. What I gather is the newer ClamAV requires newer libraries, which remove the old ones, which breaks other apps, and then reverting, once you realize what's wrong, is a true rump-sore.

I find I'm having enough trouble making time to deal with the simple software problems I run into. So I'm reluctant to leave the Ubuntu's cozy nest of pre-tested software.

Twenty years ago I would have been game, but these days I can't put in the late nights to sort out adventures. So, that's good advice and I thank you for it, but what I'm hoping to find is a way the stock components can be put together and work.

---

### Post by ofb on 2007-10-09
[http://www.mepis.org/node/13709](http://www.mepis.org/node/13709)

> For future readers, the specific steps I used are:
1)in Guarddog, advanced tab,click 'New Protocol' then
create name SMTP, type TCP, port 465, click Apply.
2)next, pick 'protocol tab', 'internet zone',
expand the 'user defined' selections and check the
box for SMTP (which was created in step 1) above.
3) click 'Apply' and you should be done.

---

