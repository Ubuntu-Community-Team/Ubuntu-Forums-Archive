---
title: "AIM no longer works in Pidgin or Gaim"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-07-05
I recently had AIM stop working for me via Gaim.  I read through the threads about the name change and went and installed Pidgin.  All other messenger services work fine except AIM.  I even went to AOL's website to test my login, it still works.  I get this message:  Could not connect to authentication server:
Connection refused

I've checked and re-checked my password and it is correct.  What could be the problem?

---

### Post by moredhel on 2007-07-05
have you tried with another client like kopete to check whether that works? The only other thing I can think of is that you might of changed some of the connection settings :\

---

### Post by bean77 on 2007-07-05
I'll try that-thank you!

---

### Post by bean77 on 2007-07-05
It's still not working although all other chats are.

---

### Post by moredhel on 2007-07-05
so you mean it won't connect in kopete either?

---

### Post by bean77 on 2007-07-05
Nope

---

### Post by jasonlfunk on 2007-07-05
Maybe a router/firewall/ISP is blocking it? Try doing a trace route to the AIM auth server. It should be listed in the Preferences of Pidgin.

---

### Post by moredhel on 2007-07-05
^ that would be a plan :)

Check that you have allowed it in firestarter (if used) and on your router ;)

---

### Post by bean77 on 2007-07-05
Sorry, I am not understanding what you mean.  If I go into the Kopete preferences, how do I check the settings?

---

### Post by moredhel on 2007-07-06
I think he means find out what the aol server is and what port it uses which you can then add on your allow list of your firewall/router.

---

### Post by bean77 on 2007-07-06
My server is login.oscar.aol.com and my port is 5190

---

### Post by moredhel on 2007-07-07
So now you need to allow port 5190 on your firewall and/or router

---

### Post by scxtt on 2007-07-07
i don't see why that would be, at least to connect - i don't forward 5190 from my router and AIM works fine (w/ kopete & pidgin) ...

---

### Post by moredhel on 2007-07-07
Neither do I, but his firewall or router might be being proactive to block everything, I don't know.

---

### Post by bluekage on 2007-08-29
I was having this problem as well, I just fixed it a minute ago actually. Just access your router settings, disable your firewall, and then save the settings. After you verifying that this fixed the problem, I reenable my firewall and AIM still works. Hope this helps you.

edit - wow...this has probably been fixed for over a month now, I should really start to pay attention to post dates...

---

### Post by bean77 on 2007-09-01
> **bluekage said:**
> I was having this problem as well, I just fixed it a minute ago actually. Just access your router settings, disable your firewall, and then save the settings. After you verifying that this fixed the problem, I reenable my firewall and AIM still works. Hope this helps you.

edit - wow...this has probably been fixed for over a month now, I should really start to pay attention to post dates...

Sorry, I am very new at this-how do I acccess my router settings?

---

### Post by mgmiller on 2007-09-01
In Firefox go to address 192.168.1.1 if it's a linksys and 192.168.0.1 if it's a netgear.
to log in, if you haven't changed it, in Linksys leave the user name blank and type admin as the password.  In netgear, user is admin or administrator and password is blank.

Once you're in the router, if it's Linksys, look in the advance tab and go to port forwarding and plug in the numbers.  If it's Netgear, I forget, you will haved to look around a bit.  Same deal for other brands of routers.  I'm not sure if you need to tell it tcp or udp, so unless you can google the answer to that question, if you select "both" it should work.

---

### Post by bean77 on 2007-09-02
> **mgmiller said:**
> In Firefox go to address 192.168.1.1 if it's a linksys and 192.168.0.1 if it's a netgear.
to log in, if you haven't changed it, in Linksys leave the user name blank and type admin as the password.  In netgear, user is admin or administrator and password is blank.

Once you're in the router, if it's Linksys, look in the advance tab and go to port forwarding and plug in the numbers.  If it's Netgear, I forget, you will haved to look around a bit.  Same deal for other brands of routers.  I'm not sure if you need to tell it tcp or udp, so unless you can google the answer to that question, if you select "both" it should work.

Thanks for the tip.  The password didn't work in Linksys but I havenever been anywhere where I would need to change it.  I have never logged into it.

---

