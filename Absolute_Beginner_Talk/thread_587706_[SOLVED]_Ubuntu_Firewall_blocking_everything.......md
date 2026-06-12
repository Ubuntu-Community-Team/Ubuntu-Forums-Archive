---
title: "[SOLVED] Ubuntu Firewall blocking everything......"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-10-23
my ubuntu firewall is blocking everything in sight :confused:

---

### Post by shad0w_walker on 2007-10-23
What firewall exactly? It comes with iptables as default but i don't recall a single post of anyone having any problems with the defaults.

---

### Post by sayuki288 on 2007-10-23
i can forward ports in my router but ubuntu is blocking the ports and i can't have fast downloads <_<

---

### Post by shad0w_walker on 2007-10-23
Well I have never needed to open up any ports on my Ubuntu installs to get torrent clients working (I assume this is to do with torrents)

A. Are you sure the ports are forwarded to the right computer
B. Have you double checked that those ports are actually open and available from the net?

---

### Post by sayuki288 on 2007-10-23
yeah i have no problem forwarding ports in my router

can i use anything to change the settings in the default firewall?

---

### Post by shad0w_walker on 2007-10-23
You can install firestarter from the repos and that will let you setup the firewall.

---

### Post by sayuki288 on 2007-10-23
any site that can teach me to use firestarter?

---

### Post by shad0w_walker on 2007-10-23
[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by ark on 2007-10-23
i have the same problem, i cant download torrent, they dont connect me to anyone, the problem is just with my torrent client (using azureus)  but everything else works fine (xchat,pidgin, firefox, etc) .

and is not the torrent, i tried the same torrent on windows and it worked.

anyway, if you find a solution to this pliz let me know.

---

### Post by lepenguin on 2007-10-28
Hi !

I just migrate from another distro to ubuntu, and I have exactly the same problem.

It's not a problem with my ADSL router, It works with other distros, it works with Windows, and I checked it. It's not a problem of torrent client, I tested several clients and it's the same result : firewalled, no connections.

I have set up firestarter but there are no rules, it seems iptables is setup to allow all by default.

It's good news if ubuntu team tweaked Ubuntu's network settings to improve security, but I would like to change this configuration to enable this...

Thanks for your help !

Edit : I just remember that gutsy includes apparmor, perhaps this is the source of this problem, but apparmor_status doesn't show anything when azureus is launched.

---

