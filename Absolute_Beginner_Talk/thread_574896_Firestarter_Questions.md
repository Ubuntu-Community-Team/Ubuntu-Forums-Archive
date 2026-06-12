---
title: "Firestarter Questions"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by PlasticWorm on 2007-10-13
Hello,

I've recently went back to ubuntu again. I've been using the Firestarter GUI, and while trying to get a something to work, I restarted X. During so, it said Firestarted Failed to load, however, I went back to the walk through and this time did everything default. I restarted X once more (still working on the problem), but this time it said to load.

The GUI still doesn't show up at start up, and I still have to do this manually. Does this mean it mean its still work even when the GUI is not loaded? (Sorry for these n00bish questions, I'm just a bit worried.) Or have I not fixed the problem?


Thank you

---

### Post by fiskking on 2007-10-13
I installed mine a couple of weeks ago and it must be started manually through the  menu System/Adminstration/Firestarter.  If you see the Lightning bolt icon in the task bar, then you know it is running.

---

### Post by PlasticWorm on 2007-10-13
Yea, I start the GUI manually and get blocked connections (Lightning Bolt), just doubling checking.

Thanks.

---

### Post by American_Outcast on 2007-10-13
I use this to test my firewall. I seem to have a problem keeping my ICMP from changing back to default. I have to start the gui each time, uncheck and then check ICMP and it passes as true stealth with the link at the bottom of this reply.  Firestarter loads for me at startup without having to see the GUI. It took me a bit going from XP to get use to this.

[Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by bodhi.zazen on 2007-10-13
The Ubuntu (Linux) firewall is called IP tables and is included with your Ubuntu installation.

The default settings are permissive (meaning they allow all traffic) and, if you are not running a server, you may feel this is adequate protection.

If you would like to configure your firewall the two options are to use a gui front end or write IP rules for yourself (there are various scripts on the web that will help with this).

The most popular gui tools are Firestarter and Guard dog (KDE). Keep in mind that these applications are not firewalls, but rather configuration tools. This is sometimes a source of confusion as the application should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest :twisted:.

See these links for further information/how to use these tools :

[center][[color=red][Size=6]How to Firestarter[/size][/color]](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) - [[color=blue][size=6]How to Guard Dog (KDE)[/size][/color]](http://www.simonzone.com/software/guarddog/manual2/index.html)[/center]

Firestarter Home Page : [http://www.fs-security.com/](http://www.fs-security.com/)

**Default Firestarter Policies**:
> [list][*]New inbound connections from the Internet to the firewall or client hosts are blocked.
[*]The firewall host is freely allowed to establish new connections.
[*]All client hosts are allowed to establish new connections to the Internet, but not to the firewall host.
[*]Traffic from the Internet in response to connection requests from the firewall or client hosts is allowed back in through the firewall.[/list]

If you would like to learn more about IP tables, here are some starting points:

_**Iptables references_** :
[list][*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*][http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[*][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)[/list]

If you would like to learn more about basic Ubuntu security, please see this thread :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

If you would like to debate/discuss the use of firewall, please post here:

[ Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by PlasticWorm on 2007-10-13
I tried and apparently failed the solicited TCP packets and Ping reply but passed Unsolicited Packets. Only one port was not stealthed, but was closed, all others did not respond.

I'm still in the dark about all this.

Edit: Thank you bodhi, that was a bit helpful and I could understand some things :D

---

### Post by Nero_Flint on 2007-10-13
> I tried and apparently failed the solicited TCP packets and Ping reply but passed Unsolicited Packets.

In the firestarter GUI go into Edit ---> Preferences ---> ICMP filtering ---> Check the "Enable ICMP filtering" box and try the test again.

---

### Post by PlasticWorm on 2007-10-13
Tried that, no luck.

---

