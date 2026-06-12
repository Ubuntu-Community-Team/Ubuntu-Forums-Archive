---
title: "DNS settings - keep reverting to default"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by GaryReggae on 2006-07-28
Hi folks,

I'm having a problem with the DNS settings on my new Ubuntu installation.  For the internet to work, I need to have my DNS server set to 195.74.102.146, however, every time I change it, it reverts back to 192.168.1.1 (the IP address of my ADSL router) after a while.  This doesn't work as my router is not a DNS server!  Why does it keep losing the setting and is there any way of stopping it from overriding my changes?  I change the DNS server by going into the System menu then Networking then the DNS tab.

---

### Post by jayant on 2006-07-28
i am having similar problems. not exactly the same but similar. can you let me know what you've tried so far please? maybe it can help. also you can take a look at my thread to see if something helps. [http://www.ubuntuforums.org/showthread.php?t=224577](http://www.ubuntuforums.org/showthread.php?t=224577)

or maybe this will help
[http://www.ubuntuforums.org/showthread.php?t=224330](http://www.ubuntuforums.org/showthread.php?t=224330)

---

### Post by MaximB on 2006-07-28
actually I had the same problem too
and the good guys here managed to help me
so now I know (hopefully) how to help you too.

after configuring your networking (dns)
go to the terminal and type :
sudo chattr +i /etc/resolv.conf    
to make the file read-only

walla - problem solved !

---

### Post by jayant on 2006-07-28
thanks maxddark! i havent tried it yet as i found a different way to make sure my resolv.conf doesnt get over written.

garyreggae did this work for you? if it did i might give it a try as well.

---

### Post by GaryReggae on 2006-07-29
Yep - that worked a treat.  I set up the DNS settings as I wanted them then ran that command in the terminal and rebooted (which previously nuked my DNS settings).  When I went back in, the internet worked straight away!

Thanks for all your help. :)

---

### Post by MaximB on 2006-07-29
no problem.
welcome to our community

---

### Post by spartas on 2006-08-30
I have found the correct answer in preventing the DNS settings from resetting!  In /etc/dhcp3/dhclient.conf, include the following:

```

supersede domain-name "example.com";     # This is if you would like to 
                                         # use search domains, optional

supersede domain-name-servers 127.0.0.1  # Replace with your own domain name
                                         # servers

```

I'm not sure of the syntax for specifying multiple domain name servers, but I bring you answers.

---

