---
title: "Can one host a website with a DHCP?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-02-11
I have an older computer that doesn't see a lot of use, so I had the idea to use it as a server for my fiancée's website.

However, I've only ever heard of people doing that with Static IP's. Is it possible to host a website on my DHCP connection? I'm not holding a lot of hope, because I realize that the server machine needs a physical  "address" so people can access it from the net. 

(If I said anything that doesn't make sense, it's because I actually don't know ANYTHING about the mystery of the internet)

---

### Post by hyper_ch on 2008-02-11
it is possible...

however if you want to operate an email server then you need a static ip.

But one would need more information.

Would the server be behinde a router?
Do you want your own domain name or could it be something like YOURNAME.no-ip.com?

---

### Post by Pogeymanz on 2008-02-11
Cool. Since I am a complete noob when it comes to the internet, can someone point me toward a guide on how to do this? I only have a very vague idea of the things that need to be done; and I have no clue on how to do it with DHCP.

---

### Post by pt_lam on 2008-02-11
> **hyper_ch said:**
> it is possible...

however if you want to operate an email server then you need a static ip.

But one would need more information.

Would the server be behinde a router?
Do you want your own domain name or could it be something like YOURNAME.no-ip.com?

Can you tell some more about this?
Thanks!

---

### Post by hyper_ch on 2008-02-11
basically:

(1) Setup your server

(2) If you are behind a router, assign it a static IP and router port 80 from your router to the server

(3) decide on whether you want to use no-ip.com or dyndns.org
--> Both of them provide you with client tool that will auto-update your IP in their DNS. Both are free of charge but require a registration

(4) depending on which one you used, install the clients

---

### Post by jaytek13 on 2008-02-11
> **hyper_ch said:**
> basically:

(1) Setup your server

(2) If you are behind a router, assign it a static IP and router port 80 from your router to the server

(3) decide on whether you want to use no-ip.com or dyndns.org
--> Both of them provide you with client tool that will auto-update your IP in their DNS. Both are free of charge but require a registration

(4) depending on which one you used, install the clients


Just to add to #2, you actually have to set up all networked interfaces connected to the router to have a internal static IP below the routers normal range. Like, if the router starts assigning internal IP's at 192.168.1.100, you would want to start assigning your devices at, say, 192.168.1.50. This will prevent IP renewal, but if a single device on your network is assigned an internal IP >= the routers default range the IP renewal request will take place and you would be assigned a new external IP, which will mess up your configuration.

---

### Post by gvartser on 2008-02-11
> **hyper_ch said:**
> it is possible...
however if you want to operate an email server then you need a static ip.


Well its possible, i had my e-mail server with DHCP assigned IP from my ISP. Its a bit tricky, and I also got tired of all hack and spam attempts from certain Asian countries so I changed to gmail instead.

They have a free of charge service to host your whole domain with email accounts etc.. Really nice and then you also get their web interface.

* [http://www.google.com/a/help/intl/en/users/user_features.html#utm_medium=et&utm_source=gmail-en&utm_campaign=crossnav](http://www.google.com/a/help/intl/en/users/user_features.html#utm_medium=et&utm_source=gmail-en&utm_campaign=crossnav)

/g

---

### Post by hyper_ch on 2008-02-11
> **gvartser said:**
> Well its possible, i had my e-mail server with DHCP assigned IP from my ISP.
Sure it's possible, but most mailservers will not accept mail coming from a mailserver with DHCP...

---

### Post by Pogeymanz on 2008-02-11
What do you guys mean when you say "behind a router?" Do you mean physically between the modem and the router or is "behind a router" some jargon that I don't know?

Do I have a choice of whether or not to put it "behind the router"? We do have a wireless router with only one computer physically plugged in to it.

We bought a domain name and she was going to pay for a webhost, but I had the fancy idea to host it ourselves.

Also, how does one go about assigning all these internal IP addresses.

It's sad: I consider myself relatively computer-competent, but I don't know much of anything about networking or the internet.

---

### Post by samb0057 on 2008-02-11
You can but it's kind of a pain. Look up no-ip and dyndns on google.

---

### Post by dstew on 2008-02-11
Not to bring down the party, but most ISP's specifically forbid you to serve web pages to the net over your home connection. You have to read your contract to be sure.

---

### Post by hyper_ch on 2008-02-11
well, you have to see if the place where you bought the domain supports dns-ing to your dynamic domain from no-ip or dyndns... or whether you can setup your own nameserver - but that would make it a lot more complicated...

---

### Post by stchman on 2008-02-11
> **EmosSuck777 said:**
> I have an older computer that doesn't see a lot of use, so I had the idea to use it as a server for my fiancée's website.

However, I've only ever heard of people doing that with Static IP's. Is it possible to host a website on my DHCP connection? I'm not holding a lot of hope, because I realize that the server machine needs a physical  "address" so people can access it from the net. 

(If I said anything that doesn't make sense, it's because I actually don't know ANYTHING about the mystery of the internet)

It can as long as your IP does not change very often.  I have Charter and I have had the same IP for a long time.

Some ISPs change the IP often which would require you to change them in the DNS.

If you want to have your own website there are a lot of place that will host your site for like $4 a month.

---

