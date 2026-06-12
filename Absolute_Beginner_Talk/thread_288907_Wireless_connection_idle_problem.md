---
title: "Wireless connection idle problem"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-30
Some times when I boot up, my wireless connection refuses to connect to my internet, and stays idle. The only way I have found how to fix this problem is restarting till my NIC connects to my wireless internet. Does anyone know how to fix this problem?

Cheers

---

### Post by blissfulpenguin on 2006-10-30
Well, I'm a newbie at replying to posts, so tell me if this is not helpful.  It sounds like you might be relying on the boot scripts to initialize your wireless card.  Alternatively to rebooting, you could open a terminal and with root privileges run an "init" script to do just what you are doing by rebooting.  For instance:

[COLOR="Indigo"]sudo su
(PW)
/etc/init.d/networking restart
[/COLOR]
But this solves very little.  All it does is keep you from having to reboot.  Try opening the /etc/network/interfaces file with your favorite text editor.  Then, verify that your wireless card is in there.  More than likely, you'll want to enable wlan0.  It should look something like this:

[COLOR="Indigo"]auto wlan0
iface wlan0 inet dhcp[/COLOR]

Once you have verified the presence of this entry, save the file (you might want to comment out all other interfaces if this is a laptop - this will turn off all other net devices and give wlan0 exclusive dhcp access).  Then, restart networking as in the first command listed up there at the top of this post ([COLOR="Indigo"]/etc/init.d/networking[/COLOR]).

If this alone doesn't start your NIC, you can try forcing it with:

[COLOR="Indigo"]ifup wlan0[/COLOR]

Alternatively, if you run the command "ifconfig," and nothing shows up, you can configure your card this way:

[COLOR="Indigo"]ifconfig wlan0[/COLOR] (inet?)

If that doesn't work, check that last option on the ifconfig man page:

[COLOR="Indigo"]man ifconfig
[/COLOR]
If you've tried all this and nothing works, I hope I at least helped to familiarize you with the command line controls for network cards.  Please do reply.  :p 

Josh

---

### Post by spamzilla on 2006-10-30
Ok thanks for replying Josh. As of now, my wireless internet is working. Next time it doesn't work when I reboot my laptop, I'll try what you have suggested. (I can't now as I am busy converting loads of files to .mp3!)

Thanks for replying :)

---

### Post by blissfulpenguin on 2006-10-30
sure thing.  hope it helps.

:)

---

### Post by blissfulpenguin on 2006-10-30
Hey, BTW, I am not a wireless person, but I just came across the command iwconfig .
It seems to be a more specific command-line wireless configuration tool.  Try the man pages on that if the ifconfig command isn't helpful.

:)

---

### Post by spamzilla on 2006-10-31
Hey Josh

When I turned on my laptop, as usual my NIC wouldn't connect to the internet. I tried what you suggested, but it didn't work :( When I put most of those commands into the Terminal, I got this error back a lot:

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

I got this message even though it were listed here /etc/network/interfaces.

---

### Post by spamzilla on 2006-10-31
Hmmm odd. I just entered

sudo su
/etc/init.d/networking restart

into terminal after turning on my laptop, and the NIC connected to the internet! I'll keep you guy posted on whether this fixes my problem or not.

---

### Post by pastorjay on 2006-11-09
> **spamzilla said:**
> Hmmm odd. I just entered

sudo su
/etc/init.d/networking restart

into terminal after turning on my laptop, and the NIC connected to the internet! I'll keep you guy posted on whether this fixes my problem or not.

Any progress on this?

---

### Post by spamzilla on 2006-11-10
Sadly not. My laptop either will, or will not connect to the internet. My bro who uses windows on his laptop has no connection problems, and I am sadly thinking about going back to XP of i cannot fix this problem soon.

---

