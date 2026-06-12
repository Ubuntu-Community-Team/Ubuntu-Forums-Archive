---
title: "Problem when setup VPN, there is no left click menu item named VPN ..."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-20
Hi
thank you for reading my post
I have followed several tutorial in
[http://shiny.thorne.id.au/2007/01/pptp-from-ubuntu.html](http://shiny.thorne.id.au/2007/01/pptp-from-ubuntu.html)
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
and some thread in ubuntuforum itself in order to become able to install make my vpn works.

To get you an overview of what i have done:

- sudo apt-get install 
- sudo apt-get install pptp-linux
- sudo apt-get install pptpconfig
- sudo apt-get install network-manager-pptp

All of the above command executed successfully.

Now I have done the following:

kill nm-applet, execute the following commands:

sudo /etc/dbus-1/event.d/25NetworkManager restart
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher restart

run nm-applet

After all of the above sequence there is no new item when I left click on network icon in system try.
The only menu item that is present is "manual configuration..."

Can you please let me know what should I do?
I have Ubuntu 7.10, Gutsy Gibbon.

Thanks

---

### Post by mgmiller on 2008-01-20
Your network card needs to be set to dhcp or roaming mode for this to work.  If you have a static IP, the vpn choices will not appear.  I also have a lot of trouble getting this to work.  I can get the vpn choice to appear, but still can't get it to connect properly to my work vpn.  

Used to work perfectly in Ubuntu 6.06, but not since then.

---

### Post by legolas_w on 2008-01-21
Hi
Thank you for your reply.
So, for now there is no way to configure the VPN with static IP?
It is really an stopper.

Thanks.

---

### Post by mgmiller on 2008-01-21
> So, for now there is no way to configure the VPN with static IP?

I'm afraid not.

There is a really long forum thread about this problem.  If you have the time, you can read through it.  There are work arounds for the static IP  problem involving making different profiles in the Location box in Network Configuration.
Here is a link to the thread:
[http://ubuntuforums.org/showthread.php?t=91249]("http://ubuntuforums.org/showthread.php?t=91249")

Hopefuly this will be fixed in Hardy 8.04, which is an LTS release.  The last time VPN worked for me with static IP was in 6.06 which was also LTS.

---

### Post by legolas_w on 2008-01-21
Hi

Is there some kind of patch or some kind of backport to make static IP and VPN work fine in 7.10?
It is somehow sad, I can not connect to my employer network, my internet provider do not provide DHCP so I must use static IP given by them, on the other hand I should use VPN over the same connection.

I looked at the tread and I did not find anything do-able to make static IP and vpn works fine.


Thank you.

---

### Post by mgmiller on 2008-01-21
Unfortunately, there is no way to make a static IP work with vpn in 7.10.  The work arounds all involved using DHCP.  The last time I could make this work with a static IP was with 6.06.

Maybe you could dual boot 6.06 and 7.10?

I am hoping this is resolved in April when they release version 8.04

---

