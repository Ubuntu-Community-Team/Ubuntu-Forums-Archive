---
title: "I broke the internet with guarddog how do I fix?"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-24
Everything was working, and I clicked on the firewall guard dog I did not know what to click on so, I just clicked apply.  

I then rebooted and now I have no internet connection.

I am obviously, sending this from a different computer.

How do I fix it, I used firestarter in the past and it did its thing and dissapeared I then ran nexuss security scan on it and my machine was safe.  I kind of would like to revert the guard dog changes and use firestarter.  Unless guard dog is better, and I can get a rudimentary explanation on how to work it.  

If nothing else I would like to have internet access back please.

Thanks

---

### Post by The Cog on 2008-01-24
You can do 
```
sudo iptables -L
```
to see if there are any rules currently active. If there are, you can use 
**sudo iptables -F**
to clear them and disable all firewalling (until you reboot). Doing this will show if it's just the firewall rules that are blocking your internet access.

If that doesn't fix things then there is something other than a firewall making your internet not work. Let us know if this is the case.

Assuming you have proved that it is the firewall that's the problem:
The main thing is that you must enable the internte services you want to use. I found this guide: [http://www.tuxmagazine.com/system/files/Guarddog.pdf](http://www.tuxmagazine.com/system/files/Guarddog.pdf)
You must select the Internet zone, and tick the DNS protocol. This allows you to use name services on the internet and connect to things by name. You should also tick HTTP and HTTPS to allow your browser to access web services on the Internet. Allowing ICMP echo requests out might be useful, to allow you to ping things.

Hope this helps.

Oh, if you decide to remove guarddog, I think its configuration file that gets loaded on boot is /etc/rc.firewall. You may need to remove that too, but I think choosing to **completely** remove guarddog in synaptic should remotve that file too.

---

### Post by ThrobbingBrain66 on 2008-01-24
Guarddog is just a front-end for configuring iptables...basically Firestarter for KDE.  So any changes you made with Guarddog would be able to be reconfigured with Firestarter.  I'm guessing you've blocked port 80 (http) and maybe other ports.  All you need to do is re-enable them.

---

### Post by KezzerDrix on 2008-01-24
i found the disable tab on the last page.  As soon as I disable it I get internet.  The problem is that it resets itself at reboot.  Which is quite annoying,if I disable it and then remove it will that fix my  problem?

---

### Post by The Cog on 2008-01-26
Like I said - choosing to remove completely should get rid of it.

But you could also try configuring it correctly. Again, like I said, you need to enable DNS and HTTP on the Internet zone for a start. 

Once you've done that, if things still don't work, we need to start some diagnostics. Start by entering the command "ping ubuntuforums.org" and see if it can work out what IP adddress that is - if it can then we at least know that DNS is working.

---

