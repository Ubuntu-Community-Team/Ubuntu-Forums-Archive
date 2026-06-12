---
title: "No Internet after Network Share!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-06-12
Help!
I was trying to share a folder from my Vista VM (VMWare Server), and suddenly my internet stopped working with both Konqueror and Firefox so I know its not the programs. But I know I have a connection because I'm typing this in my Vista VM. I really need to get my connection back. BtW, I already tried restarting X.

---

### Post by Corvinis on 2007-06-12
Did you try disabling the VMware connection / share?

This may clarify things:

[http://www.vmware.com/community/thread.jspa?threadID=87342](http://www.vmware.com/community/thread.jspa?threadID=87342)

---

### Post by HereInOz on 2007-06-12
How did you set up networking in your VM?  Bridged or NAT?  

I wonder if you can ping an external IP address from your Ubuntu system.  Try opening a terminal and typing:

ping 64.233.169.147

Do you get a response?  If so, then you have Internet connectivity from Ubuntu.

Can you open Firefox and type [http://64.233.169.147](http://64.233.169.147) and get a Google web site?

---

### Post by Nekiruhs on 2007-06-12
Nope, no good. Never got it to work anyway. Couldn't get my VM IP adress. Still not internet. Even after a reboot.
 
Corviniz:
I don't think you understand my problem. My HOST has no internet connection, but the GUEST does. Odd, eh?
 
HereInOz: 
My connection is vmnet0 (so bridged, I think)
This is what I got after typing that
```
 
PING 64.233.169.147 (64.233.169.147) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

```
and it just loops the last line

---

### Post by Nekiruhs on 2007-06-12
Please help me, I really dont want to reinstall again. I just got it setup the way I liked it!

---

### Post by Nekiruhs on 2007-06-12
BUMP!!!! Doesn't Anyone know what could be wrong???? I REALLY dont want to reinstall, but that looks like where I might be headed.

---

### Post by dreadlord_chris on 2007-06-12
> **Nekiruhs said:**
> Please help me, I really dont want to reinstall again. I just got it setup the way I liked it!

Uhmm, well.... the only help I can offer at this point is from my recent experience with vmware-server - I spent the last 4 days trying to get vmware-server working right here. It installed fine, I was able to install XP fine (took 46 minutes). Both guest & host were able to connect to the Intertubes just fine. And while they could see & ping each other - for some reason they refused to share folders between them, Samba not withstanding.

After much hair-pulling & head-banging I stumbled upon the solution that solved all my issues - VirtualBox [http://www.virtualbox.org/](http://www.virtualbox.org/) . Setup was a dream, XP installed in just over 20 minutes - and everything else just seems to work!

I know it doesn't really fix your vmware problem - but if you'd really just like to ge to work.....

---

### Post by Nekiruhs on 2007-06-12
I thought of Virtualbox a bit too late. Now my host has no internet, but my VM does, so I borked a config somewhere.

---

### Post by dreadlord_chris on 2007-06-12
Do you not have a connection even if vmware is not running?

---

### Post by Nekiruhs on 2007-06-12
Yeah, even if VMware is not running I get no connection. But Vmware gets a connection itself.

---

### Post by dreadlord_chris on 2007-06-12
Hmmm.... that is pretty odd... it probably has to do with vmware-server running as a service....
I'd just uninstall vmware - that should remove the virtual NICs that it installed, and should reset your real NIC.

---

