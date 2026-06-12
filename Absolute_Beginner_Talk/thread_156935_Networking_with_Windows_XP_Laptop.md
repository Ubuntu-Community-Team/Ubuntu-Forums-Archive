---
title: "Networking with Windows XP Laptop"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by Gracye on 2006-04-08
Ok, so I have a laptop with Windows XP and it networks with my Windows partician but I can't figure out how to network it with Ubuntu.

I've tried to figure out Samba but I can't, is there any other way?

---

### Post by Herman on 2006-04-08
Hello, Gracye,
 I always found that providing the Windows Network is set up in Windows, our Ubuntu Compturs can always access Windows shares just by going 'Places', 'Network Servers', and clicking an icon. It's simple! 
If it doesn't work, remember there are two firewalls in Windows, the one that comes with Service Pack Two plus the regular one you have to pay for. You might need to look in both and make sure they are open to the IP address/s of the other computer/s.
Also, if you have not done so already, run the Windows Network Wizard to configure your Windows network again if you still have trouble.
Most of the trouble connecting comes from Windows, not Ubuntu.

You should be able to access your Windows computer that way, but your Windows computer won't be able to access the Ubuntu one. That never bothered me very much because I do most of my work from Ubuntu anyway.
That's one reason people like to install Samba though. Another advantage of Samba, I think, has something to do with networking printers, but I don't find that necessary in my set-up.

I found SSH networking easy to set up in Ubuntu, and it does all I need to do, but I have never tried setting it up in Windows. I have recently found out that is possible. Maybe try SSH. [Info here]("http://www.users.bigpond.net.au/hermanzone/p11.htm"). SSH is supposed to be the most secure, as it uses encryption, and you won't have to alter your iptables (Linux firewall) to use it, so it is very easy. If you can figure how to install SSH in Windows too you should be all set.
I hope this will be some help to you, Regards, Herman.

---

### Post by Gracye on 2006-04-08
Thank you very much!  I'll have to try all that out.  I need to re-set up my network on Windows as I had to re-install everything because I messed up one of my partitions.  So I have to start from scratch again, but no matter, I'll get it all figured out.

Thanks again for you help!

---

