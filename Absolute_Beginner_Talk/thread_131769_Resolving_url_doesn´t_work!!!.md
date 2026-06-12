---
title: "Resolving url doesn´t work!!!"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by rawblood on 2006-02-17
Hi there...

I´m pretty new to linux and have just intalled ubuntu on an ArmadaM700 and now I´ve got an odd problem...

The thing i that when a I write an url i firefox it doesn´t resolvet, but sometime it does!!?!? 

I kan ping for exampel [www.google.com](www.google.com) and it resolves the IP and the site answers, but not firefox! BUT this is the odd part, somtime it works but not always?!

The biggest problem with this is that I can´t use apt-get!!!

I´ve searched everywhere and tried a lot byt nothing works? Some GURU here who knows what to do....?

---

### Post by alamba on 2006-02-17
check
#cat /etc/resolv.conf

it should have your ISP DNS addresses in it. Are you using a proxy too?
What's the problem with apt-get? What are the errors you're getting? Have u tried synaptic?

A

---

### Post by rawblood on 2006-02-17
Thx for your fast answer!
I´m using a router as dns forwarder, so the routers dns adress is in resolv.conf.
But correct me if I´m wrong, if the dns is the problem I wouldn´t be abel to resolve url with ping...wich I can!

Well apt-get uses url names and not ip adress to get the deb pakages so I can´t connect to the servers. I get "connection timed out".

No not tried synaptic, but I will thx for the tip.

---

### Post by essexman on 2006-02-17
[quote=rawblood]Hi there...

I´m pretty new to linux and have just intalled ubuntu on an ArmadaM700 and now I´ve got an odd problem...

The thing i that when a I write an url i firefox it doesn´t resolvet, but sometime it does!!?!? 

I kan ping for exampel [www.google.com]("http://www.google.com") and it resolves the IP and the site answers, but not firefox! BUT this is the odd part, somtime it works but not always?!

The biggest problem with this is that I can´t use apt-get!!!

I´ve searched everywhere and tried a lot byt nothing works? Some GURU here who knows what to do....?[/quote]

Hi rawblood, well done for trying.

A couple of questions:
Are you using a different set up to make this post?
Have you tried rebooting your modem and router? - Switch off each for twenty seconds. 

 It sounds silly but these are complex machines and they sometimes block certain sites.  Once I 
could get ubuntuforum but couldn't get gnome or google; rebooting the router fixed it, but worth trying both.

---

### Post by rawblood on 2006-02-17
Yes have tried rebooting the router/modem but it doesn´t work either. The thing i it works fine on alla my other system exept for umbutu...
Know I´ve installed kubutu in a vmware session here at work and will see if it works at home.

I think its a problem with the nic driver for the armada...will intall umbutu at home to in a vmware session to rule out the router.

---

### Post by soonindallas on 2006-02-17
Try disabling IPv6 support in firefox. It's enabled by default and gives problems unless you're using IPv6, which I doubt...

in firefox, enter "about:config" in the location bar.

in the filter bar type "ipv6"

you should see an attribute "network.dns.disableIPv6": you want the value to be true for IPv6 to be disabled.

if the value of the attribute is "false", double-click it to toggle to "true"

you might need to quit and restart firefox.

post back on your progress.

---

### Post by _simon_ on 2006-02-17
I had this problem.

I managed to get a website to open once via the URL. Had to use the IP's.

Doing this resolved my issue:

[http://www.ubuntuforums.org/showpost.php?p=50664&postcount=2](http://www.ubuntuforums.org/showpost.php?p=50664&postcount=2)

---

