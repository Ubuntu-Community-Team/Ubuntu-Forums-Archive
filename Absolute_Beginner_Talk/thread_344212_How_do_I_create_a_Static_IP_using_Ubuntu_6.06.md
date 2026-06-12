---
title: "How do I create a Static IP using Ubuntu 6.06?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Galactic Jack on 2007-01-22
I have been having a bit of trouble installing Azureus on my computer and I've nailed it down to the fact that I do not have a static IP set up with my router. The problem further persists with the fact that when I go to portforward.com, they don'th ave any linux installation guides. Bastards.

Anyways I was wondering if anyone out there could give me a hand with this.

My router is a WBR-1310 by D-Link and I and running Ubuntu 6.06.

GJ

---

### Post by annda on 2007-01-22
if you are sure your problem is static IP then [try this]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

and the GUI way is [here]("http://users.bigpond.net.au/hermanzone/p11.htm#Set_a_Static_IP_address")

hope it helps

---

### Post by Sutekh on 2007-01-22
Hey.  If you are using Ubuntu (GNOME), then you can set a static IP through the Networking Entry in the System -> Administration menu.  

From there look at the properties for your main connection, and in the drop down box for the configuration, you can choose Static IP.

When you start Ubuntu again you should have the new IP address.  I think you can avoid the restart by bringing down and restarting the connection, but restarting may just be easier.

Then you can go to your Router configuration, and fix the port forwarding there, good luck!

Edit: Thanks annda for the great link!

---

### Post by Galactic Jack on 2007-01-23
The both of you have helped a great deal. I now have managed to get past the DHT Initializating stage on my Azureus, which is one out of two green smileys. I have been looking around and realized that I needed Java to be installed [which I'm having a bit of trouble with at the moment as well because most of the guides are out of date or partially incomplete - ie. they make assumptions about where files are placed before you execute them]

Nonetheless, I THINK I have J2SE installed, which seems to help but from what the guides say I need J2RE or something along those lines. But with it, the Static IP works "better" than before and I can actually see about half a million or so users for about 30 seconds before my NAT becomes firewalled. So I'm still in the blue on a bit of this.

But for now, before I take a sledgehammer and a blowtorch to this router, I'm going to see if you guys can wash this around in your mouths a bit more.

Thanks again for all the help!

---

### Post by Sutekh on 2007-01-23
Glad you got something happening there.  And if you have Azureus running, the you must have Java installed properly.

The only thing you need to do is open the port for incoming TCP connections on your PC's side.

You can do this through the command *iptables* but you may prefer (as I do) to do this with the application *Firestarter*.

If you don't already have Firestarter installed, then you can install it using the following command.
```
sudo aptitude install firestarter
```Once that's installed and FIrestarter is up you can then open it and go to the *Policy* tab and select *Inbound traffic policy *from the drop down box.

Then right-click inside the bottom section (Allow Service | Port | For ) and choose *Add rule*.

Then you can enter the name of the program (Azureus) and the port(s) you want to open.  Finally click *Apply Policy* and you should be done.

If you are still stuck, try searching the forums for more info (in case I left out something).  There are *many* questions about using Azureus and Firestarter.

---

### Post by bionnaki on 2007-01-23
for future reference, you set your network information (static IP for example) in /etc/network/interfaces 

usually you'd add 

> 
iface xxx inet static 
        address 192.168.1.xx
        netmask 255.255.xxx.x
        gateway 192.168.x.x


to the beginning of the file (and filling in your own info) replacing the dhcp entry.
the xxx in the 1st line would be the alias...eth0, ra0, wlan0, whatever

no need for firestarter when you're behind a router.

---

### Post by Sutekh on 2007-01-24
> **bionnaki said:**
> 
no need for firestarter when you're behind a router.

True and I never use it.  I just don't know how to open a port otherwise.

---

### Post by Galactic Jack on 2007-04-04
I just thought I might post this saying that I STILL haven't gotten Azureus to work, yet I can STILL download at a 2.2kb/s avg, as my uploading never works.

Any ideas still?

---

### Post by sirhalos on 2007-04-04
Please login to your router and make sure Port Forwarding is activated to forward the Port Numbers that Azerous uses to your IP address. That will speed up your connect. Please check Azerous's website for what Port Numbers need to be opened up.

---

### Post by Galactic Jack on 2007-04-08
I tried forwarding ports 6881-6889 along with a certain unassigned port range. Now I consistently get green smileys, but I'm limited to speeds between 6 and 15 kb/s. Mind you, my Frostwire goes through the roof with speeds averaging 70-100 kb/s

Any suggestions on getting it higher than that or do you suppose it's now up to my ISP throttling my connection? If so, are there any Canadian ISPs that DON'T throttle bandwidth?

GJ

---

### Post by h2gofast on 2007-04-08
Some isps will packet shape which is not easy to beat and tends to slow down all bittorent traffic, some will just throttle back certain port numbers often used by bittorrent clients, which is easier to beat.

In azureus there is a setting for selecting which port number to use, also in your router's configuration there is a setting for selecting which port numbers to forward and where to forward them to.
Decide on a port number, then get the ip address your router assigned to the computer running azureus.
In azureus enter the port number you chose.
In your router's configuration forward the port number you chose, and forward it to the ip address of the computer running azureus.
Enjoy.
Remember, daycare says sharing is caring.

---

### Post by brennydoogles on 2007-04-08
> **Sutekh said:**
> Hey.  If you are using Ubuntu (GNOME), then you can set a static IP through the Networking Entry in the System -> Administration menu.  

From there look at the properties for your main connection, and in the drop down box for the configuration, you can choose Static IP.

When you start Ubuntu again you should have the new IP address.  I think you can avoid the restart by bringing down and restarting the connection, but restarting may just be easier.

Then you can go to your Router configuration, and fix the port forwarding there, good luck!

Edit: Thanks annda for the great link!

If I understand you correctly, all you have to do is choose Static IP and hit ok, and then Ubuntu will fill in the rest?? That doesn't seem to make much sense, so I will assume I misunderstood what you said and ask for clarification.

---

### Post by Galactic Jack on 2007-04-15
Ok, I think I have a good hang of it now.

After constant tweaking and fiddling, this is what I've gathered:

1) Set up a Static IP Address. 

To do this in Dapper, go to system > administration > networking and click on "Ethernet Connection" then go to "Properties". From there select Static IP from the configuration and enter the information you wish to use in your configuration. The rest will be set up by ubuntu. [*NOTE: This is FAR easier to do than going through the terminals]

2) Make sure you have Java and Firestarter installed.

Just DL the newest versions through terminal

3) Forward 6881-6889 to either "Any" port or TCP/UDP [it means the same thing]

On my router this is under the "Advanced" tab. All you should have to do is insert your local ip address [looks like 192.168.0.xxx where xxx is the sequence you are in for connection. Example: First connected IP is 101, second is 102, etc.] This will be the same address as your Static IP.

4) Find a range of ports that are unassignedand forward them through your router.

Try 2153-2158. Follow the directions from step 3 except put this range in instead of 6881-6889 and do it twice, once for udp and once for tcp. [the reason why I say to do it twice is because my router's a tit. [If you can apply it with TCP/UDP or ANY, then all the power to you]

4) Make sure you have the ports forwarded in Firestarted, then turn the firewall off while still having it run in the background 

This is key! I know it doesn't make any sense but I haven't gotten it to work anyway else. Again, to anyone who can get it working without this part, all the power to you. Keep in mind this includes both ranges, 6881-6889 AND 2153-2158, or whatever other range you decide to use

5) When configuring Azureus, follow these steps

    a) Choose three ports from that range. We will name them port A, port B, and port C
    b) Go to Tools > Options and click "Connections". Under "Incoming TCP/UDP listen port", apply port A
    c) Hit the triangle left of Connections and go to "Advanced Network Settings"
    d) Put your Static IP Address in "Bind to local IP address" and put port B in "Brind to local port"
    e) Hit the triangle left of Plugins and go to UPnP and make sure this is enabled
    f) Lastly, right beneath UPnP is "Distributed DB", in UDP port for the database, apply port C

And that's it!

---

