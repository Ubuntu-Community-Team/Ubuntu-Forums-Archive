---
title: "home network"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Ndyanabo on 2007-10-22
Please help a noob think through a networking situation. 

Here's what I want to do: network and control an ubuntu music box remotely on my main ubuntu desktop. While I'm at it, I want to share files and a printer between a windoze laptop and the ubuntu desktop.

My internet connection is a wireless network provided by my apartment complex. The service assigns a dynamic IP. There are no ethernet jacks in my apartment.

My three computers:
main desktop: connects to internet through a wireless card, and hosts my music files. Running Gutsy.
music box: barebones desktop, headless, connected to my stereo. I want to connect this to the internet by sharing the main desktop's connection. The plan is to use an ethernet cable for the connection. Currently has Feisty, but plan to install Gutsy when I get it networked.
Windoze laptop. connects directly to net through a wireless card. Want to share files and printer with the main desktop either wired or wirelessly.

I also have a wireless router for the project.

FIRST QUESTIONS: Can I share the main desktop's internet connection with the music box with an ethernet connection via the router (ie, wire both desktops to the router)? Roughly how do I do this? Will the music box be assigned a static IP?


On to the music issue. The music files are on the main desktop, the music will actually be played on the music box. I need to be able to run the music program (quod libet, amarok, or other graphical program) remotely from the main desktop.

SECOND QUESTION: I need to serve the music files from the main desktop to the music box. Will I use samba for that? Mount the drives via SSF? A VPN?

THIRD QUESTION: How will I run the music program on the music box from the main desktop remotely? Can I do it with Samba? SSF will work, but is that the best way? 

So, at this stage, I have two desktops on a wired ethernet network. Finally, I want to network the windows laptop. 

FOURTH QUESTION: Given the above, any reason why it'd be complicated to share files and a printer with the laptop? Either over a wireless network, or wired through the router? The laptop is connected to the internet through it's wireless card, so that might make it unable to connect to a WLAN, unless it was receiving its net connection from the desktop.



In summary:
My main desktop would connect to the internet through its wireless card, and connect by cable to the home network via the wireless router.

The router would link wirelessly to the windows laptop, and wired to the music box and main desktop.

The music box would have a wired connection through the router. It would use this to receive music files, share an internet connection, and run programs controlled by the main desktop.

Any reason why that wouldn't work? Anything considerations? Headaches with dynamic IP addresses? How-tos to look at?

Will I create one home network, making all files available on it (stuff on laptop, stuff on desktop, and music) to the different computers, or will I make separate connections (laptop/main desktop and windows box/main desktop)?

Remember, I'm not necessarily looking for step-by-step directions here, I just want to be pointed in the right direction.

Thanks!

---

### Post by chuckyp on 2007-10-23
1) You should be able to share the internet connection with a router.  The cable coming from your Main Desktop would go in the WAN port of the router.  The cable coming from your router would come out of one of the LAN ports numbered and go to your music box.  You can assign it a static IP or use the router (depending on the hardware) to use DHCP.  I would also recomend mpd for music playing in yoru situation.  Its a nice music player daemon that has a many front ends.

2) You can use NFS or Samba doesn't really matter the choice is yours.  I would just right click on main desktops music folder and select share.  You could then mount it on the Music box so it appears local.

3) Another reason to use MPD do some searching on it and I believe this is what you are looking for.

4) I don't think its that difficult but it depends on your knowledge level. 

A big help through this process would be making sure atleast one of the machines can connect to the itnernet so you can get on IRC and ask for help there.  Or atleast post questions on the forums.  irc.freenode.net there is a #ubuntu channel for support with about 1200 people in there.

---

### Post by hugmenot on 2007-10-23
Performance-wise it would be best to connect both PCs to the LAN switch of the router, if it has one. Then if it is able to, the router would be a WLAN client for your apparments wifi. Both PCs would automatically have an internet route. Be aware that this is a switched network then. People could access your shares it they&#8217;re not secured. But spying on your PC-to-PC traffic would not be easily possible.
Having a high throughput streaming connection over wifi, that is also used by other people, is not such a good idea. It might work though.
Why don't you just store the music on the music PC? That is, use it as a file server, and media player. If you dont want to move the hard drive I would use an NFS export on your main box. Samba works too.
If you can, use the router as the central hub. With OpenWrt on it you could even client to the main wifi and additionally create your own private access point, with just one card in the router.


For playing, you might use MPD and a client on your main box. If MPD is not powerful enough for you, you can just as well run a decent player on the music box, but redirect the GUI over X11 forwarding.

ssh musicbox.lan -X quodlibet

might be such a line. If you register a public key for SSH on the music box you don&#8217;t even have to login, the player will just start and fell like it&#8217;s running locally.

---

### Post by Ndyanabo on 2007-10-23
Thanks for the feedback.

The MPD looks pretty good, and I don't see why it wouldn't work.

I can't put the music on the music box, because there isn't enough bays for the drives. It's a pretty old computer, too. I have a couple of hard drives full of music.

Will I be able to manage a large library like that with MPD?

> With OpenWrt on it you could even client to the main wifi and additionally create your own private access point, with just one card in the router.


I think I have OpenWrt on it, or maybe DDwrt. What is the advantage of doing it that way?

---

### Post by hugmenot on 2007-10-23
You'd have one uplink to the internet, and the router gives you a private network for your machines. You can use cable, or if you figure that out, also make a wireless access point.

The thing here is that the wireless card in the router is already occupied with being a station (client). Atheros and broadcom cards however can create new virtual APs so that you can associate your other machines to that (i.e., the card does two things simultaneously). 

apt. WLAN ----- &#8592;w. router&#8594; ------ (router's WLAN) ---- PC/laptop

---

