---
title: "[SOLVED] recommend a firewall"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-16
hi can someone recommend a firewall for ubuntu please.
I would much prefere a gui but I wont cry if it aint got one.

---

### Post by por100pre1 on 2007-10-16
Firestarter. Copy, paste and ENTER this in a "terminal window":

```
sudo apt-get install firestarter
```

You'll find it in System> Administration. Run it, configure it, and close it. **No need to keep it running, it configures the firewall, it is NOT the firewall itself.** [Here's]("http://www.fs-security.com/docs/interface.php") how to use it. Hope this helps. :)

---

### Post by svalding on 2007-10-16
Sonicwall kicks ***. It's got a web-based front end so you can manage it from anywhere if you wish.

---

### Post by hyper_ch on 2007-10-16
you already have a well configured firewall installed --> iptables

firestarter is just a graphical front-end for it for configuration (which I haven't needed so far...)

---

### Post by Dr Small on 2007-10-16
> **por100pre1 said:**
> Firestarter. Copy, paste and ENTER this in a "terminal window":

```
sudo apt-get install firestarter
```

You'll find it in System> Administration. Run it, configure it, and close it. **No need to keep it running, it configures the firewall, it is NOT the firewall itself.** [Here's]("http://www.fs-security.com/docs/interface.php") how to use it. Hope this helps. :)
+1
Firestarter is a great utility. I use it :D

Dr Small

---

### Post by scrooge_74 on 2007-10-16
You can also use FIREHOL from the command line

---

### Post by Tlon on 2007-10-16
Shorewall, if you don't mind sacrificing the GUI in exchange for quality.

Or you could just get a Cisco ASA 5505.  Then you get GUI AND quality.  If you don't mind dropping $400.

---

### Post by Orbital75 on 2007-10-16
Just wanted to let you know........ 

Ubuntu already come pre-configured with a FireWall called  " iptables "
Iptables is configured with NO Ports open by default. 

Fire Starter is a GUI Front End to iptables, which means that it just
edits the iptables.

In other words Ubuntu is not like WIndows, you don't need to have
Fire Starter start up durning boot, it is only an iptables editor. 

This is how Linux does things.......

So Install Fire Starter...... Let through what you need to...... Save.......Close Fire Starter.......  then your good to go.

Hope this helps...... I went through the same thing and someone helped me so I try to give back as much as I can.

---

### Post by Shin_Gouki2501 on 2007-10-16
well its nice that peopel like to pull out their "wisom" again , again and again.
Yes ubuntu coems with iptables and firestarter is a gui for that so nice not to be redundant...

I got a question regarding firestarter:
i'm reading this thread and unitl now i never had problems with ubuntu and ports. But i thought hey a gui for port managemetn why not.
So i isntall it then run the "wizard" stuck at the 3rd step:
Ur internet hardware interface can't be the same as ur "local" network interface..

What is this ? A bad joke? ^^ Why cant my "only" network itnerface my LAN and INTERNET network interface... i think i remove this firestarter thing...

---

### Post by pancakelizard on 2007-10-16
dd-wrt latest build is what i would highly recommend

---

### Post by scrooge_74 on 2007-10-16
> **Shin_Gouki2501 said:**
> well its nice that peopel like to pull out their "wisom" again , again and again.
Yes ubuntu coems with iptables and firestarter is a gui for that so nice not to be redundant...

I got a question regarding firestarter:
i'm reading this thread and unitl now i never had problems with ubuntu and ports. But i thought hey a gui for port managemetn why not.
So i isntall it then run the "wizard" stuck at the 3rd step:
Ur internet hardware interface can't be the same as ur "local" network interface..

What is this ? A bad joke? ^^ Why cant my "only" network itnerface my LAN and INTERNET network interface... i think i remove this firestarter thing...

You can use Firestarter to configure your PC as a router, it is asking if you have one ethernet for the  internet and another for your Lan, because it has to forward traffic.

But since you only have one, just tell it is for internet, if you need to run services inside your LAN like samba, then you need to configure Firestarter to open the specific ports

---

### Post by PsycoGeek on 2007-10-16
Here is what I recommend...

```
sudo hardware-get go to best buy or cc and buy a broadband router
make install connect-configure via web interface
sudo relax because you now have a hardware firewall
```

:lolflag:

[Wireless-N Broadband Router]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175236661542&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6154239789B02")
[Wireless-G Broadband Router]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1149562300349&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0034939789B01")
[EtherFast® Cable/DSL Firewall Router]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130276636538&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3653822279B03")

The last one is what I have, and I have never had any problems with it.

---

### Post by Orbital75 on 2007-10-16
True...... Having a separate hardware based Firewall is far superior.

---

### Post by PsycoGeek on 2007-10-16
> **Orbital75 said:**
> True...... Having a separate hardware based Firewall is far superior.

Yes it is.  I have been running Linksys firewall routers since I got cable internet access and have logged a few attempts to access my network, but none have succeeded.

---

### Post by bodhi.zazen on 2007-10-16
> **Orbital75 said:**
> True...... Having a separate hardware based Firewall is far superior.

Is it still legal to directly connect to the internet without a router :shock:

I think bigmonmulgrew has gotten a few nice answers, to to keep the discussion under control :

The Ubuntu (Linux) firewall is called IP tables and is included with your Ubuntu installation.

The default settings are permissive (meaning they allow all traffic) and, if you are not running a server, you may feel this is adequate protection.

If you would like to configure your firewall the two options are to use a gui front end or write IP rules for yourself (there are various scripts on the web that will help with 

this).

The most popular gui tools are Firestarter and Guard dog (KDE). Keep in mind that these applications are not firewalls, but rather configuration tools. This is sometimes a 

source of confusion as the application should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) [i]without having 

to run firestarter/guarddog[/i]. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down 

firestarter/grauddog, and let IP tables do the rest :twisted:.

See these links for further information/how to use these tools :

[center][[color=red][Size=6]How to Firestarter[/size][/color]](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) - 

[[color=blue][size=6]How to Guard Dog (KDE)[/size][/color]](http://www.simonzone.com/software/guarddog/manual2/index.html)[/center]

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

