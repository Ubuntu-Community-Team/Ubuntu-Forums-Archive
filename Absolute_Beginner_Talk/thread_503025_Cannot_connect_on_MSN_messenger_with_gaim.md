---
title: "Cannot connect on MSN messenger with gaim"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Pandiani on 2007-07-17
Hello folks,
I'm having problem connecting to MSN network. I'm using gaim messenger on ubuntu 7.04. Really don't know what could be problem. Ubunutu machine have Internet connection through windows Xp machine and Firefox works OK (I'm making this post from Ubuntu machine).
I'm constantly receiving an error message: "Connection error from Notification server: Reading error".
Can you give me any advice?
Thanks...

---

### Post by Sandlst on 2007-07-17
I would go ahead and upgrade to Pidgin (the new name for gaim) in case this is simply a bug.  To do this, first you have to uninstall gaim and gaim-data through synaptic or the terminal (applications/accessories/terminal).  In case you don't know, the command is ```
sudo apt-get remove gaim gaim-data
```Then, go to [this]("http://www.getdeb.net/release.php?id=1045") site and downloathisd the Pidgin-Data package first (just leave it at the default Open With instead of save as) then after that is installed download and install Pidgin the same way.  Good luck, post back if you need more help.

---

### Post by zero244 on 2007-07-17
MS changed things with version 8 of msn. I had the same problem with Gaim.........I installed Kopete and it works fine with MSN and Yahoo.

---

### Post by Pandiani on 2007-07-17
Hmm, it's really strange. About 6 months ago, I had ubuntu 6.06 installed and gaim worked perfectly well with MSN. 
Is there any way to test my ports to make sure firewall is not problem since this computer is connected to the Internet through home LAN?

---

### Post by Sondre Haugen on 2007-07-18
Got one laptop at home and one PC at work. Both are running 7.04.
The first one was installed 3 days ago and the second 1 day ago.

On the laptop, MSN in Gaim works perfekt. On the PC at work, MSN in Gaim says: Writing error. I dont have the  debug log here, but nothing interesting there.

So what I think is that the error comes from a library or extra package installed that conflicts with gaims MSN support. On the computer where Gaim works with MSN, I have not installed any new software after ubuntu was up and running. On the other PC, i have installed a lot of extra software. (all working fine by the way)

On both PC it works fine with jabber, ICQ etc.

A friend of mine has setup a jabberserver at home. On the computer where MSN is not working I can make it work by using a jabber acount to that server and let his server "route" it to MSN from there. Works great but I'd realy like MSN protocol to work in Gaim directly.

So Microsoft has not changed the protocol that affects Gaims support for MSN.

---

### Post by zero244 on 2007-07-20
Thanks thats good to know I was wondering why msn would not work with Gaim.
I couldnt get amsn to work either, Kopete did work so I went with that.

---

### Post by nutz on 2007-07-20
Use your email address for your user name instead of the actual user name.

---

### Post by tomm3h on 2007-09-04
Hi guys, bit of a thread revival, but this is driving me round the bend.

I'm getting the 'writing error' when connecting to either of my MSN accounts. I'm not using a proxy, I can't connect to any other service (AIM, Y!, ICQ, etc.), and I even get the *exact* same problems with pidgin under my Windows install (dual boot on the same physical array.)

It only started when I noticed Windows had magically incremented my system time by 1hour.

I have **no** idea what is going wrong. I've tried using NTP in both Windows AND Ubuntu (via the CLI and from Ubuntu's administration panel for time/date settings, for the latter), and I've even tried resetting my CMOS in an attempt to keep my system clock as it was (disabling NTP), but this failed miserably as soon as I booted into Ubuntu - it decided that because I'm in British Summer Time at the moment, my system time needed adjusting.

Et voila; messed-up again.

How can something *so* simple screw-up Pidgin altogether, across two operating systems? The client doesn't even try to handshake with the server - it just bombs out, and there's no shell output either, no logged error messages anywhere.

I've tried re-installing Pidgin on both Windows *and* Ubuntu, and the problem still persists with Gaim!

Please, anyone .. What the heck is going on :(

---

### Post by Hasen_A on 2007-10-12
I've had the following problem. I am sitting in a univerity dorm where everything worked perfectly. Then they shut down the wireless LAN and when it was set up again, a lot of stuff no longer works: mail uploading smtp, and MSN messanger can no longer connect.

I haven't changed anything in the settings and believe that the ports are closed. I've checked them with the console and on several internet sites. Now the question is whether i can redirect gaim to use another port for MSN instead of port 1863, since that worked for the icq port, which i changed to 443. Is there a specific port which i need to use?

THanks beforehand.
andy

---

