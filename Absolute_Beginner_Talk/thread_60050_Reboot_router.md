---
title: "Reboot router?"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by edwina on 2005-08-26
This must be easy, but I can't figure it out...

How do I reboot my router and then start using it under Hoary? If it isn't already on when I start my machine, there is a loooong pause as it tries to configure the network, then I have to reboot in order to get my router recognised. Is there a way of getting my router initialised/loaded/mounted from within Ubuntu?

Anyone ..?

Thanks.

---

### Post by xmastree on 2005-08-26
I'm guessing here, but...
The long pause you speak of will be ubuntu looking for a DHCP server from which to get it's configuration. If your router is off, it'll wait for a timeout before continuing.
If you've got this far, and want to configure the network once the router is on, you can go to System > Administration > Networking, select the network interface, deactivate it and activate it again.

At least I **think** that's what you mean...

---

### Post by edwina on 2005-08-26
Thanks xmastree, it may well be that simple. I'll give it a go when I get home and let you know. I have clicked idly around the network settings before, but never seem to get anywhere.

Do you think that there might be a way of setting the timeout on checking for a DHCP response? It is clearly way too long at the moment, as it only takes about 3 seconds with the router switched on, so only needs to check for about 10 seconds before assuming there is nothing available.

Thanks for the help.

---

### Post by xmastree on 2005-08-26
> Do you think that there might be a way of setting the timeout on checking for a DHCP response? Possibly, I would suggest you ask in the networking forum.
Also, it may be delayed while trying to check the time of day from the time server, you might want to disable that too.

---

### Post by edwina on 2005-08-27
Excellent, that all worked nicely.

I had clicked about in the Network Tools panels, but not the Networking panel. Ubuntu recognised my router and made it all work automatically, so I had never had to mess about with the Networking stuff before. I also wouldn't have guessed that deactivating and then reactivating eth0 was the secret to making it pick up that the router had been switched on. Well, this is the Noob forum after all ;-)

Thanks again, xmastree - this has been irritating me for a while.

Oh, by the way, ctrl-c makes the load-up skip the networking stage (or any stage, depending on when you press it, I think).

---

