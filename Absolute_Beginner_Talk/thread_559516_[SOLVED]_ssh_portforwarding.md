---
title: "[SOLVED] ssh portforwarding"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by guymclaren on 2007-09-25
Can anyone help me understand how to configure port forwarding to allow sambar to be used over ssh? In essence I want my windows client to access sambar over the net. 

I am able to do everything from inside the router but am unsure how to test everything 

In fact can someone tell me what the come up with when they access [http://myharddrive.dnsalias.com/](http://myharddrive.dnsalias.com/)

When I do it, I get the routers control panel despite the webserver being set up on port forwarding.

how would I check wether ssh is actually working from outside

---

### Post by gautada on 2007-09-25
> **guymclaren said:**
> Can anyone help me understand how to configure port forwarding to allow sambar to be used over ssh? In essence I want my windows client to access sambar over the net.

I am not sure what sambar is but if you lookup the ssh parameters -L and -R for port forwarding you should be able to forward the sambar ports.

> **guymclaren said:**
> I am able to do everything from inside the router but am unsure how to test everything 

Connect to the router via the WAN ip address.

> **guymclaren said:**
> In fact can someone tell me what the come up with when they access [http://myharddrive.dnsalias.com/](http://myharddrive.dnsalias.com/)

It took me to a default ubuntu apache setup.

> **guymclaren said:**
> When I do it, I get the routers control panel despite the webserver being set up on port forwarding.

Not sure why.  Sometimes routers need to be restarted for setting to take effect.


how would I check wether ssh is actually working from outside[/QUOTE]

---

### Post by Dr Small on 2007-09-25
I get a blank directory listing when I visit the link you provided.
To enable Dynamic Port Forwarding in SSH, use the -D operative.

Example:
```
ssh user@host -D 1776
```

---

### Post by guymclaren on 2007-09-25
Thank you both. I don't get the apache page I get the router, so obviously things may be working and I am not getting the results i desire. Maybe because I am trying to go out and back in through the router?

If I set up an user account will someone test ssh for me please

---

### Post by Dr Small on 2007-09-25
Yes, i could test it.
Of couse, I am leaving in about half an hour, so if you could hurry...

---

### Post by guymclaren on 2007-09-25
Thank you have sent you the user details as a pm

---

### Post by guymclaren on 2007-09-25
Thank you Doc, Today you are my hero

---

### Post by Dr Small on 2007-09-25
No problem.
Please remember to mark the thread as "[SOLVED]" from the Thread Tools ;)

Dr Small

---

