---
title: "how do I Disable the firewall"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by grimsanta on 2006-11-02
One last question before i hit the sack.  I finally got java to install, and so frostfire loads now, but it just sits at "starting connection" so i can't get anywhere.

I have a feeling it's the firewall, as it says there's one up, but i can't for the life of me figure out how to turn it off?

How do I turn off the firewall

---

### Post by Polygon on 2006-11-02
its not the firewall as the built in firewall (iptables) on default basically closes all the incoming ports, but i think that most programs can access the internet fine, at least it was for me for all of my programs (songbird, gaim, azureus, iceweasel, thunderbird, etc etc)

it might be your internet, your isp might be blocking the ports needed for frostwire (maybe lol) or your router. Your router does have a firewall type thing, you could try checking in that.

---

### Post by _lynX on 2006-11-02
I've never had a problem with Frostwire connecting until the past few days, in which I haven't been able to connect at all. I think it may be a Frostwire issue. This is a relief to hear though, as I thought it was just me.

---

### Post by Voxxi on 2006-11-04
I was having the exact same problem, but I have it working now.

I looked at [this]("http://www.ubuntuforums.org/showthread.php?t=278134&highlight=frostwire") thread and found this:
```
sudo dpkg-reconfigure dash
```

Apparently Dash in the new CLI in Ubuntu/Kubuntu 6.10 (Edgy). So I made bash the default, and now it suddenly works. Bit odd.

I'm running Edgy, so I don't think this would be applicable in other versions. Hope this helps someone. ;)

---

