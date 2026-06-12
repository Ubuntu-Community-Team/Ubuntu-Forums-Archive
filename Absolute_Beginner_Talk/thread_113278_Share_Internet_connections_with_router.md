---
title: "Share Internet connections with router"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-01-06
I have 2 computers running Windows XP and a 3rd one with Ubuntu Linux.  I just ordered a Linksys BEFSR41 router to share an internet connection for all 3 computers, I've just been been disconnecting and reconnection the cable from my broadband cable modem to access the internet on each of the computers.
My first goal is to set up the router with the 3 computers to share my internet connection(Windows XP shouldn't be a problem), then maybe setting up a LAN, which I'm totally new to.  Would someone please give me some simplified instructions on how to set up Ubuntu to share the internet connection?(or will Ubuntu automatically recognize the router IP, etc?).  I've read that I'd need install samba and smb.conf to allow communication between Windows and Ubuntu.  I've been reading posts in these forums and am reading the Ubuntu FAQ Guide, but it's getting a little confusing, and I was wondering if there was a simple step-by-step for the initial installation of my router for Ubuntu.  Learning Linux is quite a challenge, but it's fun and I definitely don't want to get in over my head too prematurely tweaking & reconfiguring.  Thanks to all the great posters for the invaluable assistance you're giving all the people new to Linux.

---

### Post by buckley on 2006-01-06
well, i have been using ubuntu for about... oh i would say 12 hours or so (lol) but when i installed it, it immediately recognized and assigned my IP, and without any further configuration, i was copying music from my laptop (XP) to my ubuntu drive without any problems.

i would think that it should recognize your connection.  if not i would just do an ifconfig /release and /renew

---

### Post by diggs on 2006-01-06
Best way to do it is to turn everything off, router, modem, all computers. plug everything in, starting with the modem, then router, then computers. it should all work. to acess your router's settings, open up a web browser, like internet explorer or firefox, then type in:
192.168.1.1

And that should give you acess to your router. if you are having issues, just call the manufacturer and get them to walk you through it. should be pretty easy though. you may have to clone mac addresses though, depending on how many computers your internet provider lets you have connected. to do that:(if it is a linksys)
click on the setup tab
click on the MAC address clone tab
click on the clone your PC's MAC button
all routers have this feature, just poke around and look for it.
and restart all the machines. that should work! at least it did for me.

Why do you have to clone the MAC addy? cuz that is the physical addy of your computer, and some IPs only allow 2 computers to be connected to an internet connection. Basically the IP sees the router as a seperate computer connecting to the system. that is why. Hope this made sense, this is how it was explained to me.

---

