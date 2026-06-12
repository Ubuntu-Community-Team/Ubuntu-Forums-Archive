---
title: "Still no internet or repositories"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-06-04
I just installed a new router but the same problem persists.  I can get Google but I can get little else.  I cannot get yahoo and I cannot even get ubuntuforums.org.  I have to boot into WinXP to make my posts on this forum. Only about 5% of the web pages come up.  Somebody out there must know the solution to this problem.  I can't get the repositories either.

---

### Post by Pragmatist on 2007-06-05
Does the internet work without the router? (i.e. have you tried just plugging the modem into the Linux box?)

What is the Make and Model of the router?  Sometimes it is necessary to configure a firewall that is built-in to the router.  Usually, there are instructions as to how to configure the router via your browser.

---

### Post by WhiteSphinx on 2007-06-05
The router is a modem/router combo.  What I had before was just a modem and it worked the same way even when connected directly to the box.  I got Google, but little of anything else.

---

### Post by Pragmatist on 2007-06-05
> **Pragmatist said:**
> **[SIZE=3]...What is the Make and Model of the router?[/SIZE]**...

You didn't answer my other question.

---

### Post by Seisen on 2007-06-05
There are some know problems with people getting certain modem/router combo's to work.

---

### Post by WhiteSphinx on 2007-06-05
I did answer the question. The fact is that connected directly to the computer without a router yeilds the same result. NO INTERNET!!!!!

---

### Post by Pragmatist on 2007-06-05
> **WhiteSphinx said:**
> I did answer the question. The fact is that connected directly to the computer without a router yeilds the same result. NO INTERNET!!!!!

Please answer the following question if you want help:

**What is the Make and Model of the Modem/Router?**

---

### Post by WhiteSphinx on 2007-06-05
I am currently using a 2WIRE 2700HG-b.  I was previously using an Actiontec GT701-WG DSL modem. Both of these devices work perfectly with WinXP.

---

### Post by WhiteSphinx on 2007-06-06
Changeing window scaling does not work.  Does anyone have any other ideas??

---

### Post by WhiteSphinx on 2007-10-28
Okay this is too cool.  Problem solved.  This should work for anyone with an A33G PC Chips Motherboard or for anyone with an SiS190/191 ethernet.

First do this:

```
export EDITOR=gedit && sudo visudo
```

This will bring up the sudoers file.

Replace the following line (because of a bug)

> Defaults !lecture,tty_tickets,!fqdn

with:

> #Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

Add this line to the end of the sudoers file:

> username ALL=NOPASSWD: /sbin/ifconfig
Be sure to replace "username" with your own username.

Then open System>Preference>Sessions

Click Add

_N_ame > Configure LAN
_C_ommand > sudo ifconfig eth0 mtu 1492

Now you will be able to access the internet with you SiS190 Ethernet after you restart.

---

