---
title: "ubuntu internet security"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by g.hughes on 2007-04-17
Many thanks for replies to previous post.
I am still experimenting around with my ubunntu DVD distro but I have not intalled as yet.
I would be grateful for any advice concerning internet security in ubuntu; antivirus, firewall, antispyware, etc.
Oh, I understand a new version of ubuntu is due for release shortly. Should this have any bearing on my install from my DVD?

---

### Post by Gif on 2007-04-17
Hi,

I had similar concerns on this subject too  :) 
See this thread [http://ubuntuforums.org/showthread.php?t=404630](http://ubuntuforums.org/showthread.php?t=404630)

Hope it helps,

---

### Post by bwhite82 on 2007-04-17
Most of these things you speak of are not a problem on Linux. Almost all of that stuff is targeted at the masses (Windows users). Ubuntu's default security is plenty good enough, all ports are closed until needed by default, etc. The new release will not affect your installation (assuming it's an Edgy DVD), but you will have the option to upgrade to the newest release once  you're all setup and ready to go.

---

### Post by doctorj on 2007-04-17
> **Soldierboy said:**
> Most of these things you speak of are not a problem on Linux. Almost all of that stuff is targeted at the masses (Windows users). Ubuntu's default security is plenty good enough, all ports are closed until needed by default, etc. The new release will not affect your installation (assuming it's an Edgy DVD), but you will have the option to upgrade to the newest release once  you're all setup and ready to go.
Is a firewall actually needed?

I found this firewall -- FIRESTARTER -- which did nothing much, from what I could see. All that happened is it broke the network and I could not see the other 4 machines in the network.

So I stopped the firewall. 

Is it worth trying to make the firewall work with the network, or do I just forget it?

---

### Post by bwhite82 on 2007-04-17
In most instances, depending on what you are going to do on linux, you do not need to do anything with your firewall. Firestarter is just a front-end for IP_Tables in Ubuntu. Really, if you're not doing any serving or remoting, theres not anything you need to do. It just works.

---

### Post by floke on 2007-04-17
Firestarter stops several ports from responding to remote queries that otherwise report themselves as being closed. Apart from that, not a lot.

Try the link below with Firestarter on and off and you'll see the (small) difference.

[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)

---

### Post by doctorj on 2007-04-17
> **Steve.K said:**
> Firestarter stops several ports from responding to remote queries that otherwise report themselves as being closed. Apart from that, not a lot.

Try the link below with Firestarter on and off and you'll see the (small) difference.

[http://www.grc.com/x/ne.dll?rh1dkyd2](http://www.grc.com/x/ne.dll?rh1dkyd2)
One thing I must say is that Ubuntu people are very practical. Giving me a little test to do was a very practical demonstration. Thanks. And I will stop worrying about anti-virus, firewalls etc. What a great world to be in. Why would you stay in the Windows world?

---

### Post by dpar on 2007-04-17
Firestarter doesn't 'do' anything. It is just the GUI to manipulate the firewall that is already there (iptables).Turn it on or turn it off will make no difference unless you make changes with it to the iptables rules.

---

### Post by hyper_ch on 2007-04-17
And use for downloads only trusted ressources... either official or trusted repositories or official websites of certain products that are not in any repositories :)

That way you should be fine :)

---

### Post by airtonix on 2007-04-17
yep, there is a phrase lurking around this forum that has just appeared here ... it goes like this :

"in a world with-out gates and windows who needs firewalls ?"

or maybe it goes : 

"what need doth a penguin have of windows when it has neither walls, gates or even jobs?"

or for an extremely maybe it goes : 

"those who through stones shouldn't live in glass houses"

aero-"glass"-vista -> windows -> are parts of a house. that is surrounded by gates.

---

### Post by g.hughes on 2007-04-19
OK.   I take your point concerning antivirus. 

I  am not totally convinced about the firewall, or lack of it; unless the same argument is applied concerning Linux as a target. I mean a firewall should both outbound and inbound traffic.

But what about spyware when browsing? Should no antispyware be used or is antispyawre available?

---

### Post by Lucifiel on 2007-04-19
Internet security should not be too much of an issue, unless you: 

a) tend to click on random emails from strangers

b) install software from suspicious sites without a care

c) have users on the computer who're not too Internet-savvy and who tend to make beginner mistakes.

d) Some of the software you use has bugs or exploits which could lead to security problems. And you'd like temporary protection while the fixes are being worked on. 

For me, I do run ClamAV though, with KlamAV as the gui. This is because I receive plenty of emails and often, with viruses at times. But you don't have to run an AV: for me, sometimes I've the tendency to click on links by mistake when I'm sleepy or tired and thus, appreciate an AV telling me that "Wham! Virus detected! Caution: Don't let it run!" as opposed to sending in the disaster recovery team when my pc has descended into the pits of hell.

---

### Post by g.hughes on 2007-04-19
Just found this link 

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=371340&highlight=virus+spyware]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=371340&highlight=virus+spyware")

---

