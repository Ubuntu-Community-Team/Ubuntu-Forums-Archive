---
title: "A rude localhost ('cannot connect' errors in t-bird, EAC)"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by TeaSwigger on 2007-07-21
Having the Learning Curve Blues here. 

When I initially installed kubuntu and Thunderbird (2x, via the ubuntuzilla script and with webmail extensions) it worked "out of the box." After recent updates the webmail accounts stopped working, throwing a 'Cannot connect to localhost' at you. So in webmail's settings, it indicated its SMTP and POP connections were out of order; I set the ports above 1024, restarted and now they give the green light. But same errors! No email... :-s

Further, Amarok and Exact Audio Copy (via WINE) hang/crash when attempting to poll freedb for track info.

Ideas? Pointers? Cups of ubuntu? :)

---

### Post by nanotube on 2007-07-23
so, you changed the ports in the webmail settings - but did you also change the ports in your account settings for the pop and smtp servers?

---

### Post by TeaSwigger on 2007-07-25
Ah yes indeed I did. 1025 pop, 2025 smtp in webmail and server settings in the accounts. I still get "cannot connect to localhost" and am still stumped! This localhost problem on webmail and (presumably a similar issue on) EAC is the only issue making me boot back into windows.

nanotube, your Ubuntuzilla script is excellent by the by. :)

A bit of help in return in case it helps anyone: if anyone is running the current ubuntu install (thunderbird 1.5x), you can get Webmail extensions that are made to work in 1.5x here:
[http://groups.google.com/group/thunderbird-webmail-extension/files](http://groups.google.com/group/thunderbird-webmail-extension/files)
The current versions at the webmail site:
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)
are meant for the current Mozilla build (2.x).

---

### Post by TeaSwigger on 2007-07-28
Ookay maybe I can focus on fixing this problem this weekend :)

Perhaps I should add:
The webmail and EAC did work when I first took Ubuntu for a test drive about a month ago. So it should work. It's not working on my subsequent and present install (Kubuntu), nor is it working on my new install of Xubuntu on a second PC.

The [COLOR="Red"]Cannot Connect to Server Localhost[/COLOR] errors were occuring before I installed the guarddog firewall I'm now running. In the firewall I have specified that the email ports be allowed locally and to 'internet', and set a rule to allow the ports I moved the webmail settings to. No difference either way so I'm assuming the firewall is unrelated.

I've uninstalled t-bird and WINE / EAC, and their config files etc best I could and reinstalled fresh, but the behavior remains the same. Aside from these issues these apps appear to be running fine. T-Bird moans [COLOR="Red"]Cannot Connect to Server Localhost[/COLOR] and EAC freezes when trying to poll CDDB. :(

---

### Post by TeaSwigger on 2007-07-28
And yes, my /etc/network/interfaces does have the loopback, as per solutions in other localhost threads; it says, and I paste ;) -

```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by TeaSwigger on 2007-07-28
Double checking permissions... Permissions for all files in my ~/.thunderbird folder are -rw-rw---- 

Sound right?

---

### Post by nanotube on 2007-07-28
just as a check, try turning off your firewall completely, and see if that changes anything...

---

### Post by TeaSwigger on 2007-07-28
Back, and tried disabling the firewall, and rebooting with firewall disabled; behavior is the same. :|

---

### Post by nanotube on 2007-07-29
> **TeaSwigger said:**
> Back, and tried disabling the firewall, and rebooting with firewall disabled; behavior is the same. :|

open a shell, and try telnetting to your pop server. you said you have pop on 1025, so try:
```
telnet localhost 1025
```
and see what comes up. 
it should connect, and tell you that you are connected to a pop server.

---

### Post by TeaSwigger on 2007-07-29
Hello, 

I tried it in the terminal and this was the response:
```

Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

This behavior is the same on both PCs.

---

### Post by nanotube on 2007-07-29
> **TeaSwigger said:**
> Hello, 

I tried it in the terminal and this was the response:
```

Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

This behavior is the same on both PCs.

ok, so... it is clear that your pop server is not running. :) now we're getting somewhere...

what's the output of
```
sudo netstat -plantu |grep 1025
```
do you get anything? you /should/ be seeing that thunderbird is listening on port 1025...

also, try putting your pop server on a higher port, like 4000, and see if that changes anything (ie, then restart your thunderbird, and try telnetting to localhost 4000)

---

### Post by avik on 2007-07-29
So you're saying the error is "Cannot connect to localhost," meaning the programs are trying to connect to your own computer?  Why's that?  Do you have a server running to handle these connections to your computer?

---

### Post by nanotube on 2007-07-29
> **avik said:**
> So you're saying the error is "Cannot connect to localhost," meaning the programs are trying to connect to your own computer?  Why's that?  Do you have a server running to handle these connections to your computer?

read further up in the thread - he's using the webmail extension for thunderbird, which creates a pass-through pop server through which tbird can get email from hotmail and yahoo and other webmails. :)

---

### Post by TeaSwigger on 2007-07-29
Thanks for your help :)

Output of sudo netstat -plantu |grep 1025 is:

```
tcp        0      0 127.0.0.1:1025          0.0.0.0:*               LISTEN     7346/mozilla-thunde
```

Will try port 4000 & be right back...

EDIT back... result is the same "cannot connect." sudo netstat -plantu |grep 4000 gets:

```
tcp        0      0 127.0.0.1:4000          0.0.0.0:*               LISTEN     7422/mozilla-thunde
```

"telnet localhost 4000" gives:

```
telnet: could not resolve localhost/4000: Name or service not known
```

---

### Post by nanotube on 2007-07-30
> **TeaSwigger said:**
> Thanks for your help :)

Output of sudo netstat -plantu |grep 1025 is:

```
tcp        0      0 127.0.0.1:1025          0.0.0.0:*               LISTEN     7346/mozilla-thunde
```

Will try port 4000 & be right back...

EDIT back... result is the same "cannot connect." sudo netstat -plantu |grep 4000 gets:

```
tcp        0      0 127.0.0.1:4000          0.0.0.0:*               LISTEN     7422/mozilla-thunde
```

"telnet localhost 4000" gives:

```
telnet: could not resolve localhost/4000: Name or service not known
```

hm, interesting... 

what's your output of 
```
cat /etc/hosts |grep localhost
```

and what happens if you try to telnet by ip:
```
telnet 127.0.0.1 4000
```

---

### Post by TeaSwigger on 2007-07-30
):P 

telnet 127.0.0.1 4000 -

```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

cat /etc/hosts |grep localhost -

```
::1 ip6-localhost ip6-loopback
```

---

### Post by nanotube on 2007-07-30
> **TeaSwigger said:**
> ):P 

telnet 127.0.0.1 4000 -

```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

cat /etc/hosts |grep localhost -

```
::1 ip6-localhost ip6-loopback
```

the connection refused part leads me to strongly suspect a firewall... but also /etc/hosts should have a listing for localhost for 127.0.0.1
mine looks like this:
```

127.0.0.1       localhost
127.0.1.1       groovy4

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
so add that localhost line to the beginning of your /etc/hosts, reboot just in case :), try again...

also, it could just be something bad with the webmail extension... try uninstalling it, and then reinstalling?

another thing to check: ubuntu has a local cups server running by default on port 631. try ```
sudo netstat -plantu | grep 631
```
and if it's there, try
```
telnet 127.0.0.1 631
```
and see if it connects.

that way we could see if the cannot connect problem is specific to webmail, or to all local ports...

---

### Post by TeaSwigger on 2007-07-30
Ah we must be making some progress here... edited in '127.0.0.1       localhost' which I gather should have been there. Why it compiled without it is beyond me, but now the 'cannot connect' error is gone! ...Replaced by *always* timing out while 'connecting to remote server'. And EAC still hangs when attempting to connect to freedb. ...arr... 

EDIT - webmail is working! I'd tried yahoo, but as it turns out yahoo's servers - or somewhere in my ISP chain - was funky at the same time I was trying it! Now working :) ...but not EAC's polling freedb.

sudo netstat -plantu | grep 631 -

```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4751/cupsd
```

telnet 127.0.0.1 631 -

```
telnet 127.0.0.1 631
Trying 127.0.0.1...
Connected to 127.0.0.1.
```

Networking definitely isn't in my areas of expertise ;) so if something went wrong I don't know how to find out what to do... Is there some way to make it recompile ip tables and whatever related aspects anew? Don't know if it'd work but if there's an easy way to try...

Definitely appreciate the help from you and the community. That's the main thing that has inspired me to try moving from the proprietary M$ world. :)

---

### Post by TeaSwigger on 2007-08-05
Solved! 

Two separate issues as it turned out.

Issue 1 - webmail in Thunderbird would result in 'cannot connect to localhost' errors. 

Solution was a combination of - 

1) Edited /etc/hosts file to include the following which should have been present but for whatever reason was not: 127.0.0.1       localhost

2) In Thunderbird's extension manager > WebMail > options, set pop, smtp and imap ports above 1024 and restart them.

Issue 2 - Exact Audio Copy, running in WINE v0.9.42, crashed when attempting to poll cddb or freedb. 

Solution: For other reasons I downloaded WineXS (via [http://frankscorner.org/](http://frankscorner.org/) ) and installed the items under "install system files." After doing so I discovered EAC works fine. I have no idea why, but it does.

There 'tis in case it helps anyone.

---

### Post by nanotube on 2007-08-05
hey, sorry i kinda forgot about this thread for a few days... 
so... the /etc/hosts edit did solve the problem after all? heh nice. :)

---

