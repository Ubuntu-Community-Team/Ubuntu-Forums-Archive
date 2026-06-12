---
title: "Can't see Windows network from Feisty Fawn..."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by magicalpath on 2007-09-11
Hi,

This is similar to an earlier posting by someone else, which seems to be unanswered: [http://ubuntuforums.org/showthread.php?p=2347448](http://ubuntuforums.org/showthread.php?p=2347448)

Until I set a static IP address I had no problems browsing the network. I am guessing the information retrieved from the router (DHCP server) was sufficient to allow full browsing of shared directories.

However, as I'm planning on setting up a server accessible to the outside world I didn't want to risk the DHCP client changing the IP address at some stage, so set a static IP address in Ubuntu. 

Since then I have been unable to browse the Windows network. When going Places | Network I see the toes on the foot icon move for a few seconds, and the "Windows Network" icon is displayed. Clicking on this however instantly goes to a black directory - smb:///

I've spent considerable time going through SAMBA tutorials, and *almost* (but not quite) got the Ubuntu box browsable from Windows. I can get as far as seeing a "SharedFiles" and "Printers and Faxes" icon, but for whatever reason I get a "not accessible" error message. This isn't a big deal, as I wasn't overly interested in sharing stuff on the Ubuntu side just yet. I've checked the user account in this case, and have it set to "username" and blank password. Unfortunately, if I set a non-blank password and am prompted for it (well say it is "test123") this fails also. I'm wondering if there is a problem using letters and numbers for Ubuntu passwords??? I ask, as I am using TightVNC to access Ubuntu and I can use a password of "test" but "test123" fails... weird.

Anyway, back to the SMB issue... any ideas would be appreciated. I'm happy to get it working only from Windows to Ubuntu, but I'd also like to be able to go the other way also.

Kind Regards,
Graeme

---

### Post by rivalarrival on 2007-09-11
If you had it working with dhcp, set up your router to always issue its mac address the same IP... You get a dhcp address, but it's always the same one.

Since you switched to a static IP, are you still using your router for DNS resolution, or did you specify your ISP's DNS server directly? How about WINS?

I never did get the hang of browsing local network shares...  I just used static IP addresses on all the servers and set the clients to go directly to those IP's instead of trying to resolve addresses from a name server.

---

### Post by BrendanM on 2007-09-11
You can set up the names of other computers on your network in your /etc/hosts file, which will then allow you to connect to them by name.

---

### Post by magicalpath on 2007-09-11
> **BrendanM said:**
> You can set up the names of other computers on your network in your /etc/hosts file, which will then allow you to connect to them by name.

Hi Brendan,

Thanks for that tip. It has given me a workaround which will do until I have time to fix the Windows XP -> Linux sharing... eventually I'll have one drive on the Ubuntu box as a file server.

For now though I put "192.168.1.x WinXPMachine" into the hosts file, and I can now go to SMB://WinXPMachine and see the shares correctly.

I think the problem will be like you said in your first message, and to do with the box not getting the network details it needs from the router. I haven't checked if I can fix the IP address to the MAC address, but possibly, it is a decent Linksys router. I will check this option out soon.

Kind Regards,
Graeme

---

