---
title: "Accessing my local server from far away..."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2008-02-06
Hi all, I'm running Amrok and have a web interface script installed which brodcast and controls my current playlist. The address I type in to access this is [http://localhost:4774/](http://localhost:4774/). My question is, how would I access this outside of my local network, ie: from work. 

Tips broken down into baby steps are greatly appreciated

---

### Post by monkey56657 on 2008-02-06
If you have a router then you will need to forward port 4774 to your PC IP. 

THEN OR OTHERWISE:

Go to [http://www.whatsmyip.org/](http://www.whatsmyip.org/)

Copy and paste the IP address into ure address bar then follow it with ":4774" without quotes. 

This is the URL you must now use for accessing at work so save it to a memory stick in a text file or just write it down so you will remember.

---

### Post by Dr Small on 2008-02-06
Open port 4774 on your firewall, with Firestarter, and then have someone test it for you.

If you are behind a router, you will need to forward port 4774 to your LAN IP

---

### Post by lswest on 2008-02-06
well...you'd have to set up a server on your computer, and, ideally, set up your network so that your external IP never changed (this can be done with things such as dyndns).  Otherwise you can try just connecting to your PC from outside the network using the external IP (you can find out what it is by going to [http://www.whatismyip.com]("http://www.whatismyip.com")  if that works, then you just need to set up a dns server to keep your IP bound to a url.  otherwise you'll need to set up your firewall to allow connections through.  Depending on if you can connect now or not will affect where i can start to explain.  So post back after you've tried, and keep in mind, your external IP will change, so it's best if you check the IP, write it down, then go over to a neighbours or friends house and try...depends how long it takes you to get to work i guess.

---

### Post by woodsonoversoul on 2008-02-06
well I tried to open the ports with firestarted and now it won't load at all. Never mind...:(

---

### Post by Whiffle on 2008-02-06
Hmm, you shouldn't have to mess with firestarter unless you had setup a firewall on your computer.  

Here it is in easy steps:
1)  Go to your router, and setup a static IP address for your computer that you want as a server.  Your routers manual should tell you how to do this.
2)Also on your router, forward a port (4774 for example), to port 4774 on the computer that has the server on it, using the IP address we assigned to it in step 1.
3) You should be able to access your server from anywhere by going to
[http://youripaddress:4774](http://youripaddress:4774) 

4) Optional step:  Setup a dynamic DNS account on your router so you don't have to write down your IP address

---

