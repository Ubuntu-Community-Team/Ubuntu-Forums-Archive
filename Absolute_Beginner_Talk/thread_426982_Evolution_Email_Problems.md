---
title: "Evolution Email Problems"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Grumblebum on 2007-04-29
New to Ubuntu.  Have set up ADSL modem, am talking using Firefox on Ubuntu.  Cannot get Evolution email talking to ISP, even though setting are exactly the same as on my XP box.  Is it a security thsing?  The email setup seems straightforward and I have over 20 years experience inMicrosoft support.  Comms either times out or says it can't find a route to the server.  Assistance appreciated.

BTW, have same problem with trying to run updates:

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by lamalex on 2007-04-29
sounds like a DNS issue.

---

### Post by Grumblebum on 2007-04-29
The DNS is in the modem/router and the TCP/IP settings.  If they work in Windows, why not Ubuntu?

---

### Post by freebird54 on 2007-04-29
There may be an older router (non ipv6 aware) in your setup.  ipv6 is enabled on Edgy and up, and WILL mess up the DNS with older routers than don't know how to handle it (like my Linksys).  It is easy enough to blacklist it, and see if that was your problem...  Open a terminal and:

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add this line to it

```
blacklist ipv6
```

Save the file, exit and reboot your computer. 

Hope this helps...

---

### Post by Grumblebum on 2007-04-29
Thanks for the suggestion, but I already had IPV6 blacklisted previously, because of other networking problems I had.  Current blacklist is:

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist ipv6

BTW, my modem is a brand new ADSL2+ VoIP Router, D-Link DVA-G3340S.  In that case it should be aware of IPV6 anyway.....

---

### Post by freebird54 on 2007-04-29
Well - that eliminates THAT possibility!  Sorry, can't think of anytihing else causing both troubles at this time (n00bie here too).

I did see a thread suggesting that USB connection problems might be behind such things.  Are you hooked up that way?  Which version of the OS?

Thread..  [http://ubuntuforums.org/showthread.php?t=425571&highlight=DNS+problem](http://ubuntuforums.org/showthread.php?t=425571&highlight=DNS+problem)

Still looking.... :)

---

### Post by Grumblebum on 2007-04-29
Version of the OS is beside my bean count.  DNS is handled by my modem, which is also a DNS server to the PC.  That way, I only have to set it up once for Windows and Ubuntu.  Running both systems off dual hard drives.  No USB in the sytem, bar my web cam.

---

### Post by freebird54 on 2007-04-29
You might want a look at this thread - some people seem to have been fixing it by using OpenDNS - or making other DNS changes.    [http://ubuntuforums.org/showthread.php?p=2434983](http://ubuntuforums.org/showthread.php?p=2434983)

---

### Post by Grumblebum on 2007-04-29
Thanks.  Have to go for the moment.  Will check this and report back.

---

### Post by Grumblebum on 2007-05-04
Took a while to get back.
Have changed the DNS servers in my router to the openDNS servers, rather than my ISP.  Browser still works fine.  Been to the openDNS site.  All their tests work fine.
Put the nameservers at the top of my resolve.conf file.  So far it hasn't been overwritten.  Did the prepend statement in the dhclient.conf file.  Incidentally, the whole file was an example with every line commented, so I merely uncommented the prepend line and added the openDNS statement.  Thought this would be the safest option as browsing etc seemed to be working OK with the rest of the file commented.
Opened up evolution email.  It will now receive, but not send.
Any further assistance greatly appreciated.
BTW, trying to RAS into work, which is a Microsoft/Citrix environment, system says it wants to launch a 'launch.ica' file, but it won't happen because there is not application associated with it.  Any ideas?

---

### Post by freebird54 on 2007-05-04
Probably, if you can now receive but not send, it will be a minor misconfiguration in the options.  Although 'Login' is probably the most common type - it is not universal.  Double check all your entries in 'Sending Email'  and if you can compare them with settings on another machine, it can only help...

No idea on the other problem - never heard of a 'ica' file on any system.  You may have to start a separate thread on that..

---

### Post by Grumblebum on 2007-05-04
Can't find anything wrong with my email options.  Still. I'm learning a lot with all the trouble shooting.  Guess it'll pay of in the long run......

I'm in Windows now.  Maybe when I log back into Ubuntu....

Thanks for all your help. by the way.  I'll report back when I'm in Linux.

---

### Post by Grumblebum on 2007-05-04
Got it!  I tried to log into the SMTP server using an email alias, rather than my ISP login details.

Now, if I can only get updates working...........

---

### Post by Don Cox on 2007-05-07
>Opened up evolution email. It will now receive, but not send.

Before I gave up on 'evolution' I would have changed the outgoing smtp port from the default 25 to 587 and given that a try. There is at least one post somewhere on the forum that suggests 'evolution' does not possess this facility.

---

### Post by Grumblebum on 2007-05-08
All is fixed now, including updates.  Thanks to those who offered assistance.  Now, over to the security threads..........

---

