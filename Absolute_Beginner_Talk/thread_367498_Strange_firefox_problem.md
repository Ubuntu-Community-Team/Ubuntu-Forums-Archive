---
title: "Strange firefox problem"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by mikeman on 2007-02-22
Hi all,

I'm completely new in Ubuntu, and have ran into a strange problem. I have installed Ubuntu parallel to WinXP. It worked great, except I can't use the Firefox browser. Now, I know my connection is fine, because in XP it works. The strange thing is this: If I ping,say, 'ping www.google.com' in Ubuntu, then it pings ok. That means it can resolve 'www.google.com' fine, and can access it. If I take the IP address(in the form xxx.xxx.xxx.xxx) and enter it in the Firefox address bar, then I see google. But if I enter 'www.google.com', then it times out. The same thing happens with any address I have tried. 

Why is this happening? Any ideas on how I can fix it? Thanks in advance for any help.

---

### Post by ubunutgoz on 2007-02-22
Have you tried the following...

1 - try disabling ipv6

a - in FIREFOX browser type **about:config**
b - in the Filter bar (just below address bar) type **ipv6**
c - in the next window down (preferences), you'll see a single line [B]network.disable.Ipv6
[/B], double click until it is bold and the value is **true**

This could be all you need to do.  If it still doesn't work, follow these instructions which came from 

[http://www.linuxforums.org/forum/suse-linux-help/66053-firefox-painfully-slow.html](http://www.linuxforums.org/forum/suse-linux-help/66053-firefox-painfully-slow.html)

[B]In the address field, write:
about:config
Hit Enter
Change the following to “true”:
network.http.pipelining
network.http.proxy.pipelining
Change:
network.http.pipelining.maxrequests to: 10-30 ( I set it to 30, I got a 24 Mbps line)
Rightclick somewhere on the “page”
Click on new => Integer
Write in the dialog box:
nglayout.initialpaint.delay
Click OK
On the next dialog enter:
0 (Zero) click OK
Restart the browser.[/B]

That just might help!

Let me know
Alan

---

### Post by maestrobwh1 on 2007-02-25
Wow... I had disabled IVP6 in my etc/modprobe.d/alias file with a minor speed up.  Doing this in the browser made it fly!  Thanks!

---

