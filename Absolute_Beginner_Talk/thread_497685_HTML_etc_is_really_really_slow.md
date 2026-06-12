---
title: "HTML etc is really really slow"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Psychobiker on 2007-07-10
Hey,

Runnign xubuntu 6.06, and everything online is extremely slow, my connection settings are direct, the net works, but really slow. DNS server is the same as it was under Windows.
But, my downloads blast along at 200+ KB/s.

L

---

### Post by p_quarles on 2007-07-10
Do you mean kilobits/second (kbps) or or kilobytes/second (KBps)? If the former, then I could see why you're having trouble loading html, but if it's the latter, html is not your problem. 

What was your connection speed under Windows?

---

### Post by Psychobiker on 2007-07-10
200 kilobytes. It comes and goes sporadically, ie it will be blistering for a minute...then dead

L

---

### Post by p_quarles on 2007-07-10
Oh, I see. I misunderstood you're first comment. You're saying it was 200KB/s under Windows, but sporadic under Xubuntu? (I thought you'd meant that 200K was slow, and for some connections it is).

Has this been going on for a while? Because if you just loaded Xubuntu like, say, this weekend, it's possible your network is just having hiccups. Mine does that occasionally.

I'm probably not going to be much help beyond that. If it were me, I'd look at any other machines connected to the network (if it's wireless, make sure no one's leeching your WAP), using a lighter browser (like Epiphany), and logging into the modem's admin tool and checking for problems there.

Also, I'm assuming you're running a slightly older machine (no other reason to use Xubuntu), so make sure that IPv6 is disabled. That can cause all kinds of network problems on machines that don't get along with it.

---

### Post by Psychobiker on 2007-07-10
It's a laptop,

1.5GHz, 256MB...ancient doorstop of a thing. My main rig would take Ubuntu no problem.

How does one disable IPV6?

L

---

### Post by p_quarles on 2007-07-10
Ubuntu made my doorstop useful again, as well (it's running the server edition). Gotta love that. 

This link will guide you through it:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?action=show&redirect=DisableIPv6)

---

### Post by Psychobiker on 2007-07-10
no go. tells me unknown mime type. and it won't let me save it if I edit it in thunar

L

---

### Post by p_quarles on 2007-07-10
The problem with Thunar is most likely that you aren't root. Unfortunately, I see, that tutorial didn't give any instructions for Xfce.

You can still edit either of those files in the terminal, though. Try this to get it open ```
sudo vim /etc/modprobe.d/blacklist
```
or ```
sudo vim /etc/modprobe.d/aliases
```
Vim isn't really a beginning text editor, but I don't use nano, so wouldn't be able to give you instructions. Anyway, when you open the file, you'll need to switch to interactive mode by pressing the letter "i." Then, go ahead and make the appropriate changes to the appropriate file. Switch out of interactive mode by pressing [esc], and then type these commands to save and exit ```
:w
:q
```
Note that you will need to type out the colons, then the letter, then press enter. 

That should let you edit the files. Still don't know if it will solve the problem, though.

---

### Post by Psychobiker on 2007-07-10
cheers! will try

---

### Post by Psychobiker on 2007-07-10
wheeeeeeeeeeeeeeeeeeeeee! 
Going like its **** is on fire

L

THANKS :D

---

### Post by p_quarles on 2007-07-10
> **Psychobiker said:**
> wheeeeeeeeeeeeeeeeeeeeee! 
Going like its **** is on fire

L

THANKS :D
Cool. Glad it worked.

---

