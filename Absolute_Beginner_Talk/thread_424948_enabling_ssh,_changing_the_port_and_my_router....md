---
title: "enabling ssh, changing the port and my router..."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by abouttogiveup on 2007-04-27
OK. so i have 6.10 efty setup on my desktop at home (first timer) and i would like to connect to it remotely if possible.

So..  telnet probably isn't the best thing, so i guess ssh connection would be.  I have done a bit of searching, and i understand that if i am on a 192.169.xxx.xxx network then i cannot use those ip addresses internally from my laptop.  I can see how to enable SSH for that PC on by BTHomeHub, which i guess is on port 22, but from what i understand i am better of selecting another random port number for security, which i will look at how to do.

but..  assuming i have done all of that and i use my WAN (BT) address to connect on the right port from an SSH client like Putty on windows, what do i have to do on xubuntu to 

[LIST]
[*]checkk that ssh is installed and enabled
[*]allow ssh connections
[*]change the port it uses
[/LIST]

Thanks in advance (again)

M

---

### Post by rich.bradshaw on 2007-04-27
Basic How To:

Install ssh server:

sudo apt-get install openssh

Now this service should be running. Try:

ssh localhost

If it asks for a password, then you are successfully running ssh!

Yes, ssh is by default on port 22. If you have a strong password, that's probably OK - you might want to change it to a different port - I personally don't bother. 

If you have another comptuer on your LAN then use Putty in Windows, or just ssh in linux to connect to your server computer.

If you need to know it's internal ip, you can type 

ifconfig

this will show you all your connections. Find the one you connect with (prob eth0) and look at the inet addr. This is your IP.

If you can connect in the LAN you are sorted.

Forward port 22 to your computer using your homehub. 

On a remote computer connect to your external address. This might change, so you might want to sign up for free at dyndns.org so that you can assign a name to your computer. Then you don't have to remember it.

Most likely things to go wrong:

Don't know external IP address
IP address isn't static inside LAN, so it is different on each boot


Good Luck!

---

### Post by abouttogiveup on 2007-04-27
weyhey..   that worked.  Thanks very much.

Being a paranoid though, i would like to change the port.

I changed the port in sshd_config to another free port, and made changes in /etc/services to indicate the new port too..  is that all i would need to do?

in /etc/services, would you need to change the tcp and udp one..? sorry for my ignorance here.

M

---

### Post by abouttogiveup on 2007-04-27
that and a reboot seems to have done it..

thanks again for your help..

Everyday, Ubuntu gets that little bit easier for me.

M

---

