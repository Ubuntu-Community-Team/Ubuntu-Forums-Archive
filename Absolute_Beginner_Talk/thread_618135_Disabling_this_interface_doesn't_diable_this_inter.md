---
title: "Disabling this interface doesn't diable this interface &gt;.&lt;"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2007-11-20
Well, my Internet up and died on me a few minutes ago.  I was going crazy trying to figure out how to bring it back up.  When going to my network settings (via KNetworkManager and System Settigns both--looks like the same interface), I noticed that it listed my eth0 (wired) connection as "Enabled" when i thought I had disabled it (since I have no wired connection at the moment).  Weird...  Okay, let's disable it again.  There.  Now let's try to load my Wireless connection...

Anyways, closed out of the KNetworkManager and tried to ping my router with no luck, so I went back to KNetworkManager just to see if I had everything right...

Wait a minute, I KNOW I just disabled you!  The eth0 was mysteriously re-enabled again.  Grr, this time I'll be sure to disable you.  I also changed my Gateway addresss (and changed it back again) so the "Apply" Button wouldn't be greyed out.  After hitting "Apply"... It re-enables itself in front of my eyes!  Argh. Disabled it again, closed.

I close out of KNetworkManager and try yet again to ping my wireless router with no luck.  Load KNM back up, and (of course) eth0 is sitting there smiling with a green checkmark, mocking my lack of Internet.  I disable it again, and try pinging again...  Success?

Wait, what?  Why?

Not that I'm complaining, but was it just that my wireless network card decided to take a little nap pn me or something?  I don't know, and I don't know if any of you will, but the point of this thread was about the re-enabling of the wired connection.

How can I get it to stay disabled?  What kind of configuration files do I need to read up on, and is there somewhere (hopefully here at the Ubuntu sites) that I can read them in nice friendly letters?



BTW, that's one suggestions I have for Ubuntu...  TO have nice, big friendly letters on the splash screen saying "DON'T PANIC".  ;)

---

### Post by Arthur Archnix on 2007-11-20
Sounds like you might want to look into blacklisting your eth1 interface, or whatever interface it might be. Not certain, but that's the direction I'd start searching in.

---

### Post by Sarteck on 2007-11-21
What is blacklisting, and how would I go about it?

---

### Post by Arthur Archnix on 2007-11-21
Sorry, I thought you were just looking for some search terms to get you started. I looked into it a bit further and I **think** the reason you can't disable the ethernet (aka. eth0, aka your wired connection) is because network manager has control of it.

Try adding eth0 to your /etc/networking/interfaces file, which might prevent network manager from gaining access to it. Then try disabling.

It probably looks something like this:
```
# The loopback network interface
auto lo
iface lo inet loopback

[B]# Add this:
eth0[/B]
```

---

### Post by Sarteck on 2007-11-21
Heh, I just was thinking in different terms what "blacklisting" was, so I wanted to know if I was wrong in my assumptions.

Thanks, I'll be trying this out later on, after I read up some on in, and post the results for anyone that's interested.

---

