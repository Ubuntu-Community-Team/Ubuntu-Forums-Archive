---
title: "Mac Mini as a home server, router, and access point"
date: 2008-04-12
forum: Apple Intel Users
---

### Post by jfwiedmayer on 2008-04-12
**BACKGROUND**
I just picked up a vaio laptop with a 250 gb hard drive and have had a mac mini with 80 gb hd that i'm looking to do something creative with.  i'm gonna switch out the vaio's 250 gb hd (5400 RPM) for the mini's 80gb hd (7200RPM) and i was looking to do the following with the mini...

install (x)ubuntu or OSX and make it into a...
[LIST]media server - music, movies, photos, dvdripping, encoding (hooked up to a 42" via DVI to HDMI cord)
[LIST]
[*]wireless router/access point with the mini plugged directly to the cable modem
[/LIST]
[LIST]
[*]firewall for wireless
[/LIST]
[LIST]
[*]ssh, ftp, vnc, web server
[/LIST]
[B][LIST]
[*]...any other suggestions
[/LIST][/B]
[/LIST]

Other considerations are that i have and frequently use my xbox 360, iphone, and an ipod video.

Given what i want to do i was looking for some pros/cons before i start
[B][LIST]
[*]Which OS do you think would work better - mythbuntu/xubuntu/OSX
[*]are there any other services/server daemons that you think would be useful?  and what do they do?
[/LIST][/B]

thanks in advance for the feedback.

---

### Post by cyberdork33 on 2008-04-12
well if you are looking to make a full NAT capable router, you need a dhcp server, etc. You could also setup full RADIUS authentication for your WiFi.

personally, I think it is just easier to go buy a cheap router at the store, then just make the mini a media server

---

### Post by mrsteveman1 on 2008-04-13
I would generally agree that its better to just buy a router and let it handle the networking, they are cheap and this way your network keeps working even if the server (mini) needs to be rebooted or otherwise worked on. If you really want to use the mini as a wireless access point and router, you can, although I'm not quite sure if the mini will act as an access point, it may just go into ad-hoc mode, which technically would work but isn't what you want to do if you can avoid it.

OS X does come with the same daemons you would be using on linux, samba, apache, vnc server. So that stuff is almost identical to linux. The config panels in OS X for these services are a little easier to use than in Ubuntu but if you know what you are doing on the system, ubuntu would work just fine.

With regards to the media center stuff, if you intend on using the mini as a DVR or otherwise as a media center, you should probably stick with OS X and use EyeTV/Front Row etc. There are ways to do the same things in Linux but they aren't as mature or capable at the moment, and drivers are always an issue with the HDTV tuners if you intend to use one. I have an HDTV stick that uses the em2880-dvb driver (not included in kernel because of political f#@$% crap), it doesn't work all that well in linux both because of the driver and because the software isn't as mature as stuff like eyetv.

---

### Post by cyberdork33 on 2008-04-13
yep, I have actually been sticking with windows on my HTPC until there is some more maturity from the Linux front.

---

