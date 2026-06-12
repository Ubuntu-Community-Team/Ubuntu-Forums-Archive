---
title: "Firestarter quits working...."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-04-17
Anyone know why Firestarter would quit working after a time?  The blue button icon that sits on the status bar doesn't show any hits on the firewall even though there are hits. When I start another instance of Firestarter the new program shows that the firewall is getting hit...yet the original instance of the program still shows no hits.  Have I misconfigured something, or what is going on?  thx

---

### Post by raindog on 2007-10-27
I too have noticed that Firestarter quits after a period of time.  At this time I don't have a solution for this.

---

### Post by n3tfury on 2007-10-27
does it actually quit (as in no longer listed in system monitor) or has the gui just disappeared?

---

### Post by raindog on 2007-10-27
It actually quits.  I checked the running processes and it wasn't listed.  I know that iptables is still running, but I still would like to figure out what is going wrong.

---

### Post by n3tfury on 2007-10-27
lol, i didn't realize the original post was from 06.  there was someone else around here that said the same as you recently, but i can't find the post.

---

### Post by GeneralCody on 2008-03-04
Quits on me too...
Switching to Shorewall...

---

### Post by OrangeCrate on 2008-03-04
> A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. This is untrue ! Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run only to configure your firewall. Once configured, IP tables (the actual firewall) is active (at boot) without having to run firestarter/guarddog. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by GeneralCody on 2008-03-04
Sure. The configuration would still be intact, but it would be nice to monitor the connections in the same application, without the GUI going down all the time...

---

### Post by OrangeCrate on 2008-03-04
> Giving the user permission to launch Firestarter without the root password

In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your /etc/sudoers file in your favorite text editor and add the following line at the end:
username ALL= NOPASSWD: /usr/bin/firestarter

Note: Debian users should replace /usr/bin/firestarter with /usr/sbin/firestarter in the above line.

Simply replace username with whatever your login is. The specified user is now able to launch Firestarter without being prompted for a password using the command sudo firestarter.

A note on the security aspects: This method makes a trade off in local security for convenience. If your user account becomes compromised the attacker will be able to control the firewall. However this method is preferable to having a shared root user password in a multiuser setting. It is also preferable if the alternative is not to run Firestarter at all.
Launching Firestarter minimized to the tray on login

[B]Having performed the above configuration of permissions, the system can further be set up to load Firestarter when you log in with your regular user account. Firestarter will in that case load directly into the system tray without user intervention, after which the main interface can be accessed by clicking the tray icon.

Using GNOME:
The GNOME sessions manager

Open up your GNOME menu, select Preferences followed by Sessions. Switch to the Startup programs tab, pictured right.

Click Add and enter
sudo firestarter --start-hidden
as the startup command. Click OK and you're done.[/B]

To stop Firestarter from loading on login, simply remove its entry from the startup programs listing.


[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by jasad on 2008-03-04
I've followed all of the steps to change sudoer to eliminate the need for a password, and created a startup entry for firestarter, and no luck

 If I add the line to sudoers to circumvent the password, firestarter won't start.  It tries, hangs, then quits.  If I take the "username ALL=NOPASSWD:..." line out of sudoers, I can get firestarter to launch at startup, but I (of course) have to enter my password.  I am starting to get to the point where I may pull the rest of my hair out.

Oh, and "sudo firestarter --start-hidden" doesn't work.  I have to use "gksu firestarter"  Neither sudo nor the --start-hidden parts work...

Has anyone actually managed to get firstarter to launch at startup in Gutsy, or is all of this just speculation about what ought to work?

So confused...

Thanks knowledgeable people.  :)

Jason

---

