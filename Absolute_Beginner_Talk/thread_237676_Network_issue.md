---
title: "Network issue"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by in_orbit on 2006-08-16
Hi, 

I'm having problems connecting to a network. First of all nothing happens when I click at the icon for the network properties in the menu. I've managed to set my ip and the default gateway though by using the shell but how do I set the DNS-servers? I really don't want to run a script every time I log in at the computer to access the internet...why can't ubuntu just remeber my ip-settings? Help me please!

/In_orbit

---

### Post by jrjr on 2006-08-16
.

---

### Post by bensexson on 2006-08-16
Are you using DHCP? Are you using the Network Settings GUI under System --> Administration?

---

### Post by in_orbit on 2006-08-16
No, I'm not using DHCP and nothing happens when I try to execute "Network settings" found in the System/Administration-menu.

---

### Post by jrjr on 2006-08-16
.

---

### Post by in_orbit on 2006-08-17
That did work but I can't configure my network card for some reason. When I choose eth0 and click on configure nothing happens. What the hell might be wrong here? :confused:

Is there some file I can set my ip-address, gateway and DNS-servers manually?

---

### Post by jrjr on 2006-08-17
.

---

### Post by in_orbit on 2006-08-17
When I run gnome-nettool from the prompt I get this error message after a while:

"(network-admin:6031): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Usage:program_name [address][:port]"

Both IPv4 and IPv6 seems to be enabled. May that cause the conflict?

---

### Post by jrjr on 2006-08-17
.

---

