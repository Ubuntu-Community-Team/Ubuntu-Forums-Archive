---
title: "Several Websites Won't Load"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-02-09
So I upgraded to Edgy a few days back, and I'm now just getting a lot of updates I've been meaning to get, but I've found that a LOT of the sites I frequent for this kind of stuff are not loading at all anymore, Just giving me timeouts. 

So, I was wondering if this was just me, or if there's a larger problem. And if it's just me, what can I do to fix it?

Some of the sites I've been unable to get to:

gnome-look.org (or any sites in that network)
beryl-project.org
malteo.homelinux.net
3v1n0.tuxfamily.org

And there's a few others I'm forgetting about.

---

### Post by RomeReactor on 2007-02-09
Hi. Perhaps disabling ipv6 will help; in Firefox write in the address bar **about:config** and press enter. search for **ipv6** and when **network.dns.disableIPv6** appears, toggle it to **true**. Close Firefox and open it again.

If that doesn't help, try disabling it all across the system: Open a terminal and write

```
sudo gedit /etc/modprobe.d/aliases
```

look for the line that reads **alias net-pf-10 ipv6** and change it to **alias net-pf-10 off**. Save and reboot.

---

### Post by sunexplodes on 2007-02-09
Gave it a shot, and no change, sadly. Thanks though.

---

### Post by r4ik on 2007-02-09
-

---

### Post by sunexplodes on 2007-02-09
Already is set to 8, turns out. Thanks anyway.

---

### Post by sunexplodes on 2007-02-09
Are there any settings in /etc/hosts or anything like that, that might be causing this?

---

### Post by sunexplodes on 2007-02-09
Anybody?

---

### Post by sunexplodes on 2007-02-10
This is still happening, I can't seem to get access to a pretty wide array of sites I use. Please help?

---

### Post by RomeReactor on 2007-02-10
Have you tried pinging to the sites?

```
ping -c 3 www.gnome-look.org
```

Also, what browser are you using?

---

### Post by sunexplodes on 2007-02-10
Yeah, I've tried pinging, it just times out (100% packet loss). I'm using firefox, but as I said, it's not exclusively a browser problem, as it's occuring when i try to access a number of repositories (including security.ubuntu.ca).

---

### Post by _simon_ on 2007-02-10
Do you use a router? Try restarting it.

Possibly a problem at your ISP's end and just a coincidence it occurred when you upgraded?

---

### Post by sunexplodes on 2007-02-10
Update: A friend of mine brought a windows laptop over tonight, and we connected it to the network, and it has the same problem, so it looks like there's something off about our ISP's DNS server. 

Thanks for the ideas anyway guys.

---

### Post by sunexplodes on 2007-02-10
> **_simon_ said:**
> Do you use a router? Try restarting it.

Possibly a problem at your ISP's end and just a coincidence it occurred when you upgraded?



Hah, yeah. Exactly what happened.

---

### Post by _simon_ on 2007-02-10
Drop them an email, they might not even be aware that there is a problem!

You might expect them to know but having worked for an ISP, usually the first they know of a problem is when customers call. Unfortunately some customers sit back and just wait for it to be fixed which is no good if they don't even know about it lol

---

### Post by sunexplodes on 2007-02-10
Yeah, I called them and told some dude about it. He didn't seem to know what I was talking about, but also said it is probably just temporary and to call back if it's still happening tomorrow.

Exciting stuff.

---

### Post by sharkey_pj on 2007-02-10
It could be a routing problem with your internet provider. Have you tried performing a trace route to the same IP's?

---

### Post by _simon_ on 2007-02-10
> **sunexplodes said:**
> Yeah, I called them and told some dude about it. He didn't seem to know what I was talking about, but also said it is probably just temporary and to call back if it's still happening tomorrow.

Exciting stuff.

I'm afraid you've been fobbed off by someone who can't be bothered to check with the technicians. :rolleyes:

---

