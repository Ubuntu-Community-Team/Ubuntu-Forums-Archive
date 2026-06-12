---
title: "Tor, IPTables"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2008-01-04
Hello all,

Being the curious person that I am, I decided to see what else I could do with Linux :)
I found a blog with instructions on how to surf anonymously....
[http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html]("http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html")

2 things that concern me:

- I managed to get Tor working with the FoxyProxy addon and it successfully "changed" my IP address. I ran a Shields UP! test and found that a port was completely open (Port 1027). Am I okay?

- I messed around with the addons (Firefox extensions), but didn't touch anything related to my system. I also removed both tor and privoxy...This didn't effect iptables or my firewall in any way correct? Tor doesn't have the ability to change the way iptables functions right? I just want to make sure my firewall/computer security is still properly intact!

Thanks!

---

### Post by pieterjanvu on 2008-01-04
you might want to reset iptables to default
i think its sudo iptables -F

---

### Post by Hospadar on 2008-01-04
unless you were running tor with root privileges (sudo or su, or if it started as a service it probably was run as root) there is no way for it to change iptables.  Although any way you slice it, I doubt that stuff should have affected iptables.  blocking and opening ports isn't really what tor does, it just redirects you to anonymizing servers.

---

### Post by isaacj87 on 2008-01-04
Thanks for the responses guys...

What about the open port problem? I figured it was an open port with Tor servers...but can this negatively effect me?

---

### Post by pieterjanvu on 2008-01-04
open ports are seen as insecure
closed and stealth ports are seen as secure
in terms of firewalls atleast thats what i've read in forums

---

