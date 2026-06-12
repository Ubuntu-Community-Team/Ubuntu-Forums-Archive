---
title: "DNS Redirection on webpages"
date: 2011-12-27
forum: Apple Hardware Users
---

### Post by uhaditcomin on 2011-12-27
I have an iMAC running OSX 10.6.8
I recently revamped a laptop from running windows XP to running purely Ubuntu 11.10
Everythihg is linked via my home router - which is a BELKIN unit - connected to my cable broadband modem. The MAC is wired, the Laptop running Ubuntu is wireless, The Android Device is wireless, The Ipod Touch is wireless, and the XBOX 360 also is wireless connected.

Everything was working primo until I installed UBUNTU on the laptop and linked it all up. Now on the MAC and on the UBUNTU platform both, I constantly get this annoying web-page redirection to some odd domain when I go to the same standard sites I have always visited.

It happens using CHROME, FIREFOX, SAFARI browsers
I checked up on DNS redirection bugs and a few other things. None of the AV applications I have installed on any of the connected systems indicate any sort of infection or trojan

I flushed the Router and re-installed its configuration fresh. I changed the router name and password as well. That seemed to work for 24-36 hours but the issue is back

So I thought maybe its DNS poisoning at my ISP (Telstraclear NZ) so I have switched to OPENDNS just to check into that. I cleared the DNS resolver cache on the MAC and the UBUNTU system, I cleared browser caches as well.

Within minutes of going to one of my regular sitres... I got redirected AGAIN
Pllus I not that the OPEN DNS is nowhere near as quick as they claim - resolving webpages takes longer now than it did using my ISPs DNS...

If this is not DNS poisoning (hence the reason the switch to OPENDNS didnt provide any relief from the problem)....then I am at a loss....what could it be.

I post here because the ONLY time this issue popped up was within 12 hours of having installed UBUNTU and linking that into my home network. Before the UBUNTU installation I did not have this issue 


Any inputs welcome

---

### Post by uhaditcomin on 2011-12-29
OK... I believe I have it sorted

After some work to try and re-create the issue, and also process of elimination checks and verifications I concluded with a high degree of certainty that none of my connected systems were infected with any sort of trojan or malware.

Despite that I disconnected them all from the network, cleared their dns resolver caches, and their network host files

I connected a test system to the router, downloaded a new firmware revision for the router and re-imaged it. Then reconfigured it. Within 24 hours pointing to my ISPs DNS. I had the redirect issue back, so that confirmed to me that the 'poisoning' was coming from them.
I reflashed the router firmware, but this time set the DNS to OpenDNS - and thus far its been 24 hours and nothing - all clear.

---

### Post by bootedguy on 2011-12-29
In these instances, it is also important to clear your browser's cache.  If a website you have your browser pointed to has been compromised (with a hack of a .htaccess file on the server), your cache can be messed up.  In my experience, Chrome cache clears pretty well.  No so with IE.  I don't know about Firefox.

---

