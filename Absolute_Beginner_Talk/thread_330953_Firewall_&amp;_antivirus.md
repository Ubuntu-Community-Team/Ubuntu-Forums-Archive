---
title: "Firewall &amp; antivirus"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by RHS on 2007-01-03
I am very new to ubuntu.  What if any firewall do I need?  I will be doing banking and paying bills online.  Also what kind of antivirus do I need and how do I install these things?  I feel so unintelligent right now!  Please help!
Thanks so much!

---

### Post by aysiu on 2007-01-03
Read this:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by meng on 2007-01-03
My answer is that you won't need either, unless you have some special setup, e.g. home networking with Windows machines.

---

### Post by Hendrixski on 2007-01-03
Welcome to Linux where we are yet to experience a successful virus.  This is not to say that nobody writes viruses for Linux: some of the largest servers in the world run Linux, if a Hacker could write a virus to crash those he would be God among nerds.  So they've tried many times, never successfully.  So ordinary people like you and I haven't caught any yet, and probably won't for a long time..

But it theoretically may happen some day, so it doesn't hurt to be prepared.  Feel free to try clamAV, F-Prot, Vexira, etc. etc.  Most of what they do is search for windows viruses that may be transmitted through your system.  So it's kind of a good-neighbor thing to do, even though you don't need to.

What you DO have to worry about is phishing!  If people send you an e-mail asking for personal information, or if you get popups asking you to give a password, etc.  Don't do it!  Identity theft is the most popular computer crime today, and though there are tools to help you avoid scams, there's no substitute for caution.

Firewalls are good against hackers, though i'll leave it to others to tell you why.

Enjoy Ubuntu, and be safe.

---

### Post by 1KuleKatDaddy on 2007-01-04
Hendrixi,

I would like to say that your reply has been one of the most intelligible and nicely written posts I've seen. Thanks for taking the time to be professional and help us minions.  

regards,

1Kulekatdaddy

:p

---

### Post by az on 2007-01-04
> **Hendrixski said:**
> 
Firewalls are good against hackers, though i'll leave it to others to tell you why.



A firewall is useless on a desktop machine.  It serves no purpose.  

Just don't run services you don't need.  If you wanted to run those services behind a firewall, you would need to open the ports anyway....

---

### Post by pseudonym on 2007-01-04
> **azz said:**
> A firewall is useless on a desktop machine.  It serves no purpose.  

Just don't run services you don't need.  If you wanted to run those services behind a firewall, you would need to open the ports anyway....
if you just stick with the default iptables all your ports are closed, thus still being 'visible'. If you install a firewall on top of that like Firestarter or [FireHOL]("http://firehol.sourceforge.net/") (my personal choice), you get a much easier to configure interface for those services you inevitably *will* want to run on a desktop (bittorrent, frostwire,....), and all your ports are 'stealthed' to boot.

And as for AV, it's not particularly nice to unwittingly email a linux-irrelevant windows virus to one of your windows-using friends/colleagues, when you had the opportunity to kill it by simply scanning your mail with, for example,  [F-Prot]("http://www.f-prot.com/support/helpfiles/unix/workstation/index.html") antivirus.

Bottom line - it certainly can't *hurt* to have a firewall and AV. It quite possibly *can* if you don't. Beats me why anyone would want to take the risk.

---

### Post by az on 2007-01-04
> **pseudonym said:**
> if you just stick with the default iptables all your ports are closed, thus still being 'visible'. If you install a firewall on top of that like Firestarter or [FireHOL]("http://firehol.sourceforge.net/") (my personal choice), you get a much easier to configure interface for those services you inevitably *will* want to run on a desktop (bittorrent, frostwire,....), and all your ports are 'stealthed' to boot..

There is no use to "stealthing" ports rather than closing them (drop instead of deny).  The minute you surf the net, someone will know you are there.  There is no way around that.  A firewall does not change that.


> **pseudonym said:**
> 
Bottom line - it certainly can't *hurt* to have a firewall and AV. It quite possibly *can* if you don't. Beats me why anyone would want to take the risk.

I don't want to waste my CPU cycles to compensate for the shortcomings of other operating systems and for the choices other people make.

I'm not doing anything bad.  I'm just not participating in the ridiculous situation - the virus dance- that does not involve me.

---

### Post by pseudonym on 2007-01-04
How many times has this debate gone on? :)

> **azz said:**
> There is no use to "stealthing" ports rather than closing them (drop instead of deny).  The minute you surf the net, someone will know you are there.  There is no way around that.  A firewall does not change that.
Well, OK, but you are still able to manipulate your ports much easier than you can with iptables (if you'd even bothered to learn iptables, when there are easier solutions available), in some cases with one or two mouse clicks.

> **azz said:**
> I don't want to waste my CPU cycles to compensate for the shortcomings of other operating systems and for the choices other people make.
Unless you're criminally low on CPU cycles, I don't think it matters much. And you are covering your own, er, backside as much as anything else.

> **azz said:**
> I'm not doing anything bad.  I'm just not participating in the ridiculous situation - the virus dance- that does not involve me.
Neither am I. But the once-a-week scan I've done for the past 2 years shows me how well my systems have avoided it.

---

