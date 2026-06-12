---
title: "Remote Administration / Desktop"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by oni5115 on 2008-01-14
I'm helping out my aunt with her computer.  Windows was running really slowly and her comp was full.  So I saved her stuff, setup a dual boolt box for her and showed her a bit of  linux.  She wants to learn it so I'd like to help.  However, I do live a ways away and it's kinda hard to tell someone that knows nothing about computers how to navigate anything.  (What's a task bar? Mousy clicky thing?) You know...  So I'd like to set it up so that I can remote control her desktop and literally show her how to do things from home.  So if she has a question or runs into trouble she can call me and I can login to her system and show her how to do stuff.

I've never really setup anything like this for either windows or Linux, so I'm not even sure what to install to do it.  Nor am I sure how to make it as secure as possible - ideally, I'd only want her to accept connections from my machine mac or ip address to make sure nobody else can get in.  (Being on cable modem, my IP can change so I'm wondering if it can be done by mac, or if there is another way? (perhaps using a service to get a domain name? dynamic dns or some such?)

I'm interested in knowing what the best way to achieve access to a desktop that we can both see is, and how to make sure its secure.  I'd very much appreciate knowing the names of the programs I would need to use, and/or any tutorials or guides that are out there for them.

While her system is dual boot, I am really only worried about the linux portion at the moment, but information regarding both linux and windows XP is certainly welcome.

---

### Post by benanzo on 2008-01-14
You want VNC or RDP.  You can enable it in Ubuntu by going to **System -> Preferences -> Remote Desktop**.  You can set a password so it's a bit more secure, even though none of it is encrypted.  For much better security you can tunnel the vnc session over SSH, but that's a bit more involved.

I'm not aware of a way to restrict access to just your IP.  Using MAC address filtering is useless since MACs are only used on LANs or inside your ISP's network, not the internet in general.

---

### Post by hyper_ch on 2008-01-15
Also simple way would be to install on your friend's computer:   krfb

And on your:  krdc

krfb is a vnc server - very simple to configure
krdc is a vnc client - you just need to know the computer's IP and ports to connect.

Within a lan it's very simple, outside a lan you'll need for forward ports from the router to your friend's computer.

---

### Post by oni5115 on 2008-01-15
looks pretty good, searched google and found the desktop sharing handbook.
[http://docs.kde.org/stable/en/kdenetwork/krfb/index.html](http://docs.kde.org/stable/en/kdenetwork/krfb/index.html)

I noticed in all the examples it seems that the IP is a LAN IP.  Would it be smart enough to use a WAN IP?  We're both on comcast, which are dynamic IP's that generally change every 6 months or so.  I'm curious how to work around that, since I know they know nothing about IP addresses, let alone how to log into their router and find out their WAN IP address.

If I do this for multiple family members, should I instead look into reverse VNC?  So that if they have a problem they can call me, I can turn on the VNC server on my end, have them connect to me?  That way I only have to setup port forwarding and stuff on my router, and not on theirs.
 
Can you remote control through SSH?  (I've really only barely messed around with it on 2 computers I have LAN'ed here at home.)  I know I could run SSH -x to forward the x client, and was able to run stuff from one computer on another computer.  Not sure if I could actually use it like a VNC though.

---

### Post by hyper_ch on 2008-01-15
you could install on her computer a no-ip.com or dyndns.org client. Both are in the repos and you just need to sign-up. So their IP will be updated.

And of course, you need to forward the according port for vnc (same goes for SSH)

---

### Post by oni5115 on 2008-01-15
Thanks, going to to mess around with it on my laptop and desktop for a bit and see how I want to set it up.  That way, next time I am over there I can set it up for her.

---

