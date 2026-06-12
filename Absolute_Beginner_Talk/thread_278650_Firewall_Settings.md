---
title: "Firewall Settings"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-16
Hello!

I recently thought about installing a firewall for Ubuntu (Just to be really careful, though I doubt it honestly needs it) and so I decided to install clamav. Well, I did that, and now whenever I open up frostwire (the p2p client) it says that I am behind a firewall and cannot connect. So I uninstalled clamav (as I said, I probably don't even need it) and restarted. However, frostwire still complains that I'm behind a firewall. Is there any way to figure out what I have installed (I don't remember, but I might have installed another antivirus software to try, and forgot to uninstall it)? How might I try to fix this?

Thanks!

---

### Post by Marsolin on 2006-10-16
Most Linux firewalls are just front ends for the built-in [iptables]("http://linuxappfinder.com/package/iptables") filrewall, so uninstalling clamav didn't change the firewall configuration. I'd check the [Frostwire]("http://linuxappfinder.com/package/frostwire") documentation to see what ports it uses and open those.

---

### Post by az on 2006-10-16
Clamav scans for windows viruses, and it's not a firewall.

Are you behind a router?

---

### Post by John.Michael.Kane on 2006-10-16
you could search in synaptic for clamav,and make all dependencies are removed.

Also clamav is not a firewall. it's an antivirus scanner. 

If you was looking to install a personal firewall theres one already installed called iptables.

The frontend for iptables is firestarter.

---

### Post by blendmaster on 2006-10-16
Okay, well the reason I ask is that that's the last thing I remember doing until frostwire started saying that. It didn't used to say that. 

Actually, I remember that I could use it just the other day, even after installing clamav. (And I realize it's not a firewall, but I said that as I wasn't thinking right, it's one of those days for me).

So what do you guys think I should do to figure this out? I don't think I even changed anything recently.

---

### Post by daou on 2006-10-16
In other words, installing Firestarter just makes it much easier to change your iptables settings (what connections, ips to allow etc).

---

### Post by Error_Msg on 2006-10-16
Speaking of which...
I set the inbound traffic policy and "allow connections from host" to allow connections for the IP of a second machine using the Samba service, but it is not allowing the connection. What I've been doing so far is stopping Firestarter, verify the connection, it works, and then restart the firewall and then it works fine.
I use xfce4, could this have something to do with it?
I haven't tested it on Gnome yet. I will do that now.

E_M

---

### Post by blendmaster on 2006-10-16
The problem is, is that I've had firestarter with this too (assuming firestarter is always automatically installed with ubuntu). But only recently has it decided to complain. But, it's these kinds of problems that I love!

---

### Post by xpod on 2006-10-16
I had frostwire installed with firestarter and it worked fine with the firewall up and running too.
It shows a little earth icon down the bottom right with a wall over it if the firewall is set up

That was dapper but ive not got round to it here in edgy......mmmmm

EDIT..seems they left it out of automatix2 unless im missing something

---

### Post by shanepardue on 2006-10-16
install firestarter for configuration of your iptables (your software firewall) and if you're behind a router, make sure to open the ports frostwire listens on through your router's config. that'll clear a pathway for you.

---

### Post by blendmaster on 2006-10-16
I don't think I have a router. Aren't those for multiple PC's to share a single connection. If so, then I don't have one.

I installed firestarter, and disabled the connection. Tried frostwire, and still nothing!

I don't know what to do. I tried changing the port to which frostwire listens, still doesn't work.

Any more ideas? By the way, thanks for the help so far!

---

### Post by blendmaster on 2006-10-16
Wow!

I figured it out, but it had nothing to do with any other software!

I accidently told it to use configure a Socks v5 proxy, which apparently made it quit.

Disabled this, and it works fine!

Sorry about all that!

Thanks!

---

### Post by shanepardue on 2006-10-16
no problem! that's awesome it worked out for you!!

---

### Post by az on 2006-10-17
> **blendmaster said:**
> 

Sorry about all that!

Thanks!

Don't be sorry!  The fact that you pointed out the problem will certainly help others who are having the same problem.

---

