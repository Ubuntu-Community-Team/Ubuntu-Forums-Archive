---
title: "Need help configuring Firestarter to work with aMule"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Westerberg on 2006-07-19
I want Firestarter's outgoing policy to be restrictive by default, whitelist traffic.  So I click that option and add rules to allow aMule to pass through at its default ports -- 4662 TCP and 4672 UDP.  But then I look at the terminal and see the following errors repeated:
> WARNING! Server UDP-Socket discarded packet due to errors (2) while sending.
WARNING! Client UDP-Socket discarded packet due to errors (2) while sending.

Also, say I select a file to with 50 sources.  I'll only be able to get into queue for about 10 of them.  If I blacklist outgoing traffic,  I'm able to get into nearly all of the queues.
Obviously I'm doing something wrong.  Can someone tell me what I need to do?

---

### Post by reneMx on 2008-03-06
It's been a long time since you posted this issue and surely you've came up with a solution but I'm posting just in case someone is having a similar problem.
I'm using GuardDog and it comes with all the internet services blocked by default. I enabled DNS, Http, Https,Ftp and the Edonkey2000 protocols, but when running amule I got the same error:

WARNING! Server UDP-Socket discarded packet due to errors (2) while sending.
WARNING! Client UDP-Socket discarded packet due to errors (2) while sending.

and wasn't able to connect to any server, after several tests (enabling and disabling protocols)  I figured out that we have to enable NIS "Network Information Service" in order to get rid of those errors. 
After enabling it I'm getting a low ID, but without problem to establish connection with the servers.Now it's just a matter of opening ports.
Greetings from México!!:KS

---

