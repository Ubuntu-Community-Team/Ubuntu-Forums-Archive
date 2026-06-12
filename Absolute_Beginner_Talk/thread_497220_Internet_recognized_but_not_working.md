---
title: "Internet recognized but not working"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by ess117 on 2007-07-10
Hi all.  I'm back for more advice.

Recent install on a Dell Dimension 8200 of Feisty Fawn.  I'm using a WMP54G Linksys wireless ethernet card.  The card seems to be recognized by the initial drivers, and it correctly identifies my network, "Basketball", by name, so it must be talking to the router.  After putting in the password, the internet connection indicator shows  me as "Connection to Basketball" - but there's no access through Firefox or the Ubuntu update or program fetching software.  It lists signal strength at 80%-85%.

What's going on here, and are there any ways around it?

---

### Post by swisscow on 2007-07-10
Possibly (because this happens to me) DHCP has dropped. What I do to solve this is to go to the wireless configuration page (I type in 192.168.0.1 in a web browser- yours may be different), find the tab that says DHCP and select renew/connect. All seems well when it has connected.

I think there are some command line commands as well to do this but not so sure what they are.

---

### Post by Rocket2DMn on 2007-07-10
You may have to configure your computer's DNS to match that of the router's auto-detect DNS info for your ISP (or just look at another computer on your network).  I had this problem on a server computer of mine running Fedora Core 5.  But yes, definitely sounds like DNS to me - you can confirm by pinging google at 64.233.167.104 - if that goes through, its the DNS for sure.

---

### Post by techknowmama on 2007-07-10
> **Rocket2DMn said:**
> You may have to configure your computer's DNS to match that of the router's auto-detect DNS info for your ISP (or just look at another computer on your network).  I had this problem on a server computer of mine running Fedora Core 5.  But yes, definitely sounds like DNS to me - you can confirm by pinging google at 64.233.167.104 - if that goes through, its the DNS for sure.
mater of fact you can put the ip adress in the address bar of firefox if it a dns problem it should pull up the google page

---

### Post by scheuri on 2007-07-10
Either it is the DNS which is not setup or not transfered from your router to you correctly.
OR your routing...

It happend to me that cable connection (you know, RJ45) did work, wireless did not. As soon as I disabled the ethernet (simlpy done and can be simply reactivated again) it worked.
It may happend that, even if you have wirless connection, your computer takes eth0 (or whatever your cabled connection/interface is called) as default and tries to use it.....and that wont work.

But that is just a thought.

Greetings
scheuri

---

