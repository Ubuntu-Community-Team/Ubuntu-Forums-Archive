---
title: "Getting Online"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by etorres on 2005-12-11
I just installed ubuntu on a computer for a christmas gift. How in the world do I get online. I know it might be a stupid question, but I need to know so the kids that are recieving can get online. Thanks

---

### Post by Zelut on 2005-12-11
Is it connected to your LAN now?  Does that not connect?  I'm assuming it should work out of the box--just run Firefox and you should be online.

If you're planning on using wireless however, well, thats another story that'll take some more work

---

### Post by etorres on 2005-12-11
I don't understand. How do I connect to an isp?

---

### Post by GreenHawkIA on 2005-12-11
Are you trying to connect through dial-up (a modem) or through a high-speed (broadband - like cable or DSL) connection?  What you do depends on what type of setup you have.

---

### Post by etorres on 2005-12-11
I will be using dial-up with this computer.

---

### Post by GreenHawkIA on 2005-12-11
Up in the upper right hand corner of your Ubuntu there should be, by the date, a network connection symbol - looks like two monitors stacked on top each other.  Click on that, and a connection properties screen will come up.  Click on the configure button, then a network settings box will come up.  You should have a box with all your network interfaces, one of which should be modem connection.  Double-click on that, click the checkbox to enable that connection, and fill in your information.  After you close out that window with all your information filled in, use the drop down menu at the bottom of the network settings window to change your default connection to your modem.  That should get you started.

---

### Post by Mustard on 2005-12-11
Here is a pretty good HOW TO on dialup.

[https://wiki.ubuntu.com//DialupModemHowto](https://wiki.ubuntu.com//DialupModemHowto)

---

### Post by Mustard on 2005-12-11
[QUOTE=GreenHawkIA]Up in the upper right hand corner of your Ubuntu there should be, by the date, a network connection symbol - looks like two monitors stacked on top each other.  Click on that, and a connection properties screen will come up.  Click on the configure button, then a network settings box will come up.  You should have a box with all your network interfaces, one of which should be modem connection.  Double-click on that, click the checkbox to enable that connection, and fill in your information.  After you close out that window with all your information filled in, use the drop down menu at the bottom of the network settings window to change your default connection to your modem.  That should get you started.[/QUOTE]

That's how I got started up when I first installed Ubuntu. Although I got to the Networking gui via the System>>Administration>>Networking menu option.  I think the problem with doing it that way (at least from my experience) is that it started dialing out during the boot sequence when the boot sequence was trying to synchronise the system clock with an ntp server.

Currently I have no entries in the Network gui with regards to my ISP settings.  Its all handled using the methods described in the HOW TO above.  After that is set up, I then downloaded gnome-ppp using synaptic and after filling in the configurations for gnome-ppp I can now easily connect via the gnome-ppp gui.

---

### Post by Mustard on 2005-12-11
[QUOTE=etorres]I will be using dial-up with this computer.[/QUOTE]

You didnt specify whether the kids are using the same connection that you are currently using.

Are the kids going to be using the same ISP to connect?

---

### Post by unisol on 2005-12-13
in a terminal type wvdialconf /etc/wvdial.conf hit enter and wvdial will tell you what port you r modem is on. then go into system/ adminstrator/networking and fill in the infirmation: isp, username, password, etc you should connect

---

