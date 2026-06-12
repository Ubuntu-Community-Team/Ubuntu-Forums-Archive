---
title: "Tor"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by poordamnedfool on 2007-03-18
how do you know if TOR is running in the background?

---

### Post by g3k0 on 2007-03-18
Not sure what tor is but when I look to see what processes are  on to kill it I type ps -aux

---

### Post by poordamnedfool on 2007-03-18
ok i did that and i didnt see TOR running, is there something that i am susposed to do to set it up?

---

### Post by poordamnedfool on 2007-03-18
Never mind i guess i didnt install it right im gonna reinstall it and see what happens

---

### Post by poordamnedfool on 2007-03-18
ok so i reinstalled everything and i still cant get tor running here is what i get when i try running the program

jqaskwig@poordamnedfool:~$ tor
Mar 18 23:51:36.921 [notice] Tor v0.1.1.23. This is experimental software. Do not rely on it for strong anonymity.
Mar 18 23:51:36.923 [notice] Initialized libevent version 1.1a using method epoll. Good.
Mar 18 23:51:36.924 [warn] /var/lib/tor is not owned by this user (jqaskwig, 1000) but by debian-tor (109). Perhaps you are running Tor as the wrong user?
Mar 18 23:51:36.924 [warn] Failed to parse/validate config: Couldn't access/create private data directory "/var/lib/tor"
Mar 18 23:51:36.924 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

any ideas?

---

### Post by ramjet_1953 on 2007-03-18
If you just install tor and privoxy from the Synaptic repositories and then go to the tor website: [http://tor.eff.org/](http://tor.eff.org/) and then click on:

[COLOR="Red"] Docs>Installing tor on Linux/BSD/Unix.[/COLOR]

Just follow the instructions from the point where you have already installed tor and privoxy. ie ignore all of the install info for tor and privoxy, as you have already installed both applications, using Synaptic.

**IMPORTANT: This part is crucial.**

Once you've installed Privoxy (either from package or from source), you will need to configure Privoxy to use Tor. Open Privoxy's "config" file (look in /etc/privoxy/ or /usr/local/etc/) and add the line 
[COLOR="Red"]forward-socks4a / 127.0.0.1:9050 .[/COLOR]
to the top of the config file. Don't forget to add the dot at the end. 

Privoxy keeps a log file of everything passed through it. In order to stop this you will need to comment out three lines by inserting a # before the line. The three lines are:
[COLOR="Red"]logfile logfile[/COLOR]
and the line 
[COLOR="Red"]jarfile jarfile[/COLOR]
and (on some systems) the line 
[COLOR="Red"]debug 1 # show each GET/POST/CONNECT request
[/COLOR]
You'll need to restart Privoxy for the changes to take effect.

Install the tor add-on for Firefox and you will get a button on the bottom toolbar of Firefox that allows you to toggle tor on and off.

Remember, when you use proxys, surfing can be painfully slow, at times.

Regards,
Roger :cool:

---

