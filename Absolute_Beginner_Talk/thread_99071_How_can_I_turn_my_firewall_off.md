---
title: "How can I turn my firewall off?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-12-04
I've read lots of posts from lots of people re: inability to open ports for Azureus, etc.  The advice usually given is "install firestarter, tell it to allow ports xxx-yyy, apply."  This is totally not working for me.  When I go to [ShieldsUp]("https://www.grc.com/x/portprobe=55555"), it still tells me the ports are closed, even though my router is set to foreward them to me and firestarter is set to allow access to them.

I really don't want to give up Azureus.  So my question is: is there a way to disable firewall altogether?

---

### Post by tokyovigilante on 2005-12-04
It depends on which firewall (router, Firestarter, both) is the problem. My system is set up to disable the NAT fireall on my DSL modem and have my server as a demilitarised zone (ie just forward all the traffic to my server) which runs Firestarter, then I can forward the appropriate ports (Bittorrent etc) without worrying about my router.

You need to work out whether your router is blocking access to your ports before Firestarter gets a chance to see them. I'd say this is more likely the case, as Firestarter by default stealths ports rather than closes them (Closed means your computer sends a response denying access to the port, whereas Stealthed just ignores the request, which is more secure). It's better not to disable all firewalls completely, especially if you have a dedicated (DSL or other broadband) connection with a static IP.

Go to ShieldsUP! and run the Common Ports Scan and post the result (minus your IP), with and without firestarter enabled (sudo firestarter in a terminal, then click the enable/disable buttons).

BTW, what service are you running that needs port 55555? (I assume its a custom one you've set up). What brand of modem/router are you using? What type of connection do you have?

---

