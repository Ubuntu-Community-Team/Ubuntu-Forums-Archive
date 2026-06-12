---
title: "Web pages only display when IP is typed?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by woolyg on 2006-12-05
Hi all,
Relative noob here. I have Ubuntu 6.06 running in VMWare, and it's going quite sweetly, apart from the fact that I can't view web pages.

- I can ping google, and get a reply, and ping other PC's on my network. Sweeeeeet.
- I can't view websites.
- However, I when I type in an IP for a site (say 216.239.53.99 for google) it displays the page OK.

Anyone else seen this before? I'm led to believe its some kind of DNS thing, but I have no idea... 
All help appreciated.
Wooly

---

### Post by nickburns on 2006-12-05
Shut down the vmware OS and change the networking option from NAT to Bridged or visa versa and see if that helps.

---

### Post by woolyg on 2006-12-06
Thanks for the reply Nick.

It was originally on bridged, and I could only view sites by typing the site IP (which shows that the connection is there somewhere!)

I tried what you said, changed it to Host-Only (NAT option was greyed out) and the sites displayed fine.

Thanks for your help dude, much obliged!
Woolyg

---

### Post by goodha2 on 2006-12-06
i am having the EXACT same problem as you!

i tried typing in the IP and it worked fine just like you said, so im convinced this will for for me. but how in the WORLD do i go about Shutting down the vmware OS and changing the networking option from bridged to Host-only????

please any help is much appreciated!!
spence

---

### Post by woolyg on 2006-12-06
Are you using VMware?

If so, hit the big red 'stop' button to the top left - that will shut the virtual PC down. Then DOuble click on where it says 'Ethernet'... you'll be able to change the setting there!

Wools

---

### Post by goodha2 on 2006-12-06
i dont have vmware, heres my dealio;

i installed ubuntu,

thats where im at :)

im trying to figure out how to change whatever to host only, with no luck!

spence

---

### Post by woolyg on 2006-12-06
I've a feeling your issue would probably be DNS based (in your networking settings).. anyone concur?
Woolbat

---

### Post by Chinkostu on 2006-12-06
> **goodha2 said:**
> i dont have vmware, heres my dealio;

i installed ubuntu,

thats where im at :)

im trying to figure out how to change whatever to host only, with no luck!

spence

thats just for VMware. are you having exactly the same problem on a HDD install?

---

### Post by ferg on 2006-12-06
> **woolyg said:**
> I've a feeling your issue would probably be DNS based (in your networking settings).. anyone concur?
Woolbat
 
+1... I'm with you on this :p I had this a few months ago when my provider randomly decided to change their DNS servers without notifying people. Fine if you have them set on auto, but I like my all manually configured. Pain... took me a while to work out.
 
Perhaps check your DNS settings on your router/modem? If they aren't already, setting them to automatic might be the best option for the interim. That would be my best guess without any more details from you! :) Hope this is of some help! :D
 
Fergus

---

### Post by OneSeventeen on 2006-12-07
I am having similar issues, but the problem is even if my router has the DNS IP's, Ubuntu still defaults to the following (which never works for me):```
search localdomain
nameserver 192.168.136.2
```

I just change it manually to the IP's I find on my router's status page and it works.

The problem is, when I'm on other networks, I can't always access their router's status page.

How do I set Ubuntu to automatically get a DNS host and find out what domain goes where?  (simply clearing the contents of /etc/resolv.conf makes it default back to 192.168.136.2)

---

