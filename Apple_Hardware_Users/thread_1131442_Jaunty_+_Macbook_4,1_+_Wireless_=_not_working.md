---
title: "Jaunty + Macbook 4,1 + Wireless = not working"
date: 2009-04-20
forum: Apple Hardware Users
---

### Post by jjt288 on 2009-04-20
Hello,

I'm new to Ubuntu but experienced with unix. I tried installing the Jaunty RC on my Macbook 4,1 and I'm having issues using the wireless. It looks like a bug was reported, but there is no information there about a resolution and no updates recently. I was wondering if anyone here has found a workaround for this until it's fixed?

The problem is that Hardware Drivers reports that the "Broadcom STA wireless driver" is "activated but not currently in use", but nothing shows up in my wireless GUI and I cannot connect.

Bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343556](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343556)

I have tried following the troubleshooting on the ticket but with no luck. Anyone know a way to get this working? This is the only thing holding me back from switching from OS X to Ubuntu!

Thanks, jjt

---

### Post by cyberdork33 on 2009-04-20
make sure that the 'wl' module is loading ( lsmod will help you determine this).

Make sure that other wifi modules are not loading (such as b43).

Also, just in case, you can get to documentation for your Mac here:
[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by Claritux on 2009-04-21
Did you try to just disable and re-enable the drivers? Worked for me on my MacBook 4.1.

---

### Post by jjt288 on 2009-04-21
Yeah it looks like the mod "wl" was not enabled. I added it and restarted networking and it was good.

Thanks guys,
jjt

---

