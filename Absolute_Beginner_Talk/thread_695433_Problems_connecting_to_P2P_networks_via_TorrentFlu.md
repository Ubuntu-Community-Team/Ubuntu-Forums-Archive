---
title: "Problems connecting to P2P networks via TorrentFlux and aMule"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by lafaki on 2008-02-13
Hi,

I am not able to connect to any P2P networks using TorrentFlux and aMule.
Let's take it one be one.

**TorrentFlux**
When I first installed it, I could connect to peers and managed to download almost 3 GB of shared files in less than a day with very god speeds. Suddenly when I am trying now to start a new Torrent the very same way I was doing it before, it doesn't connect any more. It keeps on saying 

"Connecting to peers". 

Any ideas?  

**aMule**
This program never connected to the network. I managed to get the server list but when aMule GUI starts it throws the below error and doesn't open any port (TCP or UDP) for connecting to a server:

"MuleUDPSocket: Failed to create valid Server UDP-Socket"

Any ideas here as well??

The modem router is properly configured for port forwarding for both TorrentFlux and aMule. aMule ports were also tested successfully via an aMule internet site. To my knowledge, there is no firewall turned on the system (I get this info from Webmin).

Your help will more than appreciated!!

Thanks,
Akis

---

### Post by Hallvor on 2008-02-13
For aMule: Try adding a few servers manually, and you should be able to connect.

[http://www.gruk.org/list.php](http://www.gruk.org/list.php)

---

### Post by lafaki on 2008-02-13
Thanks, I will try.

After working a bit more with TorrentFlux, it seems that it can connect again to the network. I believe that the initial connectivity problem might be related to lack of available seeds.

So now I need to focus on aMule. I will follow the below link and try to add some servers manually. The question is if the error message I get from aMule at startup (failed to open UDP socket...) is related to the server list or not?!?

Btw, are there any aMule servers that you recommend and that you could share with me?

In addition to the above problem with aMule, on amuleweb the server list is blank. Maybe the amule daemon and amuleweb need a restart; but if not, what could be the problem? 

Finally, aMule seems not to keep my preferences between different sessions, i.e. when I activate the Web GUI, close the aMule GUI and open it again the Web GUI is deactivated again. Could it be a file read/write access issue?

Thanks!
Akis

---

### Post by Hallvor on 2008-02-13
> **lafaki said:**
> Thanks, I will try.

After working a bit more with TorrentFlux, it seems that it can connect again to the network. I believe that the initial connectivity problem might be related to lack of available seeds.

So now I need to focus on aMule. I will follow the below link and try to add some servers manually. The question is if the error message I get from aMule at startup (failed to open UDP socket...) is related to the server list or not?!?

Btw, are there any aMule servers that you recommend and that you could share with me?

In addition to the above problem with aMule, on amuleweb the server list is blank. Maybe the amule daemon and amuleweb need a restart; but if not, what could be the problem? 

Finally, aMule seems not to keep my preferences between different sessions, i.e. when I activate the Web GUI, close the aMule GUI and open it again the Web GUI is deactivated again. Could it be a file read/write access issue?

Thanks!
Akis

1. Failed to open UDP-socket suggests to me that a different application uses the same port, though I might be wrong. Do you use the same port for torrents?

2. Any large non-fake server will do. I think the largest Razorback servers and Saugstube are safe. You only need servers for bootstrapping aMule, You will get more results from searches in KAD once bootstrapped.

3. Are the settings saved when you restart the aMule daemon, and not just the gui?

---

### Post by lafaki on 2008-02-14
Now aMule is working, thanks for your help!

What I did was to delete all existing servers and add new ones by downloading the server.met file from the below given URL: 

[http://www.gruk.org/list.php](http://www.gruk.org/list.php)

Now I can connect to servers (wigh High ID), search and initiate download of files without any problems!

Regarding the amuleweb, I restarted it and now it is in synch with my aMule GUI. Server list, connection status, download transfers, search functions are all working ok on the web. The only strange thing with amuleweb is that it can't be accessed by Firefox, only by Internet Explorer; therefore I cannot access it from my Ubuntu GNOME desktop as I have only Firefox and the IE Tab plugin is not available for the Linux version of Firefox :-(

I also realize that either amule daemon can be running or the amule GUI.

---

### Post by pemur1 on 2008-02-18
Instead of making a new thread about amule, I figured I'd post here.

I installed amule today and thought I'd set up the port forwarding correctly for my router, but apparently I hadn't. I'm always getting a low id. I've set up a static ip in emule, but since I've switched to Ubuntu, I haven't been able to. Any assistance would be greatly appreciated.

---

### Post by Hallvor on 2008-02-19
If everything is working in Windows, the problem is probably IPtables (firewall) in Ubuntu.

You can easily open the aMule ports using the command line. Check my signature, copy and paste the relevant commands.

OR you can install a GUI for IPtables called Firestarter and open the ports from there.

The fastest and easiest IMHO is using the command line.

---

### Post by hyper_ch on 2008-02-19
by default iptables does not prevent any connection. So no ports need to be opened.

---

### Post by Hallvor on 2008-02-19
> **hyper_ch said:**
> by default iptables does not prevent any connection. So no ports need to be opened.

You will have to open them to get a high ID in aMule. Don`t ask me why.

---

### Post by hyper_ch on 2008-02-19
The ports are open by default.

---

### Post by Hallvor on 2008-02-19
> **hyper_ch said:**
> The ports are open by default.

I know. But try to get a high ID in aMule without "opening" the ports. By default, aMule will get a low id (firewalled status), despite all ports being open. It does not make sense to me.

---

### Post by pemur1 on 2008-02-19
Won't I need to set up a static IP for my router also?

After opening the ports, I'm still getting a low ID. I have Firestarter installed, but have no clue how to get that set up either.

---

### Post by hyper_ch on 2008-02-20
I don't use aMule so I dunno about the high/low ID

---

