---
title: "MOL-wireless? DHCLIENT"
date: 2007-01-18
forum: Apple PPC Users
---

### Post by Uta on 2007-01-18
Before I installed MOL along with these, (ipmasq, dnsmasq, dhcpd) I had a working wireless setup on my iBook G4. Now I have no connect, although if I (ifconfig in the terminal) I see that I do have an IP and my wireless card does display(in my case it's eth1).
How can I troubleshoot this. I have unplugged my router and restarted that, I have restarted dhclient and I see an IP from my router. Everything looks fine but I no longer can get to the Internet. Also I can not ping the router.Also after trying "sudo dhclient eth1" I get bound to 192.168.0.108. This use to be a valid IP from my router?
thanks

---

### Post by Uta on 2007-01-18
the only way I could get my Internet connect back was to uninstall MOL and the two additional files I had installed (ipmasq and dnsmasq). I'll wait till I upgrade to Edgy to try this again.Phew!

---

### Post by calum on 2007-01-19
> **Uta said:**
> Before I installed MOL along with these, (ipmasq, dnsmasq, dhcpd) I had a working wireless setup on my iBook G4. Now I have no connect, although if I (ifconfig in the terminal) I see that I do have an IP and my wireless card does display(in my case it's eth1).
How can I troubleshoot this. I have unplugged my router and restarted that, I have restarted dhclient and I see an IP from my router. Everything looks fine but I no longer can get to the Internet. Also I can not ping the router.Also after trying "sudo dhclient eth1" I get bound to 192.168.0.108. This use to be a valid IP from my router?
thanks

Several MOL users (including myself) have reported that they have to run 'sudo /etc/init.d/ipmasq restart' after any network (re)config, which includes having to do it as soon as you've booted.  

If you don't want to use MOL's networking functionality, you can probably just uninstall ipmasq and dnsmasq, and things should go back to normal.

---

### Post by Uta on 2007-01-19
I reinstalled mol again but this time I did not install "ipmasq and dnsmasq", I added in my dhcp.config file, INTERFACES= " eth1 tun0" and in my /etc/mol/molrc.net file I added "netdev: tun0 -tun" and removed from my /etc/mol/tunconfig file "/etc/init.d/ipmasq restart" and "/etc/init.d/dnsmasq restart"
I rebooted my linux system just to make sure I would retain my wireless connect (it did) and then I started mol, it worked, mol found it's internet connect. Mac on Linux in Dapper works with a wireless connect.

---

