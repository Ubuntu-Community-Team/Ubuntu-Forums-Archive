---
title: "System/Administration/Networking terrible"
date: 2006-08-25
forum: Apple PPC Users
---

### Post by davidmaxwaterman on 2006-08-25
I am constantly frustrated by this tool.

I use a laptop I change networks fairly often, switching between a 'modem'+eth0 at work and eth1 at home.

Under OS X, such a change would work very well, even automatically, but under Ubuntu it is a real PITA.

The Networking tool seems to promise the same 'Location' based settings, but completely fails to deliver.

It seems not to save my 'modem' phone number, requiring me to retype it each time, and I often have to reboot in order to get the new configuration working properly (even though 'netstat -rn' and '/etc/resolv.conf' seem to have the correct settings).

When I try to use the 'Location', it takes ages (a minute or so) to switch between them - I might as well reboot.

Does anyone else have similar problems?

Max.

---

### Post by APU on 2006-08-25
I also had problems with the different network configuration tools (including Network Manager and Wifi-Radar) and therefore use manual configuration now. The problem mainly aroused because I use WPA encryption on my network and Network Manager cannot really handle this as of now. But this is not really relevant in your case anyway i guess.

I have written a little script (just a calling a bunch of "cp" commands from bash) that overwrites the files "/etc/network/interfaces" and "/etc/resolv.conf" files with others that I have preared for every location i work in. Then it issues "/etc/init.d/networking restart" to restart networking and use the new settings.

All it takes now is a "sudo netloc-change NameOfLocation" to reconfigure everything. NameOfLocation is of course refering to where the different network configuration files that I have prepared reside.

APU

---

### Post by hajk on 2006-08-25
You're not telling us what your hardware is, so difficult to suggest a solution to your problem. I know from experience that the new MacBook has a 
problem with slow activation of the wireless ath0 interface -- most likely some glitch in the new madwifi-ng driver modules (bug filed). I have not experienced any of the problems with the wired eth0 or ppp0 interfaces that you mention.

---

### Post by davidmaxwaterman on 2006-08-25
> **hajk said:**
> You're not telling us what your hardware is, so difficult to suggest a solution to your problem. I know from experience that the new MacBook has a 
problem with slow activation of the wireless ath0 interface -- most likely some glitch in the new madwifi-ng driver modules (bug filed). I have not experienced any of the problems with the wired eth0 or ppp0 interfaces that you mention.

Well, I didn't think the h/w was relevant, but I suppose it could be for the speed thing. I'm on a TiBook G4/800 DVI with airport, and have a Huawei CDMA PCICIA card fitted (that's the modem/ppp0 connection).

ath0? I've not heard of that. I have eth0 (wired), eth1 (airport), and ppp0 (modem)

Max.

---

