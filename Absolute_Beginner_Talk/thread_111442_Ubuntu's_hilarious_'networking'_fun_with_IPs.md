---
title: "Ubuntu's hilarious 'networking': fun with IPs"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Fortigurn on 2006-01-02
I have had it up to my neck with the way Ubuntu fools around with my home network.

1)  My Ubuntu rig connects to my XP rig's LAN in order to share the ADSL link.  

2)  I have the Ubuntu ethernet connection set to DHCP.  

3)  This means, of course, that every time the Ubuntu rig is rebooted (not very often, but often enough to make this annoying), it gets a new IP address.

4)  This IP address then has to be entered in ZoneAlarm on the XP rig, in order for my Ubuntu rig to have ADSL access.

5)  Aha, you ask, so why not assign it a static IP address?

6)  Simple - if I do that, and enter that IP address in ZoneAlarm on the XP rig, absolutely nothing happens.  The Ubuntu rig doesn't even recognise that a network exists

7)  Tonight I went through the usual rigmarole of re-entering the new DHCP assigned IP address in ZoneAlarm, only this time it didn't work - my Ubuntu rig still doesn't connect to the XP rig's network.

I have spent the last half an hour Googling, reading Ubuntu FAQs, and generally fooling around with the network settings, and I have had enough.

Could someone please explain to me how I can get this to work consistently?  Thanks.

---

### Post by varunus on 2006-01-02
Sounds to me more like this is a firewall/XP issue than an Ubuntu issue...

Lets try static IPs for a minute.  You said that the Ubuntu machine does not recognize that a network exists.  What do you mean?  Is it unable to connect to websites?  What about local shares?  Is it a DNS issue (ie, can you browse to [http://72.14.203.104](http://72.14.203.104) but not [http://www.google.com)?](http://www.google.com)?)

It should be fixable even with your current setup...

Another option; can you hook the Ubuntu machine up to the ADSL line and share that connection with windows?  Ubuntu can do this pretty easily and through a GUI (though there are guides that show how to do it through the command line on these forums...).  Post back here if you want to do this, I can show you how through just a GUI.

---

### Post by stuporglue on 2006-01-02
> Another option; can you hook the Ubuntu machine up to the ADSL line and share that connection with windows? Ubuntu can do this pretty easily and through a GUI (though there are guides that show how to do it through the command line on these forums...). Post back here if you want to do this, I can show you how through just a GUI.

I'm interested in seeing this.

---

### Post by dixonstalbert on 2006-01-02
hi Fortigurn

I have my wireless ubuntu laptop networked with 3 windows computers that all run Zonealarm.

I entered a 'trusted zone' in Zonealarm by selecting

Zonealarm > Firewall >  [Add>>] > IP range > IP address (top box) 192.168.0.100  > IP address (2nd box) 192.168.0.105 > description > My Local LAN

my dlink router is set up to only assign local IP's in this range, so whatever IP it assigns to my laptop, it is in this range and ZoneAlarm lets it talk to my windows computers

I cannot remember exactly, but LAN IP's can only be between 192.168.0.0 and 192.168.0.999 and also 2 other ranges (?127.0.0 and something else)

maybe you could look at the IP's your ubuntu gets set to and and set up a trusted zone range like this in ZoneAlarm

You can test any changes you make to ZoneAlarm config to make sure they are safe by going to [www.grc.com](www.grc.com) and run the utilities in 'Shields Up' to test your firewall

hope this helps

---

### Post by diggs on 2006-01-02
buy a router maybe? I was wirelessly networking within 30 seconds of getting ubuntu going on my laptop to my XP/ubuntu box.

---

### Post by Herman on 2006-01-02
> buy a router maybe? I was wirelessly networking within 30 seconds of getting ubuntu going on my laptop to my XP/ubuntu box. I agree with diggs, if you can afford one, routers are great and they make life a whole lot easier and better. Mine also gives me the added protection of a 'hardware firewall', which is very good.
I have five computers all dual booting Windows and Ubuntu, and four can be plugged in to the router at a time. Two of these have Zonealarm in Windows, no problems.

The other three, (our best computers), have no firewalls because we don't need them anymore.
Ubuntu is our new firewall. We use Ubuntu for connecting to the internet now and don't have any more problems with spyware or viruses getting into Windows. Any spyware that may be already in Windows can't get out (dial home). Files that need to be moved to or from Windows and the internet go through Ubuntu. When I boot Windows, I physically unplug the internet wire.
You can do things that way too, regardless of whether you get a router or not. It saves a lot of time and money.

 Just use Ubuntu for the internet. Ubuntu is a lot safer than Windows for the internet.
Actually, I hardly use Windows for anything much at all anymore.   :smile: (Herman)

---

### Post by Lord Illidan on 2006-01-02
[quote=Herman]I agree with diggs, if you can afford one, routers are great and they make life a whole lot easier and better. Mine also gives me the added protection of a 'hardware firewall', which is very good.
I have five computers all dual booting Windows and Ubuntu, and four can be plugged in to the router at a time. Two of these have Zonealarm in Windows, no problems.

The other three, (our best computers), have no firewalls because we don't need them anymore.
Ubuntu is our new firewall. We use Ubuntu for connecting to the internet now and don't have any more problems with spyware or viruses getting into Windows. Any spyware that may be already in Windows can't get out (dial home). Files that need to be moved to or from Windows and the internet go through Ubuntu. When I boot Windows, I physically unplug the internet wire.
You can do things that way too, regardless of whether you get a router or not. It saves a lot of time and money.

 Just use Ubuntu for the internet. Ubuntu is a lot safer than Windows for the internet.
Actually, I hardly use Windows for anything much at all anymore.   :smile: (Herman)[/quote]

I agree all the way. A router is better, and you avoid probs.. My network at home uses one, and I love it...

---

### Post by diggs on 2006-01-02
I have a router at home, tommorow I can tell you what it is. It's a few years old, works great-not wireless. I'll sell it to you for $20us. Where do you live?

---

### Post by diggs on 2006-01-02
I have a router at home, tommorow I can tell you what it is. It's a few years old, works great-not wireless. I'll sell it to you for $20us. Where do you live?

---

### Post by r4ik on 2006-01-02
The idea putting a Windows machine behind the Ubuntu system never crossed my mind.
Man am i stupid.

---

### Post by Herman on 2006-01-02
Probably too far away to bother mailing an old router. They have improved a lot technologically in the last few years, I would imagine, just like everything else to do with computers. If you had an old one and it isn't satisfactory, try a newer one, they are great. I postponed buying a router fro a long time, but now that I have one I think they are the best invention since the wheel. :D (Herman).

---

### Post by Herman on 2006-01-02
> The idea putting a Windows machine behind the Ubuntu system never crossed my mind.
Man am i stupid. to 44ik, 
yes, it works great, but I should point out to you, just in case you don't already know, that  a virus that can kill Windows can be present in something you have downloaded in Ubuntu and lie harmless and dormant there. Ubuntu will be immune to it. Later, it can come to life when it is imported into Windows. Therefore, it is wise to use an open source virus scanner in Ubuntu, for example ClamAV, to scan those files before transferring them. 
Then, also use some kind of antivirus scanner in WIndows to scan the new files a second time, just to make sure. (Like getting a 'second opinion' from another doctor).
You can also get spyware in Windows from most software and games CDs too, it doesn't only come from the internet. Not allowing Windows to connect to the internet is the only real answer, so at least the spyware that's in there can't call home to report all your private business to its maker.
 Just making sure you are aware of all those things.   :D (Herman)

---

### Post by proventech on 2006-01-02
Internal IP addresses (LAN IPs) can be in the following ranges:

10.0.0.0-10.255.255.255
172.16.0.0-172.31.255.255
169.254.0.0-169.254.255.255
192.168.0.0-192.168.255.255

I would forget about the 169s.  Most of those would be for Autoconfiguration IP addresses (IPs that the OS assigns the ethernet adapter if no other connection is found).

127.0.0.1 is a Loop Back ip for testing the ethernet adapter.  Also, in Windows, the hosts file would point to this ip.

---

### Post by Fortigurn on 2006-01-02
[QUOTE=dixonstalbert]hi Fortigurn

I have my wireless ubuntu laptop networked with 3 windows computers that all run Zonealarm.

I entered a 'trusted zone' in Zonealarm by selecting

Zonealarm > Firewall >  [Add>>] > IP range > IP address (top box) 192.168.0.100  > IP address (2nd box) 192.168.0.105 > description > My Local LAN

my dlink router is set up to only assign local IP's in this range, so whatever IP it assigns to my laptop, it is in this range and ZoneAlarm lets it talk to my windows computers

I cannot remember exactly, but LAN IP's can only be between 192.168.0.0 and 192.168.0.999 and also 2 other ranges (?127.0.0 and something else)

maybe you could look at the IP's your ubuntu gets set to and and set up a trusted zone range like this in ZoneAlarm

You can test any changes you make to ZoneAlarm config to make sure they are safe by going to [www.grc.com](www.grc.com) and run the utilities in 'Shields Up' to test your firewall

hope this helps[/QUOTE]

That sounds like an excellent suggestion - simply assigning the entire range a a trusted zone.

---

### Post by Fortigurn on 2006-01-02
[QUOTE=diggs]buy a router maybe? I was wirelessly networking within 30 seconds of getting ubuntu going on my laptop to my XP/ubuntu box.[/QUOTE]

I have actually recently purchased a router with a built in firewall and other networking protection.  I am going to spend some time to see if I can set it up.

---

### Post by Fortigurn on 2006-01-02
[QUOTE=varunus]Sounds to me more like this is a firewall/XP issue than an Ubuntu issue...

Lets try static IPs for a minute.  You said that the Ubuntu machine does not recognize that a network exists.  What do you mean?  Is it unable to connect to websites?  What about local shares?  Is it a DNS issue (ie, can you browse to [http://72.14.203.104](http://72.14.203.104) but not [http://www.google.com)?](http://www.google.com)?)[/quote]

Unable to connect to websites, and no local sharing.

---

### Post by Fortigurn on 2006-01-02
[QUOTE=Herman]Ubuntu is our new firewall. We use Ubuntu for connecting to the internet now and don't have any more problems with spyware or viruses getting into Windows. Any spyware that may be already in Windows can't get out (dial home). Files that need to be moved to or from Windows and the internet go through Ubuntu. When I boot Windows, I physically unplug the internet wire.

You can do things that way too, regardless of whether you get a router or not. It saves a lot of time and money.

Just use Ubuntu for the internet. Ubuntu is a lot safer than Windows for the internet.

Actually, I hardly use Windows for anything much at all anymore.   :smile: (Herman)[/QUOTE]

This is where I really want to be.  I actually built an Ubuntu rig specifically with the intention of using it as the home server and firewall.

---

### Post by Fortigurn on 2006-01-02
[QUOTE=diggs]I have a router at home, tommorow I can tell you what it is. It's a few years old, works great-not wireless. I'll sell it to you for $20us. Where do you live?[/QUOTE]

Thanks, but I've bought a router, I just haven't installed it yet.  I live in Taiwan.  ;)

---

### Post by Fortigurn on 2006-01-02
Thanks for all the help guys, I'll report back when I have some time to spend on this.

---

### Post by r4ik on 2006-01-03
[QUOTE=Herman]to 44ik, 
yes, it works great, but I should point out to you, just in case you don't already know, that  a virus that can kill Windows can be present in something you have downloaded in Ubuntu and lie harmless and dormant there. Ubuntu will be immune to it. Later, it can come to life when it is imported into Windows. Therefore, it is wise to use an open source virus scanner in Ubuntu, for example ClamAV, to scan those files before transferring them. 
Then, also use some kind of antivirus scanner in WIndows to scan the new files a second time, just to make sure. (Like getting a 'second opinion' from another doctor).
You can also get spyware in Windows from most software and games CDs too, it doesn't only come from the internet. Not allowing Windows to connect to the internet is the only real answer, so at least the spyware that's in there can't call home to report all your private business to its maker.
 Just making sure you are aware of all those things.   :D (Herman)[/QUOTE]

Thanks for your advice i will take care :)

---

