---
title: "adding synchonize ntp to Xubuntu - how do I?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-08-13
Hi,
I'm trying to get my machine to synchronise its clock on boot.  When I was using (G)Ubuntu everything worked on boot.  In Xubuntu this doesn't seem to happen.
I installed BUM, no reference in there to Ntp, and I can't see that there's anyway to add a service (if that's what its called:-? )
I know that ntp is working since I can use the GUI to update the time, and run ntpd from the command line.
I have ntp-server in /etc/init.d, and the config file refers correctly to my chosen time servers.

I may also need to get it to work later than boot, for example how can I add sudo ntpd... to my autostarted apps - presumably you can't sudo a command in autostart?
I may need it to run later since my connection on this box is a wireless one, and it seems to take a bit of time to fire up, for example mounting shares at boot doesnn't work, I have to do it from terminal after login.  (Or is this a separate question altogether?)

I've been ploughing through the wiki, forum, man and google, but I'm now more confused than ever](*,) 

Thansk for any help...

---

### Post by damianubuntu on 2006-08-15
Anyone?
Still getting nowhere on my onw here!

---

### Post by lamego on 2006-08-15
NTP and all the required files/service are installed with:
```
sudo apt-get install ntp
```
If you don't have the server running you could add a manual sinchronization command.
Edit the file /etc/rc.local (this file is ran as root during startup).
And add a line prior to the "exit 0":
```
ntpdate your_ntp_server
```

---

### Post by damianubuntu on 2006-08-16
Thanks, works great.
I also put my mount.... command in there and that works fine too.  Are they any restrictions on what I put in that file, or can I put anything in that I want autostarted?

---

