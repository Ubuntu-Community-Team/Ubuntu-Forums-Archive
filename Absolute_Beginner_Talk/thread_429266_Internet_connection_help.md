---
title: "Internet connection help?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by seashoreone on 2007-05-01
Well I finally got ubunto uploaded and running on my old P3 computer and was wondering if anyone could give me some ideas on how to tap into my internet connection that is running on my other computer.

I have just started trying to figure this out and so far learned that it is more than simply hooking up an Ethernet card and cable between both computers.  I ran the XP wizard and couldn't get it to work on my ubuntu computer.

I know so little about networking computers that I barely know what to ask.  If anyone can help, I would appreciate it.

Thanks,
Mike

---

### Post by jiminycricket on 2007-05-01
You can use an app called Firestarter to share on or from Ubuntu, or [this]("http://www.kde-apps.org/content/show.php/KDE+Internet+share+wizard?content=53675").  From the [Microsoft ]("http://support.microsoft.com/kb/306126/")site, it appears that this is some of the info you need to input on Ubuntu if you use the XP computer as a host; however, you would substitute System->Administration->Networking instead of the XP network control applet:

> On the client computer
To connect to the Internet by using the shared connection, you must confirm the LAN adapter IP configuration, and then configure the client computer. To confirm the LAN adapter IP configuration, follow these steps:
1.	Log on to the client computer as Administrator or as Owner.
2.	Click Start, and then click Control Panel.
3.	Click Network and Internet Connections.
4.	Click Network Connections.
5.	Right-click Local Area Connection, and then click Properties.
6.	Click the General tab, click Internet Protocol (TCP/IP) in the This connection uses the following items list, and then click Properties.
7.	In the Internet Protocol (TCP/IP) Properties dialog box, click Obtain an IP address automatically (if it is not already selected), and then click OK.

Note You can also assign a unique static IP address in the range of 192.168.0.2 to 192.168.0.254. For example, you can assign the following static IP address, subnet mask, and default gateway:

   IP Address      192.168.0.2
   Subnet mask     255.255.255.0
   Default gateway 192.168.0.1
					

8.	In the Local Area Connection Properties dialog box, click OK.
9.	Quit Control Panel.
To view a video about how to confirm the LAN adapter IP configuration, click the Play button (Play button) on the following Windows Media Player viewer:

[http://support.microsoft.com/servicedesks/ShowMeHow/3061262.asx](http://support.microsoft.com/servicedesks/ShowMeHow/3061262.asx)

---

### Post by kvonb on 2007-05-01
Don't forget, if you are connecting a LAN cable directly between 2 computers then it **has** to be a crossover cable, **not** a standard straight through one!

Or if you connect them by going through a cheap hub/switch then that will do that for you, as long as one of the computers is connected to the crossover port, (it can be identified by a "x" type symbol).

---

