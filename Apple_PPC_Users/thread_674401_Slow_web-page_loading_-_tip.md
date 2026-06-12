---
title: "Slow web-page loading - tip"
date: 2008-01-21
forum: Apple PPC Users
---

### Post by stream303 on 2008-01-21
A friend of mine loaded Ubuntu on his ppc and had very slow web page loading times, and was thinking it was a ppc specific problem.  He's behind the typical home style dsl router running dhcp and things seem to fly on Windows or OSX, but when it came to Ubuntu, it was very slow.

It was a dns issue.  I've written a lot of messages over the years in the networking forums about controlling your primary and backup dns server addresses in /etc/resolv.conf, but save yourself a lot of pain!

Just place your primary and backup dns server addresses **inside your router's setup page!**

If you don't know them, don't make them up.  A good alternative is to use the OpenDNS addresses, 208.67.222.222 for primary and 208.67.220.220 for backup. (from [www.opendns.com](www.opendns.com)) Don't use untrusted dns server addresses just floating around.

While you are inside the router's setup page be SURE to change the default username and password.  If your router doesn't have any login security, I think it would be wise to look for another router that does.

I placed this here to save some searching time in the general networking forums, since my friend thought it was ppc specific.  6.06.1 is working for him now, and I'm browbeating him to upgrade. :)

---

### Post by Jose Catre-Vandis on 2008-01-21
Useful tip :)

Edit your title so it makes sense and is more searchable :)

---

### Post by stream303 on 2008-01-21
Thanks Jose!  I guess Sow web pages aren't too common. :)  PM'ed a moderator since vbulletin won't allow initial thread title changes.

The whole dns issue behind windows-centric router hardware used to drive me bananas - especially when trying to demo anything non-windows or osx.  At least we're all on a level playing field with dns issues out of the way....

---

### Post by stream303 on 2008-01-24
This might be really important for owners of very old networking hardware / routers etc which may not faithfully follow the ipv6 standard.  Turning it off ***globally*** and relying on the older IPV4 protocol may help.

The best guide I have seen on this is here:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Disabling IPV6 isn't really necessary for modern gear, but I do it anyway since I'm behind a home router and find no need to run it.

I basically follow the instructions above, but I do it without assuming you can bring up a graphical editor.
```
sudo nano -w /etc/modprobe.d/blacklist
```

Now just add
```
blacklist ipv6
```
to the end of the file.  Note that there is NO HYPHEN between blacklist and ipv6.  In Nano, CTRL-0 to write it, and CTRL-X to exit nano. Reboot.

To test if it is working after a reboot, I use:
```
lsmod | grep ipv6
```

If nothing shows up, you're done.

This works for me with both Feisty, and Gutsy. Afterwards, I go into the network settings, and delete all host entries that start with IP6.  DO NOT remove the older ipv4 addresses 127.0.0.1 and 127.0.1.1. Leave those intact.

---

