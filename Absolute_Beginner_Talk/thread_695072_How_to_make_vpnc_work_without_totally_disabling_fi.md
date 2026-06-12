---
title: "How to make vpnc work without totally disabling firewall?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by bbqsandwich on 2008-02-12
Hello,

I connect to my company's network from home using vpnc.

I have Firestarter installed. I cannot go to any Web pages or access any company files when the firewall is running. If I use Firestarter to completely disable the firewall, everything works fine.

However, it seems to me that disabling the firewall is not a good idea. Correct?

Is there any way to set up my firewall (or whatever other aspect of the system I would have to change) so I can use the VPN connection without disabling the firewall?

Oddly (or maybe not), the VPN connection worked totally fine before I installed Firestarter for the first time. I tried uninstalling Firestarter, hoping it would put things back to the pre-Firestarter configuration, but that did not help. Now that it is installed, the only way I can get it to work is, as I mentioned, disabling the firewall.

I have searched the forum for other vpnc-related threads and have been unable to find an answer.

Thank you for your help!

[I]EDIT: After some more Googling, I came across a page with an answer: [http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/](http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/)
[/I]
**Here are the instructions, in case anyone has a similar problem and stumbles across this thread:**

You have to edit user-pre file under /etc/firestarter/. First make the file writable by issuing the command

```
sudo chmod 600 /etc/firestarter/user-pre
```

Then edit the file

```
sudo gedit /etc/firestarter/user-pre
```

Copy and paste the following lines in that file:

```
iptables -A INPUT -j ACCEPT -s xxx.xxx.xx.xxx -p esp
iptables -A INPUT -j ACCEPT -s xxx.xxx.xx.xxx -p udp -m multiport --sports isakmp,10000
iptables -A INPUT -j ACCEPT -i tun+
iptables -A OUTPUT -j ACCEPT -d xxx.xxx.xx.xxx -p esp
iptables -A OUTPUT -j ACCEPT -d xxx.xxx.xx.xxx -p udp -m multiport --dports isakmp,10000
iptables -A OUTPUT -j ACCEPT -o tun+
```

Enter your company server's IP address in place of xxx.xxx.xx.xxx. Save and close the file. Restart the firestarter using
```

sudo /etc/init.d/firestarter restart
```

...And then connect using vpnc, and it should work! At least, it did for me.

Also, it is worth noting that it appears you can enter a domain name, like ourvpn.mycompany.com, instead of the numerical IP address.

This was also covered in the following thread on this very forum: [http://ubuntuforums.org/showthread.php?t=80076](http://ubuntuforums.org/showthread.php?t=80076)
But for some reason, I could not find it in searching.

---

### Post by frigaut on 2008-03-12
Works great for me (in hardy). Thanks!

---

