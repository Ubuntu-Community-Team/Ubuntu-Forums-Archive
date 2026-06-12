---
title: "Guarddog + Ktorrent"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by ErwinC on 2008-04-08
I can't figure it out: how do I configure Guarddog  to work with torrents?
When I switch of Guarddog: Ktorrent is working: up and downloads are fast and ok.
When I switch on Guarddog: Ktorrent does not work anymore.

I searched the forum, I googled a lot but I didn't find anything that helped?
Anyone???

---

### Post by ibutho on 2008-04-08
You need to open some ports on the firewall for use with your torrent apps. On my system I use 6881, 63072 and 4444. You then need to configure ktorrent to use the ports that you opened.

---

### Post by Locutus_of_Borg on 2008-04-08
go to advanced tab under guarddog, set a new protocol, create a range of ports as TCP/UDP then configure ktorrent to use those ports, also set UDNP under ktorrent plugins.

this is from memory, but i think that is what i did when i had guarddog

---

### Post by ErwinC on 2008-04-09
I've tried about everything, made different protocols >> opened ports like described above. 
Uploading works fine, but no downloading. I'm becoming desperate.

---

### Post by liverpoolfc2 on 2008-04-10
Did you add a new Zone? I added and called it DMZ, used advanced tab and added ports.
Set DMZ for torrents, and the in the user defined checked the torrent ports.
Looks to be working fine for me, and i'm also behind a router.

New to the world of Linux, installed Guarddog last night as I didn't really like the other firewalls and Iptables is beyond me at the moment, just spent a few hours online reading about this, have to say was a bit of a nightmare to get going but i'm getting their.

Just a matter of setting router, client, guarddog to all see the ports I wanted to use.
Seems to drop now and then, but I'll figure that out soon enough, have spent a few days here reading, great site, and never really felt the need to make any posts as of yet as the answers are all here so far.

Good Luck.

[edit] Just realized I joined this site in July 2007. Linux scared me, but I have decided to give it another go,
and for some strange reason I understand it better, guess it's all that reading i've been doing.

---

### Post by ErwinC on 2008-04-10
For now, I installed Firestarter and switched off Guarddog. It seems everything is working now. 
To bad Firestarter is as configurable as Guarddog. For that reason I will give your methode a try....in a while...

I'll keep you informed. Thanks

---

### Post by liverpoolfc2 on 2008-04-11
Well, for some strange reason it just stopped working, could download without any problems.

Now I can't upload, oh well back to the drawing board.

[edit] Should add to this, rarely use torrents, use newsgroups for anything I need, newsgroups working fine, just this torrent thing is bugging me now.

---

### Post by hyper_ch on 2008-04-11
why install that anyway on your computer? Properly configuring the firewall on your router would be a lot simpler ;)

---

### Post by liverpoolfc2 on 2008-04-11
True, run DD-WRT on my router, just that I stumbled across guarddog, and it just began to annoy me that everything other than torrents would work, ftp,chat,,nntp. strange this is, it does work for a few hours, then just stops. 
Back to me router firewall.


> **hyper_ch said:**
> why install that anyway on your computer? Properly configuring the firewall on your router would be a lot simpler ;)

---

