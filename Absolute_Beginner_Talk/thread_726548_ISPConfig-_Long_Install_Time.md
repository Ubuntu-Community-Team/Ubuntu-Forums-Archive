---
title: "ISPConfig- Long Install Time?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by drndrw on 2008-03-16
Hey guys. I am currently installing ISPconfig on my Linux server, and so far its been going for over two hours. I think its working, but it takes forever. Is it working? Thanks!

---

### Post by bsharp on 2008-03-16
I haven't installed ISPConfig in a while, but if I remember correctly, you should be sitting there typing in commands... and yes if you are typing commands it does take a while.

---

### Post by drndrw on 2008-03-16
Okay, well the thing just stopped. Three hours later. And it didn't work. Why not? Is it going to take another three hours to make it work? What do I do? This is my error:

> ERROR: Could not configure SpamAssassin
cd: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
mv: cannot stat `binaries/aps.tar.gz': No such file or directory
mv: cannot stat `binaries/spamassassin.tar.gz': No such file or directory
mv: cannot stat `binaries/uudeview.tar.gz': No such file or directory
mv: cannot stat `binaries/clamav.tar.gz': No such file or directory
mv: cannot stat `binaries/cronolog': No such file or directory
mv: cannot stat `binaries/cronosplit': No such file or directory
mv: cannot stat `binaries/ispconfig_tcpserver': No such file or directory
mv: cannot stat `binaries/zip': No such file or directory
mv: cannot stat `binaries/unzip': No such file or directory
tar: spamassassin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `spamassassin': No such file or directory
tar: uudeview.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `uudeview': No such file or directory
tar: clamav.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `clamav': No such file or directory
tar: aps.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./setup2: line 873: ispconfig_tmp/php/bin/php: No such file or directory
ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here!

---

### Post by bsharp on 2008-03-16
Try following this tutorial, it's how I've gotten mine working:
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by drndrw on 2008-03-16
Yeah, I followed the whole tutorial as well. I am attempting to re-install with Spam assassin installed. How long should a successful install be?

---

### Post by bsharp on 2008-03-16
I would say about an hour, but from what I remember there are parts where it is compiling and some where you should be sitting there entering alot of commands.  Sorry I can't help any more than this.

---

### Post by drndrw on 2008-03-16
Yeah, I am entering a few commands. I wonder if that causes the slowing. But should I open port 81 before installing?

---

### Post by bsharp on 2008-03-16
I didn't need to, but it depends on your firewall configuration.

---

### Post by drndrw on 2008-03-16
I'm not sure if it's my firewall, or my router that is not letting me connect. Apparently everyone I talk to cannot see my web address. Can you?

drndrw.gotdns.com

I am using the ddclient with it, by the way. Does that effect anything?

---

### Post by bsharp on 2008-03-16
Your address isn't loading for me, 
do you have port forwarding set up correctly on your router? I don't think ddclient would matter, unless it is being blocked.

---

### Post by drndrw on 2008-03-16
I just restarted my router also, so if you could check again. But, I am using that address on my computer, and it works fine. I'm not sure if I have ddclient blocked, as I am using SSH with it on a Windows computer. Is there a way to see if it is or not?

---

### Post by bsharp on 2008-03-16
I see the problem: your dns records are pointing to your LAN address instead of your WAN address.  Go to [http://whatismyip.com](http://whatismyip.com) and change your records to point to that instead.

---

### Post by drndrw on 2008-03-16
Oh! Wow, I don't know how that happened. I put in my dynamic address before. But now, I'm not getting anything on the page. Why is this? I have my ports opened in my router.

---

### Post by bsharp on 2008-03-16
Opened ports and forwarded ports are 2 different things.  Opened merely means stuff can get through, forwarded means anything on that external port is sent to the internal port.  

As for the reason it changed, when you restarted your router the server got a new IP address from DHCP.  ddclient took the *internal[i] address and sent it to the DNS server instead of the [i]external*

---

### Post by drndrw on 2008-03-17
No, I set my LAN address to a static one. And do I want opened or forwarded then?

---

### Post by bsharp on 2008-03-17
You should forward them, and it doesn't matter if your LAN ip is static or not, because ddclient is sending the LAN address to the DNS server instead of the WAN address.

---

### Post by drndrw on 2008-03-17
Oh. So then must I change BIND settings also?

---

### Post by bsharp on 2008-03-17
No, not BIND, when ddclient is syncing with the DNS server at drndrw.gotdns.com, it is sending your LAN address.  The local DNS server doesn't matter in this instance, but I'm not sure on how ddclient should be configured, as I've never done that before.

---

### Post by drndrw on 2008-03-17
Okay, I know what I need now. What is a web address that will show me my dynamic IP address?

---

