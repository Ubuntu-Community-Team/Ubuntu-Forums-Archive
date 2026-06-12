---
title: "How to open UDP port for Ktorrent and make it work"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by DenOK on 2007-02-11
I have Kubuntu 6.06

Ktorrent 2.1 always gives me Tracker Status: Invalid response  :( 

Port settings are
Port: 6881
UDP Tracker Port: 4444

So, I've checked for open ports here  [http://www.utorrent.com/testport.php?port=6881](http://www.utorrent.com/testport.php?port=6881) and - OK! Port 6881 is open and accepting connections.
But,
[http://www.utorrent.com/testport.php?port=4444](http://www.utorrent.com/testport.php?port=4444) - Error! Port 4444 does not appear to be open.  :( 

How do I open that port? Also, please, give me some advices on how I can manage ports, monitor network for activity, security.

Obviously, it's simple question, but Google didn't help, or maybe there's somth wrong with me? :)

---

### Post by RomeReactor on 2007-02-11
Hi. Search Adept for **Firestarter** if you don't have it; it's a really easy-to-manage Firewall.

---

### Post by DenOK on 2007-02-11
>>> Search Adept for Firestarter 

Tnanks, but I'm stuck, already installed Firestarter, but it didn't help, I mean it is so simple, maybe even too simple :)

I've tried and added rules to open outbound/inbound 4444 (and many other variants), no luck, only Amarok stopped playing radio stream :mad: 

I forgot to mention: I have direct ip from ISP assigned by DHCP.

---

### Post by DenOK on 2007-02-11
Also, there's one question about Firestarter or other firewall like that: Do they need to be run in background (deamon) all the time? Like in sys tray?

You see, all I need is to manage ports, and don't want to have another background proccess living in the system.

---

### Post by RomeReactor on 2007-02-11
Maybe the issue is with your router not forwarding the ports? Do you know how to access the configuration page for it? On my 2wire box all i have to do is type **homeportal** on Firefox and it takes me inside the router to change settings. Check your router's manual or go to your router vendor's page and see if they can tell you how to gain access to the configuration. Sorry i can't be of more assistance at the moment; i'm off to bed. Post back how it goes and we'll try to sort it out.

---

### Post by DenOK on 2007-02-11
Thank you for trying to help,

But I don't have any router (and I'm *not* behind any kind of server/firewall/proxy),  also I'm pretty sure that it is Linux ports config problem, because I didn't get into internet connection problems of any kind with my ISP when using Win.

---

### Post by PurplePenguin on 2007-02-11
If you can manually select a different nonstandard port (just think of a random number between, say, 40000 and 50000), you'll probably have better luck.  It complains about 4444?  OK, change it to 44444.  Just don't forget to put this number into both your firewall and your torrent client.

If your modem is ADSL, it could actually be a modem/firewall.  Bell Sympatico in Canada pulls this trick so pretty much all of your ports are constantly closed - it doesn't matter which ports you open in your system's firewall, because the modem is blocking all your ports anyway.  There are ways around this for people who like googling. :D

Firestarter isn't a firewall, it's just a frontend.  So, no, it doesn't need to run all the time.  Start it, make your changes, close it, and your firewall is still running.  Make sure you keep it open while playing with your torrent client, though, and see if it pops up any events on ports that you think should be open.  This will tell you immediately if your firewall is blocking a port, letting you right-click and allow the service to run on the desired port.

---

### Post by DenOK on 2007-02-11
Oh, me...

It *appears* that almost all ports that I can think of are closed, obviously I have tried playing with Firestarter a lot, still no luck. Eg.: 8000 or 44444 are closed by default then I change firewall rules (inboun/outbound, right?) to open them, still Tracker Status: Invalid response

On windows uTorrent or BitComet are working just *fine*. And I'm pretty sure that my modem *isn't* blocking anything.

So, openning ports in firewall didn't help (they appeared open according to Firestarter, but *closed* according to online test, and Ktorrent still complaints), anyway thank you for covering about frontend, it is clear for me now :)

---

### Post by PurplePenguin on 2007-02-11
Hmmm... how about temporarily shutting the firewall off?  Shouldn't hurt for a few seconds while you try connecting again.  

Another thing - are you absolutely sure that there's no problem with the torrent / tracker?

Have you tried using a different program?  I know that ktorrent's got a PnP mode, although I never used it since it seemed a bit buggy to me.  Why not try installing Azureus just as a comparison test?  It's got a good little config utility that will tell you for sure if the port you want is closed or not...

---

### Post by Norfolk 'n' Good on 2007-02-11
Try this...  [http://portforward.com/default.htm](http://portforward.com/default.htm)  I sorted my port forwarding out in no time.  Also, I found it useful to shut down Firestarter while in Amule.

---

