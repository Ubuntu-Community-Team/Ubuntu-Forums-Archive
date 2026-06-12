---
title: "Remote Access an XP pro PC over the internet with Ubuntu?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by eekfonky on 2007-05-16
I have a friend in France and often the quickest way to sort out any issues with files is for me to remote access his computer. Since moving from XP to ubuntu I cannot find a way to remote access his PC. I have the IP address, can anyone help?

---

### Post by compmodder26 on 2007-05-16
There is a terminal server client installed by default in Ubuntu.  Go to Applications->Internet->Terminal Server Client.  Fill in the appropriate information and click "Connect"

---

### Post by tompickles on 2007-05-16
ive never tried it - but in "applications -> internet -> terminal server client" this lets you connect to a remote PC.

No idea if this is useful as not had to try it myself yet.

---

### Post by eekfonky on 2007-05-16
I tried the Terminal Server Client and it say connection refused although my friend has not refused any connection. Apart from the IP address, what other info is required?

---

### Post by tompickles on 2007-05-16
again - no idea if itll work, but you could try installing Gnome-RDP using add/remove programms - showing all open source.

---

### Post by lazyart on 2007-05-16
Be sure that your Terminal Services Client is connecting with RDP or (RDPv5).

---

### Post by compmodder26 on 2007-05-16
Are you using the proper username and password to connect to your friends machine?

---

### Post by BHelts on 2007-05-16
with the terminal server client you have to set up the xp machine to allow RDP, this will also log out the current session that your friend is logged into.  if you want him to watch what you are doing, terminal server client is not for you.  You want your friend to download a VNC server, then you'll log on using vnc viewer with something like 123.456.789.123:5900 or whatever port you want to use.  you'll have to set up port forwarding on your friends router if he has a router and you'll need to open up that port on any firewalls running on his/her machine.

---

### Post by eekfonky on 2007-05-16
he doesn't need to see what I'm doing I just need access from time to time.
Also his machine isn't password protected but has a user name on the start screen, is this what I need?

---

### Post by dbott67 on 2007-05-16
There are a number of issues that you may have to contend with.

1. Routers, Firewalls & port-forwarding:  Most home-based NAT routers will not permit unsolicited inbound connections, so you would need to make sure that if your friend has a router, it needs to have port 5900 forwarded to his internal IP address.

Additionally, Windows XP has a software firewall that's enabled by default that would prevent a connection.  You would need him to create an exception that permits port 5900 (TCP) inbound.  Click "ADD PORT" and add the appropriate port.

[IMG]http://www.cezeo.com/tips-and-tricks/windows-xp-firewall/windows-firewall.png[/IMG]

Additionally, there are 3rd party firewall products (Norton/Symantec, McAfee, etc.) that would need to be configured if installed.

If you're friend is not that tech-savvy, this could prove to be somewhat of a challengs.

3. If you're tech-savvy and can do port forwarding on your end, you might want to try a  "Reverse VNC" connection.  I've written up a HOWTO here:

[http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

Post #1 and #6 are what's required for sending a Windows XP session to Ubuntu.

-Dave

---

### Post by lazyart on 2007-05-16
what protocol is your terminal services window trying to connect with?  I think it defaults to VNC but you want RDP.

Since the OP says he's connected before I doubt it's an issue with the windows machine.

---

### Post by eekfonky on 2007-05-17
Thanks, I'll try that next

---

