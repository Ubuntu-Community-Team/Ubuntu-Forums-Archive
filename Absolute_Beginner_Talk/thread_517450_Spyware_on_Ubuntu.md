---
title: "Spyware on Ubuntu?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Number_6 on 2007-08-04
I've just switched from Windows XP to Ubuntu (not sure why... I guess I was bored :)). Even when I was using XP, a lot of my software was free/open source. Since I had no idea if anything I was installing would put spyware on my system, or viruses, etc, I had a few things I did to make sure my system was clean. I would run Spybot, RootkitRevealer, Avast, and check the list of running processes to make sure that I recognized all of them. I also had a firewall (Comodo) set up to warn me whenever new software tried to connect to the internet. 

I'm never going to be content with just what is in the repositories for software. What can I do on Ubuntu to assure myself that my system hasn't been comprimised by something I've downloaded? Is what I did to check Windows acceptable for Linux (and if so, how do I perform the equivalent actions (except checking processes, I know that already)?). Is there anything else I can/should be doing?

Thanks

---

### Post by aysiu on 2007-08-04
Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by yogo on 2007-08-04
I think a better title for your thread would be "What can I do to protect Ubuntu from spyware."


The way yours reads, it implies that spyware is in the distribution.

Reading your thread I know that is not what you meant, just google spyware apps for Ubuntu.

---

### Post by Number_6 on 2007-08-04
> **aysiu said:**
> Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Thank you, that helped a lot.

> **yogo said:**
> I think a better title for your thread would be "What can I do to protect Ubuntu from spyware."

The way yours reads, it implies that spyware is in the distribution.

Reading your thread I know that is not what you meant, just google spyware apps for Ubuntu.

Thanks, I've changed the subject. I didn't mean to use my original title, I just forgot to change it by the time I finished writing my post. 

A couple more questions: Are all of the running processes listed in the System Monitor, or is it possible for some to be hidden? Also, is there a way to set up IPTables to warn when a program is making an outgoing connection and ask me to allow it, or do I have to allow programs ahead of time?

Thanks

---

### Post by euler_fan on 2007-08-04
> **Number_6 said:**
> [Is] there a way to set up IPTables to warn when a program is making an outgoing connection and ask me to allow it, or do I have to allow programs ahead of time?

Thanks

My first suggestion is to relax a little on this issue. Between Linux in general being far less targeted than Windows and the F/OSS community's distaste for software that 
"phones home" or does anything else without permission (my impression) there is far less need for the kind of heavy duty monitoring you had in set up in Windows unless you are running your own server.

Not sure about an interactive way to do this . . . (at least I haven't seen any) You can always simply set it up with a restrictive outbound policy and a white list of outbound connections. Not sure what a restrictive outbound policy would buy you though, given the above. Unless you or the machine in question has a pretty limited and well defined set of connections to make, any white list will take forever to set up. For instance, (in the server example) if it will only ever connect to the Ubuntu and ClamAV update servers plus a few other specific things. Bear in mind, once someone gets root privileges, the only smart option is to pull the plug and start over. You can't trust a compromised machine. 

If you're worried about something you don't want making an outbound connection making one (and in a position to monitor your traffic), Firestarter lets you monitor all your outbound connections. So can Conky with a properly configured .conkyrc file. There are plenty of examples in the different Conky-related threads. Then simply blacklist the ones you don't like. This is much easier than white listing and would give you both flexibility and control over your machine. I would go with Conky since it does not run as a root process the way Firestarter does, and so should be at least marginally safer for ongoing monitoring. Also, you can do things under this setup like locking the firewall before you go to bed, things like that. Then even if something tries to connect it can't. You can also read your logs.

IMHO yes you should use a firewall on top of the default "no ports open" Ubuntu setup and yes, scan regularly with ClamAV, rkhunter, and chkrootkit. I prefer the daily 0200 cron-job approach, but to each their own. :) But except for a firewall and being well patched, there isn't much you can do that isn't a basically reactive measure and (at this point and probably for the next 5-10 years) worth the effort.

---

### Post by moiecoute on 2007-09-01
> **Number_6 said:**
> Thank you, that helped a lot.

Also, is there a way to set up IPTables to warn when a program is making an outgoing connection and ask me to allow it, or do I have to allow programs ahead of time?

Thanks

I'd also like to know about this. I have come across from Windows and I love this approach nice and simple. Perhaps IPTABLES just can't do it in which case if anyone could recommend another firewall which could ?

---

### Post by Perfect Storm on 2007-09-01
> **moiecoute said:**
> I'd also like to know about this. I have come across from Windows and I love this approach nice and simple. Perhaps IPTABLES just can't do it in which case if anyone could recommend another firewall which could ?

You could install a nice gui for it.

```
sudo aptitude install firestarter
```

---

### Post by Kobalt on 2007-09-01
You can also read [this sticky]("http://ubuntuforums.org/showthread.php?t=510812") in the Server & Security section of the forums.

---

### Post by moiecoute on 2007-09-01
> **Artificial Intelligence said:**
> You could install a nice gui for it.

```
sudo aptitude install firestarter
```

Thanks for that. I have had a look at Firestarter and I can see how I can limit what traffic goes out by whitelisting ports. But how do you whitelist an application ?

By this I mean if I allow port 80 for browsing how do I know that some trojan inadvertantly installed onto the computer by my kids isn't using port 80 to communicate out or something to that effect.

Coming across from Windows, whether it be a Symantec or MS Onecare it would tell you what program was trying to get out and on what port. You then had the choice to allow it or deny it. I guess I am looking for that same functionality............ based on the example or for the reasoning I give in the above paragraph.

Thanks all your comments are much appreciated.

---

### Post by Perfect Storm on 2007-09-01
It wouldn't be a problem as you have to give "permission" which and what to run (that's the linux way). 

A better explaination is given by the dude above (the link) how linux works.

---

