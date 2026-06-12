---
title: "Out of the box Cisco VPN client for 6.10?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by sson on 2007-02-22
Hi!

Is there a simple "one-click" install for Cisco VPN client on Ubuntu 6.10?

I've installed 6.10 twice in the last month, **real smooth** on my laptop, but on both occations I've had to back out since I need the classic VPN/RemoteDesktop into my work environment.

After some googling and spending way to much time on this single client install I'm right up against the wall, either I get VPN or I'm back in M$ land at home.

Any help for the ultimate Ubuntu noob? TIA!

---

### Post by geezerone on 2007-02-22
Haven't tried it or had the need but found these links which may help:

[http://ubuntuforums.org/showthread.php?t=347308&highlight=Cisco]("http://ubuntuforums.org/showthread.php?t=347308&highlight=Cisco")
[http://ubuntuforums.org/showthread.php?t=360569]("http://ubuntuforums.org/showthread.php?t=360569")

Let us know how you get on.

---

### Post by sson on 2007-02-23
Thank you **geezerone**, I have not seen those links before. Will take a look when I get home!

---

### Post by sson on 2007-02-23
I'm having no luck with this, with no time to spare (three more hours down the drain) and my patience (none left) it's Windows time for me. I'll take a look with someone who can do Linux-speak when I find him/her. If I find him/her.

Your first link points to something called a tar.gz - file, a compressed file with source, needs comepiling etc... yeah, sure, I'll do that, but only while you hold your breath! ;)

Second link was fine, sudo-bash-install-gedit-profile.conf etc, no problems there. But connect just dumps an error, no luck with that on google. Spent most of my time looking for that error. Added a few suggested parameters to the profile conf and ended up killing my network connection. Reboot into Windows.

Thanks for your help!

---

### Post by geezerone on 2007-02-23
Welcome to the wonderful world of FOSS!  :) 

Seriously, I saw that Synaptic has vpnc client which would be far easier. Ensure you have the repositries enabled if it isn't shown when you search in Synaptic.

I also saw a kde front end also when searching for vpnc in Synaptic.

I have installed both kvpnc and vpnc and very nice config/appearance just a shame that I don't use or know about vpnc :p

Let us know if you try this and how you get on.

---

### Post by sson on 2007-02-23
The kvpnc/vpnc I had already tried. Kvpnc looks very good but I got nowhere with it, I'm guessing because I never got vpnc to work in the first place.

The Synaptic, I had the repositries enabled, vpnc is what I always used for my Cisco client install in bash. Rather liked the simple config file, easy to grab/spot error messages from it. Understanding them is a diffrent matter to say the least!

I'll be sure to check Ubuntu out again, it's by far the best install I've seen for a Linux desktop and overall it just looks and feels right for me.

---

### Post by geezerone on 2007-02-23
> **sson said:**
> The kvpnc/vpnc I had already tried. Kvpnc looks very good but I got nowhere with it, I'm guessing because I never got vpnc to work in the first place.

The Synaptic, I had the repositries enabled, vpnc is what I always used for my Cisco client install in bash. Rather liked the simple config file, easy to grab/spot error messages from it. Understanding them is a diffrent matter to say the least!

It would seem that kvpnc uses vpnc just a GUI for it.

Why not post the errors on here or search if not done so and maybe someone could help out?

Glad you gave Ubuntu a try anyhow.

Regards :)

---

### Post by supirman on 2007-02-23
I use vpnc with a simple config file such as:

myLocation.conf
```
IPSec gateway pixvpn.ourdomain.com
IPSec ID TheVPNPassword
IPSec secret TheVPNSecret
Xauth username domain\username

```

and then:
```

sudo vpnc-connect myLocation.conf

```

Works like a charm.

---

### Post by sson on 2007-05-23
Just to close this thread, using "7.04 - the Feisty Fawn" the VPN now works right out of the box for me :D
A bug disconnecting the VPN has been fixed and is now in the feisty-proposed section in the software updates.
See [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413](https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413)
Thanks for your input all.

---

