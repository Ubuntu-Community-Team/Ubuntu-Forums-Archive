---
title: "How do I disable firewall(s)"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-09-28
My Pan newsreader, as well as Frostwire, are having difficulties that I think I can attribute to my firewall. TIA.

---

### Post by Albi on 2006-09-28
do you have a router?

---

### Post by Johan! on 2006-09-28
Which firewall are you using?

And why would you want to disable the firewall?
If you use one, wouldn't it be better to configure it the right way?

---

### Post by ricardisimo on 2006-09-28
> **Albi said:**
> do you have a router?

I'm using a wireless connection from the nextdoor café, so the router is theirs.

---

### Post by ricardisimo on 2006-09-28
> **Johan! said:**
> Which firewall are you using?

And why would you want to disable the firewall?
If you use one, wouldn't it be better to configure it the right way?

I have no idea which firewall I'm using. I tried tinkering with *Firestarter*, which would claim that I had my firewall either On or Off, depending. But no matter what *Firestarter* claimed, both *Frostwire* and *Pan* thought differently. Neither will work - or work properly - until I can control/correct this issue. Thank for responding. Any ideas?

---

### Post by ricardisimo on 2006-09-29
> **ricardisimo said:**
> I have no idea which firewall I'm using. I tried tinkering with *Firestarter*, which would claim that I had my firewall either On or Off, depending. But no matter what *Firestarter* claimed, both *Frostwire* and *Pan* thought differently. Neither will work - or work properly - until I can control/correct this issue. Thank for responding. Any ideas?

I'm going to fine-tune the question and just ask how to best work my firewall so as to be able to use Pan. I'm going to forget Frostwire for the time being, as those Java issues are pretty obscene right now. TsIA.

---

### Post by po0f on 2006-09-29
ricardisimo,

You might be out of luck.  The cafe's router most likely has the ports that those programs run on blocked.  And since you most likely can't convince them to open them up ("Hey, my p2p program won't connect, can you open up port blah?" "No!"), tough luck.

---

### Post by orb9220 on 2006-09-29
Well first write down what ports that the program is trying to use.

Then go here and they will tell you how your computer appears on the internet, [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and will show which ports  are open,closed,or stealthed.

Ubuntu's firewall is called iptables and is installed by defualt. Firestarter is the gui front-end to iptaples and only needs to run when  you are going to make changes to iptables.

You need to open the ports for the program unless the coffee shop is blocking on purpose p2p type software.

I am not have the knowledge to help you further but doing a forum search  on firestarter to see how to modify iptables for letting the app have access.

---

### Post by ricardisimo on 2006-09-29
I did the next-best thing: absolutely nothing. There must have been a problem with the connection earlier, because today it's working fantastically. I just couldn't understand how Pan could get server, group and header information, but no bodies... doesn't make any sense. No idea what happened, but now it's all fine. Thanks for the input anyway.
By the way, I suspect that the issue with Frostwire is local, and not on the router. I can download very well from anyone who's not blocking "freeloaders" - like myself until I get the issue resolved. But that can wait until the java bugs are worked out.

---

### Post by pseudonym on 2006-09-29
For future reference, the firestarter [documentation]("http://www.fs-security.com/docs.php") at their website is very user friendly. :)

As far as frostwire is concerned, the best way to configure it is go to Tools>Options>Advanced>Firewall Config and note the number of the 'Listening Port' . Then in router config below this check 'Do Nothing' if you don't have a hardware router (the upnp option won't work in linux because you need root privileges to alter firewalls, and you should definitely NOT be running frostwire as root). If you do have a hardware router as well you will see that it tells you what to do in the same section.

Then in firestarter you need to open up the frostwire listening port so people can connect easily to your machine (the brick wall icon should disappear). If you are security conscious you will stealth the port again when you finish your p2p session. :)

---

