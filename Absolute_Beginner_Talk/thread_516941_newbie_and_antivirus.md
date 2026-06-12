---
title: "newbie and antivirus"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by trishapugh on 2007-08-03
new to ubuntu, have a laptop which only runs ubuntu, no windows.  I have nortons 360 can I run with ubuntu, if not then what antivirus, spyware and firewalls work best.  have only ever used windows so I am confused with what I can use with ubuntu.

Trisha

---

### Post by Ralob on 2007-08-03
no need for antivirus/spyware scanner. for firewall get firestarter or guarddog.

if you absolutely need a virus scanner get clamav

all of which are available from the repository.

---

### Post by az on 2007-08-03
An antivirus in an Ubuntu desktop is like a parachute on a bus.  You don't need it.  Ever.  The only time you may need one is if you are running a mail server and you want to offer that service to your clients.

A firewall on any desktop system is useless.  Again, you may need one if you are running a server.

Just keep up-to-date siwth software updates and avoid installing software from places other than the repositories and you wil be safe.

---

### Post by qamelian on 2007-08-03
> **az said:**
> An antivirus in an Ubuntu desktop is like a parachute on a bus.  You don't need it.  Ever.  The only time you may need one is if you are running a mail server and you want to offer that service to your clients.

An antivirus is still a good idea. While a file infected with a Windows virus might not be able to harm your Linux box, it could cause problems if you pass the file to someone who is still using Windows.

> A firewall on any desktop system is useless.  Again, you may need one if you are running a server.
Unless you're behind a decent, well-configured hardware firewall such as you'll find in most routers, a firewall on a desktop PC is a good idea and not useless at all. When I was connecting directly to the internet, before I bought a router, software firewalls protected my system against a variety of ills. 

Fortunately, Ubuntu is already provided with a firewall in the form of iptables.

---

### Post by az on 2007-08-04
> **qamelian said:**
> An antivirus is still a good idea. While a file infected with a Windows virus might not be able to harm your Linux box, it could cause problems if you pass the file to someone who is still using Windows.
.

And exactly how will this file get passed on to a windows box?  Ubuntu does not offer any additional ways to infect a windows box.

> **qamelian said:**
> 
Unless you're behind a decent, well-configured hardware firewall such as you'll find in most routers, a firewall on a desktop PC is a good idea and not useless at all. When I was connecting directly to the internet, before I bought a router, software firewalls protected my system against a variety of ills. 

Fortunately, Ubuntu is already provided with a firewall in the form of iptables.

Ubuntu doesn't listen to the network unless you install software that needs to.  That's what is relevant when people say it comes with a firewall.  The iptables rules set by default (without firestarter or any other firewall GUI) are not what is preventing your computer from talking to the net.

On windows, a software firewall is trivial to bypass and therefore only as secure as the underlying OS.  In Ubuntu, it's plain useless, if not a pain to manage when you actually need to use the network.  It serves no purpose.

---

### Post by lisati on 2007-08-04
> **az said:**
> And exactly how will this file get passed on to a windows box?.

Email is one way, by inadvertently forwarding something. A trojan is named after a story involving famous wooden horse and refers to something potentially malicious wrapped up to disguise its presence.

---

### Post by xpod on 2007-08-04
The only time av ever enters my mind now is when i see these threads:)

> An antivirus in an Ubuntu desktop is like a parachute on a bus. You don't need it. Ever. The only time you may need one is if you are running a mail server and you want to offer that service to your clients.

A firewall on any desktop system is useless. Again, you may need one if you are running a server.

Just keep up-to-date siwth software updates and avoid installing software from places other than the repositories and you wil be safe.

I know it and you know it but try telling that to people on my isp`s cable forum where they only support Windows.......WOW...:)

After being "advised" that everyone of us are prone to viruses,infection & spyware, especially when leaving things to assumption i only said "excuse me,i leave nothing to assumption and i know i`m safe thank you very much"

Boy what an onslaught i copped....LOL
Your not allowed to put people right  without being threatened with infraction though(not even politely).

I suppose the fact that the Cable Forum was just hacked a couple of days ago had them all on edge and a bit raw to the touch mind you:lolflag:

---

### Post by az on 2007-08-04
> **lisati said:**
> Email is one way, by inadvertently forwarding something. A trojan is named after a story involving famous wooden horse and refers to something potentially malicious wrapped up to disguise its presence.

Email is OS-agnostic.  So why is it more dangerous through email if it comes from an ubuntu box?  If windows needs a virus scanner, It should scan your emails without knowing from where they came.

---

### Post by euler_fan on 2007-08-05
I tend to agree that AV is not necessary on an Ubuntu box. I also agree that it is the owner's/user's responsibility for their own security practices.

However, I find it polite and a "professional courtesy" to other computer users of all stripes to scan my machine every few weeks. Not because I expect to find something (I never do) but because it allows me to offer an assurance that I am not acting as a carrier for a disease I am immune to.

I think the preceding is a perfectly valid reason to want to run periodic virus scans of a Linux box, and if a new user wants to run AV we should try to provide them not only with assurances that it is unnecessary for their own protection but also a few alternative reasons to still run it if they wish.

The firewall issue has been debated to death on these forums. I don't judge either way.

---

### Post by qamelian on 2007-08-05
> **az said:**
> And exactly how will this file get passed on to a windows box?  Ubuntu does not offer any additional ways to infect a windows box.

Gee, maybe you're familiar with the concept of forwarding email attachments? If someone sends you an infected attachment and you pass it on to someone else they can become infected even if you are safe. If you don't intend to contribute to the security in this chain, then you you shouldn't be forwarding attachments.



> Ubuntu doesn't listen to the network unless you install software that needs to.  That's what is relevant when people say it comes with a firewall.  The iptables rules set by default (without firestarter or any other firewall GUI) are not what is preventing your computer from talking to the net.

On windows, a software firewall is trivial to bypass and therefore only as secure as the underlying OS.  In Ubuntu, it's plain useless, if not a pain to manage when you actually need to use the network.  It serves no purpose.
Sorry, but you don't know what you're talking about. A software firewall is only trivial to bypass if you use a poor product and/or configure it improperly.

---

### Post by az on 2007-08-05
> **qamelian said:**
> Gee, maybe you're familiar with the concept of forwarding email attachments? If someone sends you an infected attachment and you pass it on to someone else they can become infected even if you are safe. If you don't intend to contribute to the security in this chain, then you you shouldn't be forwarding attachments.


Ubuntu does not offer any additional possibilities for a windows box to get infected.  The email attachment from Ubuntu (that you sent, not that some third-party made your copmuter send) should be scanned by the virus scanner on the windows box just like every other email.  Ubuntu will not fire off emails that will secretly be able to bypass your windows security.  Nor will it do so by itself.

> **qamelian said:**
> 
Sorry, but you don't know what you're talking about. A software firewall is only trivial to bypass if you use a poor product and/or configure it improperly.

Of course I know what I am talking about!

[http://www.securityfocus.com/infocus/1839](http://www.securityfocus.com/infocus/1839)
[http://www.securityfocus.com/infocus/1840](http://www.securityfocus.com/infocus/1840)

---

### Post by euler_fan on 2007-08-06
What I find interesting after having read this article is twofold:

1) The authors advocate firewalls as one layer in a multi-layered approach, not their abandonment. More specifically, coupled with a competent IDS and training for the admin responsible for it. This is the same approach widely advocated by SANS and others as well.
2) Existing firewalls are not designed to counter this kind of threat. They are designed to counter many other kinds of threats. These threats are ones which are designed to exploit weaknesses in existing security techniques. E.g. Hackers are smart enough to look for ways around existing security practices.

This leads me to make an observation and ask two (sets of) questions:

Given that in all fields of endevour historically (castles, computers, banks, etc) no single system has ever provided complete protection from all threats, it is unrealistic to make the argument that firewalls are worthless because they do not cover attacks X, Y, and Z but instead to consider their effectiveness at countering attacks A, B, and C along with the likelihood of attacks A, B, and C and the amount of damage they can cause.

Question 1: Are firewalls effective at blocking attacks they are designed to handle? What is the likelihood of that attack set? How much risk is removed by a firewall?

Question 2: How vulnerable is the Linux TCP/IP stack to a LSP vulnerability? How can this vulnerability be negated transparently to the user? Should we be implementing IDS (such as SNORT or OSSEC-HIDS) as a standard practice for Linux users much as AV and firewalls are for Windows users?

In short: First, don't throw the baby out with the bath water, unless there is no baby. Second, if the family cat can't kill the snake in the bedroom, don't fire the cat--buy a mongoose.

---

### Post by az on 2007-08-06
> **euler_fan said:**
> 
1) The authors advocate firewalls as one layer in a multi-layered approach, not their abandonment. More specifically, coupled with a competent IDS and training for the admin responsible for it. This is the same approach widely advocated by SANS and others as well.

What the authors describe is in the context of a sysadmin running a network.  Of course a firewall is useful there.   A firewall is a useful tool if you are running a server.  I maintain that a firewall on a desktop system is useless.

> **euler_fan said:**
> 

Question 1: Are firewalls effective at blocking attacks they are designed to handle? What is the likelihood of that attack set? How much risk is removed by a firewall?

A packet filter firewall filters packets according to a set of rules.  It can do that just fine.  An applications-based firewall is useless, since you cannot guarantee that all applications are going through it (example:  using another networking protocol or piggy-backing a process that is allowed to go through).  So I doubt that applications-based firewalls can ever be trusted.

So, do filter firewalls ward off attacks?  Well, if the attacker cannot talk to the process that is listening for it, then yes.  Can the attacker talk to the listener through other ports, using other protocols?  I guess so.  What is the likelihood of something like that finding itself into the Ubuntu repos?  A lot smaller than in a proprietary OS. 

For that matter, what's the likelihood of something listening to the network covertly in the software found in the Ubuntu archives?  

> **euler_fan said:**
> 
Should we be implementing IDS (such as SNORT or OSSEC-HIDS) as a standard practice for Linux users much as AV and firewalls are for Windows users?


I think that will be a test of how scalable to free-libre open source process is.  Right now, the assumption is that the code that is in the repos is sufficiently audited by peers.  If this is every sufficiently put into doubt, I'm sure we will eventuall see some sort of enhanced security mechanism put in by default.

---

### Post by euler_fan on 2007-08-06
> **az said:**
> What the authors describe is in the context of a sysadmin running a network.  Of course a firewall is useful there.   A firewall is a useful tool if you are running a server.  I maintain that a firewall on a desktop system is useless.


And reading the articles again carefully, their scenario (especially the Trojan) is also not likely against the desktop set up to block all inbound requests since their approach requires piggybacking on an existing stream of requests being processed. Simply rejecting all inbound requests means the Trojan would never see its instructions. There may well be other ways to mess with the application layer, but I'm starting to wonder how that would happen without the Trojan first making a new connection which it would need to hide (via a rootkit or some such) which basically throws us into the realm of either (a) your firewall will see the new outbound and if you are halfway aware of your outbound connects you'll put two and two together and shut it down or (2) you're so violated you're probably into re-install territory anyway.

> 
A packet filter firewall filters packets according to a set of rules.  It can do that just fine.  An applications-based firewall is useless, since you cannot guarantee that all applications are going through it (example:  using another networking protocol or piggy-backing a process that is allowed to go through).  So I doubt that applications-based firewalls can ever be trusted.


I'm wondering why this can't be guaranteed. I agree there are some larger issues with monitoring all processes and their Internet access permissions, but at the same time to what extent are we starting to mix the roles of a competent IPS and a firewall?

I might simply be ignorant, but I fail to see how, especially in the Linux world, this can't be designed around. As a rule I don't trust any single measure or layer anyway :)

> 
So, do filter firewalls ward off attacks?  Well, if the attacker cannot talk to the process that is listening for it, then yes.  Can the attacker talk to the listener through other ports, using other protocols?  I guess so.  What is the likelihood of something like that finding itself into the Ubuntu repos?  A lot smaller than in a proprietary OS. 

For that matter, what's the likelihood of something listening to the network covertly in the software found in the Ubuntu archives?  


Based on my own reading about IPTables you can set rules for all processes on all ports. Not sure how to get around that kind of coverage. A simple "drop all inbound silently" rule pretty much blocks all avenues.

No matter how unlikely something is, I still try to live by the idea that focused paranoia is the better part of security.

> 
I think that will be a test of how scalable to free-libre open source process is.  Right now, the assumption is that the code that is in the repos is sufficiently audited by peers.  If this is every sufficiently put into doubt, I'm sure we will eventuall see some sort of enhanced security mechanism put in by default.

Indeed.

---

### Post by az on 2007-08-07
> **euler_fan said:**
> And reading the articles again carefully, their scenario (especially the Trojan) is also not likely against the desktop set up to block all inbound requests since their approach requires piggybacking on an existing stream of requests being processed. Simply rejecting all inbound requests means the Trojan would never see its instructions. There may well be other ways to mess with the application layer, but I'm starting to wonder how that would happen without the Trojan first making a new connection which it would need to hide (via a rootkit or some such) which basically throws us into the realm of either (a) your firewall will see the new outbound and if you are halfway aware of your outbound connects you'll put two and two together and shut it down or (2) you're so violated you're probably into re-install territory anyway.

Well, in a proprietary OS, you don't know.  And in a free open-source OS you have a pretty good feeling that something couldn't communicate covertly.  Sure that's a compelling reason to have a firewall appliance between your windows desktop and the rest of the world, but less so for an Ubuntu desktop when you are reasonably sure it's not listening to anything.

For me, it's a simple and compelling reason to not use windows.

> **euler_fan said:**
> 
I'm wondering why this can't be guaranteed. I agree there are some larger issues with monitoring all processes and their Internet access permissions, but at the same time to what extent are we starting to mix the roles of a competent IPS and a firewall?

I might simply be ignorant, but I fail to see how, especially in the Linux world, this can't be designed around. As a rule I don't trust any single measure or layer anyway :)



The same reason that would make it a whole lot more possible on a free and open source platform is the reason why it wouldn't really be needed.  You run a firewall to make sure that nothing is spying on you.  You know your firewall is doing it's job because you trust your OS.  If you just trust your OS (i.e. nothing is listening to the network that you don't expect there to be) then you don't need a firewall to confirm that.

If you invented an applications-based firewall appliance, I'm sure I could find a reason not to trust that, either.  I'm not being funny.

> **euler_fan said:**
> 
Based on my own reading about IPTables you can set rules for all processes on all ports. Not sure how to get around that kind of coverage. A simple "drop all inbound silently" rule pretty much blocks all avenues..

I never said it didn't work, I said it was not needed (useless, actually)

> **euler_fan said:**
> 
No matter how unlikely something is, I still try to live by the idea that focused paranoia is the better part of security.


I don't trust windows and therefore I don't trust any software firewall running on it.  I have no reason yet, to not trust Ubuntu.  In the context of making the user's experience an easy and productive one, not having a firewall is my first choice.

---

### Post by euler_fan on 2007-08-09
> **az said:**
> Well, in a proprietary OS, you don't know.  *And in a free open-source OS you have a pretty good feeling that something couldn't communicate covertly.*  Sure that's a compelling reason to have a firewall appliance between your windows desktop and the rest of the world, but *less so for an Ubuntu desktop when you are reasonably sure it's not listening to anything.* (Emphasis Added)

For me, it's a simple and compelling reason to not use windows.


When I see a new set of vulnerabilities getting patched every month (usually a few of which are remote code execution with some level of privilege), I have to ask how sure can we really be nothing can listen or do something else we don't want it to do. I agree, far more confident than in the windows world, but enough to trust yet not verify?

> 
*The same reason that would make it a whole lot more possible on a free and open source platform is the reason why it wouldn't really be needed.*  You run a firewall to make sure that nothing is spying on you.  You know your firewall is doing it's job because you trust your OS.  *If you just trust your OS (i.e. nothing is listening to the network that you don't expect there to be) then you don't need a firewall to confirm that.* (Emphasis added)

If you invented an applications-based firewall appliance, I'm sure I could find a reason not to trust that, either.  I'm not being funny.

I never said it didn't work, I said it was not needed (useless, actually)

I don't trust windows and therefore I don't trust any software firewall running on it.  I have no reason yet, to not trust Ubuntu.  In the context of making the user's experience an easy and productive one, not having a firewall is my first choice. 

If you mean that F/OSS is sufficiently inherently secure (at least for the foreseeable future), I have to ask by what metric? I again cite the regular set of security updates. If you mean "so secure relative to windows", then again, by what metric? How can we really know unless we check?

If I ever invented an applications-based firewall I would still run a packet based one (stateful if possible and appropriate). I would not want you to completely trust it, but to use if for what it could give you with an understanding of its strengths and weaknesses. I completely agree that it is dishonest to say that any tool or set of tools is a complete security solution.

It's not that I trust or don't trust Ubuntu or any other system or system of systems or piece of software, it's that I prefer to "trust but verify". Ronald Reagan may have had his other faults, but the observation is still an astute one in a security setting.

One person's ease of use it another's intolerable annoyance. I won't comment.

---

### Post by dpar on 2007-08-09
I'm not a hacker or cracker or whatever, but I do know some very good ones. When asked about software firewalls, they just laugh. They said it won't delay them at all, just one more step.
They use Linux boxes.More secure.....lol

---

### Post by euler_fan on 2007-08-09
> **dpar said:**
> I'm not a hacker or cracker or whatever, but I do know some very good ones. When asked about software firewalls, they just laugh. They said it won't delay them at all, just one more step.
They use Linux boxes.More secure.....lol

I don't expect much besides disconnecting from the Internet to stop an attacker who is both motivated and expert at their work. To paraphrase Sun tzu: Against those truly sophisticated at attack it is always difficult (impossible?) to defend.

I'd be interested to hear their response about what percentage of attackers are good enough to break through a properly firewalled machine (and what that means) versus one without said firewalls. I'd also be interested to hear what *they* would do to secure a machine against attack, especially a laptop.

I don't ever expect to be completely safe. I simply try to manage risk as effectively as possible.

---

