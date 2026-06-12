---
title: "[SOLVED] Do I need a firewall?  College network questions."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by likegiraffes on 2007-07-31
So, I've been using Ubuntu no problem for about two months now, and its great.  No more Windows!  =)

But I'm leaving for college in three weeks, and I was wondering if running my computer on a college network is any different.  I'm going to SUNY Buffalo, and they require an anitivirus for Macs and Windows machines to even be able to connect to the network.  The tech guy I talked to said there was no need for that if I'm using linux.  He also said "there are ways to make it more secure".  I don't know if that means I actually /have/ to make it more secure to protect my computer.  Any ideas?

Also, we got a rather fire and brimstone lecture about how the college monitors our computer transactions - the lady greatly exaggerated everything she said, but she did pretty much say that they can trace anything we do on our computers without getting there hands on our machines, just through the network connection.

I don't like that.  Um, how possible is that?  Is there any way to protect my privacy?  Specifically, dowloads-of-questionable-legality, what porn I watch, etc.  Can some administration person really monitor everything I do on the internet without my knowledge?  Ugh.  >.<

I'm talking about a modem/cable connection, not a wireless connection, just for the record.

---

### Post by Rocket2DMn on 2007-07-31
You do not need a firewall, Ubuntu uses iptables to restrict programs' network access.

Colleges can monitor your network usage.  This only tends to be a problem if you do a lot of transferring which tends to through up flags when they see how much bandwidth you're using.  So yes, they can tell what you're doing by looking at the packets on the network.
In general, you'll be OK, but as far as illegal downloading and sharing goes, the best option is to just not do it.  However, that advice can be tough to follow, so just don't bring attention to yourself by being a bandwidth whore, seeding torrents, or continuously torrenting.

---

### Post by likegiraffes on 2007-07-31
That's what I thought.

If I only download torrents at home (not on the college network connection), will they be able to see past activity or anything like that?  Would they ever bother?  =P

I feel silly even asking, but this lady basically made it sound like the first time I turned on my computer, she'd remote-access my desktop and her face would pop up saying 'Boo!'. xD

---

### Post by ne0h on 2007-07-31
As said you don't need any firewall. But if u still need one I'll recommend you 'firestarter'. Get info from here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall")

---

### Post by WarholsGhost on 2007-07-31
don't use limewire and don't seed excessively

if you are worried about being invisible online check out Tor and Privoxy

Have Fun! Don't get caught and move out of the dorms asap.

---

### Post by Lakefall on 2007-07-31
> **Rocket2DMn said:**
> You do not need a firewall, Ubuntu uses iptables to restrict programs' network access.

As far as I know there are absolutely no restrictions by default. On the other hand there shouldn't be any network services running either, so no open ports by default. But that only applies until you install something which opens some ports.

---

### Post by Rocket2DMn on 2007-07-31
> **likegiraffes said:**
> If I only download torrents at home (not on the college network connection), will they be able to see past activity or anything like that?  Would they ever bother?  =P

They cannot track past activity, they can't scan your HD, or even really access your computer without hacking it.  They can only monitor what is on their network, which means network traffic like uploads and downloads.  They can pinpoint IP source and destination.  The biggest problems come from peer-to-peer programs, most HTTP traffic is probably safe, so download your pr0n from the web if you must.

---

### Post by Ek0nomik on 2007-07-31
> **likegiraffes said:**
> That's what I thought.

If I only download torrents at home (not on the college network connection), will they be able to see past activity or anything like that?  Would they ever bother?  =P

I feel silly even asking, but this lady basically made it sound like the first time I turned on my computer, she'd remote-access my desktop and her face would pop up saying 'Boo!'. xD

The minute you turn on your computer, nobody at the University will be able to see files on your computer (ex:  past downloads).  It would be illegal, as they have no reason to see what files on your computer, as you haven't done anything wrong.

As previously said, the best way to avoid getting caught is to simply not do it.  One of my roomates last year got hit by the RIAA for $3,000 for illegal filesharing, but he was using Limewire.

The University can, however, see what you are downloading.  Even though they can do that doesn't mean they will make use of it though.  The battle of where Universities draw the line is underway right now.  Do they hide students privacy or do they do as the entertainment industry wishes?  If you have a stance on the matter, I'd suggest you become politically involved.  I am.  :)

---

### Post by likegiraffes on 2007-07-31
That's what I thought.  Thanks.  =)

---

### Post by likegiraffes on 2007-07-31
> **Ek0nomik said:**
> 
The University can, however, see what you are downloading.  Even though they can do that doesn't mean they will make use of it though.  The battle of where Universities draw the line is underway right now.  Do they hide students privacy or do they do as the entertainment industry wishes?  If you have a stance on the matter, I'd suggest you become politically involved.  I am.  :)

Any suggestions as to how to become politically involved?  I feel very strongly about my right to privacy.  =)

---

### Post by soupwell on 2007-08-20
More people getting politically involved is definitely the best long term solution.  A university should treat its students as adults, and provide unfettered internet access.  What students choose to do with that access is between them and their content providers.  If some party feels that their rights are infringed by a student, that is between them and the student.  It is not a university's place to intercede in a dispute, just because one of the parties happens to be a student.

In the meantime, the solutions suggested above (tor and privoxy) will let you surf as you please, without fear of your university spying on you.  You do pay some price in slower connectivity, but if it means avoiding fines and intrusion into your life, it's probably worth it.

---

### Post by bodhi.zazen on 2007-08-20
> **soupwell said:**
> More people getting politically involved is definitely the best long term solution.  A university should treat its students as adults, and provide unfettered internet access.  What students choose to do with that access is between them and their content providers.  If some party feels that their rights are infringed by a student, that is between them and the student.  It is not a university's place to intercede in a dispute, just because one of the parties happens to be a student.

In the meantime, the solutions suggested above (tor and privoxy) will let you surf as you please, without fear of your university spying on you.  You do pay some price in slower connectivity, but if it means avoiding fines and intrusion into your life, it's probably worth it.

I agree 150 % 

I am not an expert, but I wonder if the problem is the University is actually liable for activity of the students. Obviously if this is the case, the University would need to take action to protect itself from such a liability.

---

### Post by siraf on 2007-08-20
My roomate is a lawyer, I'll ask him for you guys about some of the legal issues.
I can tell you that you need to start learning how to use gpg and pgp ASAP. Also, use a friggin proxy if you're torrenting, or wine a uTorrent and use their encryption. I did that last year and the IT thought all my traffic was http. FYI, because I'm paranoid, I don't touch any questionable downloads: warez, music, etc. I download a lot of linux distros (including ubuntu :) ) and the uploading on my torrents is what can get me phone calls.

Good luck with your surfing, more info to come.

---

