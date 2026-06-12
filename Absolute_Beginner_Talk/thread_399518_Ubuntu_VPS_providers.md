---
title: "Ubuntu VPS providers"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by sidefx on 2007-04-02
I wonder if anyone has had any experience with tektonic as a VPS provider? They offer Ubuntu as an option, but I'm wondering if anybody has had anything to do with them.

I'm looking for a good VPS provider and am looking at tektonic and linode at the moment. Linode looks a bit better, and I've come across a few community recommendations, but tektonic is a fair bit cheaper.

Or... can anybody recommend any other VPS providers?

---

### Post by sylvaticus on 2007-04-07
I was with them using a Debian Sarge, but at that time they didn't have space for new application and I was in need of growing my VPS, so I moved to vpsland.com.

Both no problems (but I have only low traffic sites.. )

---

### Post by sylvaticus on 2007-04-07
..to be precise I was with unixshell, that is their branch using Xen.. tektonic instead use the more classic "virtuozzo".. (PS with same resources Xen is better, as they can not oversell RAM)

---

### Post by elanthis on 2007-04-08
I'm using Tektonic for my server and it's working out fairly well.  Use Dapper and don't try to upgrade to Edgy on their service, though, as I've never gotten that to work in my tests - quote possibly because Edgy requires a newer kernel and with Virtuozzo you're stuck with the hosts' kernel, which is 2.6.9.

It's a good service.  The only thing to watch out for is disk speed.  Disk access on Tektonic's servers is SLOW, so keep that in mind.  Some server apps are disk intensive and aren't a good match for Tektonic's service.  In some cases you might just need to do some special optimization to your server configs, such as setting maildir_copy_with_hardlinks in Dovecot, which really sped things up for me on IMAP.

Web site hosting seems to be pretty quick.  If you host forums, use one that requires MySQL.  A lot of people claim that the smaller file-based forums are faster, but that's at least not the case on Tektonic's servers, as MySQL's data caching is far quicker given the slow disk access.

Only other problem I can point out with Tektonic is that my mail server can't send through Hotmail.  I'm using the exact same config I had on my original server where things worked, and I have the reverse DNS setup, but Hotmail just silently drops all messages sent to it from that server, and also the server of my friend who is also hosted at Tektonic.

---

### Post by sidefx on 2007-04-11
Wow, thanks for the replies chaps. Now I have another one to choose from.  vpsland actually looks really good too.  I'm seriously considering that one now.


What is the general consensus on the virtualisation environment. Would most people think something along the lines of:

UML < OpenVZ < Xen  ?

---

### Post by larrybrazos on 2007-04-11
i'm also shopping for a vps, any suggestions on virtualisation environment would be helpful.  thanks

---

### Post by sidefx on 2007-04-12
Well, after a bit of research I decided to just go with Linode, for the following reasons:

1) There seemed to be a lot of horror stories on webhosting talk about the others I was looking at. tektonic, vpsland, vpslink.  And not all that many good stories. Conversely I could barely find any complaints about linode and a number of positive reports.

2) While they run things on UML, which seems to give worse performance than Xen, they are beta testing Xen and it looks like they will offer it at some point. My initial, admittedly very shallow, investigations into UML vs Xen vs Virtuozzo seemed to indicate that UML allowed you to do more stuff than the others. Like run different kernels, etc.  I'm probably wrong there though as I know very little about virtualisation.

3) They seem to specialize in Linux VPSs, while most of the others I was looking at offer windows VPSs and servers as well, plus dedicated servers, etc,etc,etc.  While Linode seems to specialise in pure Linux VPSs.    Call me crazy but I'd prefer there not to be the chance of them sharing techs across platforms or something like that...  Plus I'd prefer to support a Linux only operation. :)

I dunno, at the end of the day it was just a gut feeling, based mainly on the positive things I've heard about them that made me choose them.

They seem good in my 1 day of use so far. Account was activated within an hour or so, and I've had no problems at all yet. :guitar:

---

### Post by sidefx on 2007-04-12
Ah, they also allow IRC servers on your Linode. Most of the other budget ones I was looking at deny it...  I doubt I'll ever need to run an IRC server, but it's nice to know I can if I want to.

---

### Post by Warpnow on 2007-06-18
I'm probably about to sign up with byteshack.com

---

### Post by vpsville on 2007-12-05
I am of course, completely biased, but we provide Ubuntu VPS's with an uptime SLA.

---

