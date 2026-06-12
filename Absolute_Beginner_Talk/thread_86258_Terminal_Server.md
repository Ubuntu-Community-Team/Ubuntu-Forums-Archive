---
title: "Terminal Server?"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by SunBurnt on 2005-11-04
I was told on the chat site that Ubuntu does a term. server setup like Knoppix.
The one on the Ubuntu menu is client only, for Win RDP I found out after much forum searching.

Does Unbuntu have a root over NFS or Samba setup (not LTSP thin client setup)?

I have powerful PCs that can do their own work, so the server isn't  loaded with  the effort like a thin client setup.

Do you call this setup a medium client, or a diskless thick client?

signed: confused & dissapointed...

---

### Post by Kyral on 2005-11-04
I think that this belongs in the Ubuntu Server Talk forum....

---

### Post by dare2dreamer on 2005-11-04
Dear Confused,
(And now I feel like Ann Landers...)

There are several ways you can accomplish what you are after. I'd suggest having a look at the following tools/projects:

VNC
FreeNX/NoMachine
LTSP

VNC is built into gnome (see preferences>remote desktop), NX is fairly trivial to set up and works amazingly well (I use it daily) and apparently Ubuntu got LTSP (linux terminal server project) support out of the box in breezy.

Hope this gives you some starting points for your research.

Happy Hacking,
dare2dreamer

---

### Post by chazzjazz on 2005-11-04
can i ask the difference terminal services and remote admin....they seem 2 sides  of the same coin..

I have used VNC on windows and you can access the server but i need to restriction to programs and folders and files.

Can it be done on ubuntu??? i need to allow a few pc onto the server: one PC might have access to firefox, others might be able to access OpenOffice etc...

can this be done quickly, efficiently and most importantly security for the current ubuntu releases??

---

### Post by SunBurnt on 2005-11-04
Sorry, you may be right about it being a server forum post, but it was so noob a Q that I thought to put it here.
So often we're thinking of a quick answer, & not about the post developing into a full blown informitive discussion.

Kyral:
The first link is to a post about console terminal usage (I think, I didn't read it all).
I'll try the IRC if no one can help here.

dare2dreamer:
VNC isn't a multi user setup as such (but it could be), & uses the servers cpu to do all the work.
LTSP uses the server for the work also, they say apps. can run on clients, but it's not the standard setup.

Root over NFS or on ramdisk runs apps. locally, this is what Knoppix Term. Server is.

Xwin does remote & local apps. on any machine.

FreeNX I'm not familiar with, I thought it was a cluster setup, could you explain what it is?
It seems it is a cluster load sharing setup, so the server doesn't carry the load, but for simple office, library, keosk, home workstation type use it seems more than's needed.
Could be great for video encoding work, if that can be done, like ClusterKnoppix, other than that I can't see that most apps. are all that demanding to need multi processing.

---

### Post by bluefrog on 2005-11-10
edubuntu or setup ltsp on top of ubuntu ( and on top of both you can setup samba-ldap) will get you what you want

james

---

### Post by dare2dreamer on 2005-12-20
You can find out what everything you need to know about NX by reading up at [www.nomachine.com](www.nomachine.com), but the short version is that it is a remote desktop tool that was designed from the ground up to handle high-latency connections and other less than stellar networking situations. It's tunnelled over ssh, allows disconnection from the remote session (ala terminal server, gnu screen,  or vnc) and there are clients around for just about every platform.

I've seen several thin-client distros start offering it as an option in addition to the usual remoted-X/VNC/etc. options.

It stacks up well against the aforementioned alternatives for a couple of reasons:

VNC is a brilliant idea, and one I used for years. Problem is that it starts falling down quickly if you need ANY security (it has absolutely none built in), or are running over a less than stellar link. VNC does its magic by essentially passing compressed images around. If you can imagine the less than wonderful side of passing around screenshots of your desktop on an open network is, from a security and speed standpoint, you begin to see the problem inherent in the system.

Xforwards not done over ssh have more or less the same problem. They require a lot of back and forth traffic and can easily be captured and replayed if someone sniffs your network a bit.

Now realize that the security side is really more relevant to my situation, where I'm working both on my local lan and administrating for a few people who log in remotely. This is where NX begins to shine. NX tunnels everything through ssh. Set up properly, it's safe as houses. As a bonus, it is optimized for crappy connections and low end hardware. You've also got the "clients for nearly every platform" angle covered like vnc does (and X might not, unless you consider a live cd a client. I do. :-)

To give you an idea of real-use viability, I'm currently running 2 NX concurrent sessions to my desktop in addition to the local login. One is via an aging laptop (pentium 133, 76 MB ram) over a 802.11b connection, and the other is via a commodity dsl line across town to an older desktop machine (pentium II, 256 MB ram - My GF at her office). Both run at near-local speeds (the laptop is a little slower, but the slower session is still faster than its own desktop!), are as secure as ssh (only thing a sniffer can find is that I loooooove port 22) and the remote sessions add no perceptible load to the local session back here at the house of penguin love.

From what I've read, modern pc hardware can actually handle dozens of simultaneous NX logins without degrading performance noticeably (on the hardware, no idea about the network saturation) and it's trivial to set up a kiosk-style livecd that provides you with an nxclient login screen. (I've done it, feel free to message me for details)

Unless you have a burning need to use an actual thin-client setup, I'd strongly consider taking your lesser machines and converting them into live-cd based nx terminals, for lack of a better term. It's simple enough to do, and even if you still boot them over the network, I'd wager the setup will still be faster than a LTSP-style implementation.

---

### Post by SunBurnt on 2005-12-24
I've known of NX for a while, looks to be security/speedup protocol just as dare2dreamer said.
I looked at the NoMachine site & I'm reading everything I can find on it, got the; how it works basic concepts.
Looks like a few requirements have to be met (of course), Xwin version, libs, etc.
I need to check the list on the NX web page against any target distro to see if it's compatable.
Other than that the distro would need a lot of upgrading to make it NX ready.
Seems to be the ideal solution, which is why it's making such a splash, just wish I had a clue as to setting it up.

Looks like Xandros has the jump on everyone else, as they've already integrated NX into it, making it the premere server/client OS, now I wonder if it'll LAN boot the client PCs.

---

