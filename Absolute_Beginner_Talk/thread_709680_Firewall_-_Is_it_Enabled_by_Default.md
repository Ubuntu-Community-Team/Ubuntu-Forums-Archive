---
title: "Firewall - Is it Enabled by Default?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by GregA on 2008-02-27
I've heard that Ubuntu doesn't have a firewall setup by default.   Is that true?  If so, what firewall gui is recommended (firestarter, guard dog, etc.)?   I've also heard Ubuntu may be coming out with a new firewall front-end, and maybe that will be enabled at install - - anyone have info on that?   thanks much!

---

### Post by Omnios on 2008-02-27
Linux uses ip tables and most stuff is sclosed by default. You can use Firestarter to modify this to allow connecctions.

---

### Post by forestpixie on 2008-02-27
> I've also heard Ubuntu may be coming out with a new firewall front-end

I did read something yesterday to that effect myself, a bit simpler to use than firestarter apparently - uncomplicated firewall :)
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by macogw on 2008-02-27
IPtables is running.  There is no GUI installed by default.  Firestarter is nice.  Everything is technically open, but since there are no services running on any ports, there is nothing receiving info sent at your computer.  It just gets ignored.

---

### Post by PeterJS on 2008-02-27
> **Omnios said:**
> Linux uses ip tables and most stuff is sclosed by default. You can use Firestarter to modify this to allow connecctions.

Everything is open by default, but nothing is listening, so the fact that nothing is closed is not important. My personal favorite analogy is: Is it important to have a guard dog guarding an empty hen house?

---

### Post by OrangeCrate on 2008-02-27
> **GregA said:**
> I've heard that Ubuntu doesn't have a firewall setup by default.   Is that true?  If so, what firewall gui is recommended (firestarter, guard dog, etc.)?   I've also heard Ubuntu may be coming out with a new firewall front-end, and maybe that will be enabled at install - - anyone have info on that?   thanks much!

Here's a good read on Ubuntu security by aysiu, who is active on these forums:

> By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. As a result, putting up a firewall would provide no more security than not putting one up. Remember that open ports provide services that hackers can connect to, and only if they can connect to these services can they be potentially abused and exploited.

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

For anyone new to Ubuntu, Psychocats is certainly one of the places to start learning about your new OS.

---

### Post by GregA on 2008-02-27
PeterJS,

I don't quite understand about "nothing" is listening.  What triggers listening, and by what?  Is it other networked (on external web) or inside a lan/wan?   I'm running a laptop on an open public network at my workplace.   Is there a way for me to secure my PC in addition to the firewall?  How would I enable WPA (which is a mystery to me as I am a newbie re wireless).  Is security only do-able if one is connecting via a router, or such?

As info, I also went to the Gibson Research Site and ran the "Shields Up" tests.  Looks all but one of my ports was closed or stealthed, but my PC did respond to pings.  

Any clarifications or tips appreciated!

Edit:  OrangeCrate, i just saw and read your post.  Thanks much, I'll check out the site you recommend.

---

### Post by macogw on 2008-02-27
If you enable a service, like an SSH server, it'll listen on a port for connections.  Ubuntu doesn't come with any installed or running.

---

### Post by kerry_s on 2008-02-27
check it here-> [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

