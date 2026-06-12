---
title: "Simple Remote Desktop - how?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2007-01-06
I'd like to control the Ubuntu desktop in my office while watching the playoffs (Indy 16, KC 0 right now) using my Ubuntu laptop.  I enabled the system preference for remote desktop on the desktop.  Installed gnome-remote desktop client on my laptop, but all I can get is "ERROR: connect: Connection refused".  What's missing?

---

### Post by ajmorris on 2007-01-06
you get a code when you start the server (desktop in your case) don't you? so did you enter that code when you try to connect with the client (laptop in your case).

---

### Post by Atomic Dog on 2007-01-06
It sounds like a password issue.

---

### Post by moshuptrail on 2007-01-06
I didn't start the server - I assumed that when I enabled it from System > Preferences > Remote Desktop that would start the server.  No?  So I didn't get a code either.
There was an option for a password under security.

On the client side, I configured the connection as RDP, There's a field for a username and password - I assumed my login id and password on the server (desktop) machine.  There's no place for a connection password.  I figured that would be requested on the fly.

p.s. I've tried the desktop both with and without a password.  Same results.

---

### Post by moshuptrail on 2007-01-06
Does the server need to be logged out?

---

### Post by moshuptrail on 2007-01-06
No.  You need to be logged in on the server.
You need to require a password.  (If you don't it doesn't connect at all)
I can connect with vncviewer from the command line.
I assume that's different from Gnome-RDP.

---

### Post by ajmorris on 2007-01-06
the server has to be started to use the Gnome-RDP

---

### Post by AndyCooll on 2007-01-06
On the machine you are trying to connect to, under "Preferences > Remote Desktop", have you enabled sharing privileges, and have you set a password?

:cool:

---

### Post by moshuptrail on 2007-01-07
Yes, I checked: 
Allow other users to view your desktop
Allow other users to control your desktop

I un-checked:
Ask you for confirmation
Require the user to enter this password.

After reading a bit more I am thinking that RDP is really for windows inter-operability.
I was unable to connect with rdesktop from the command line.  It still gives the connection refused error.  I'm thinking it's expecting me be logged in to a domain...  ???

I WAS finally able to get vnc, and xtightvnc working from the command line.
Gnome-RDP has some idiosyncrasies when using vnc.  If you don't use a "friendly" combination of parameters it returns a --help screen from xtightvnc.  I guess it composes the command line wrong in some cases.

At any rate, having figured out command line access, I simply created a desktop launcher to start xtightvnc the way I want and abandoned Gnome-RDP.  

Anyone else having "issues" with Gnome-RDP?

PS ajmorris keeps talking about a server.  how do I start the rdesktop server on the desktop (server) side?

---

### Post by Scorpuk on 2007-01-07
when you were connecting to your server through vncviewer did you pass screen 0 as a parameter?

eg

192.168.1.1:0


Otherwise it wont connect to the logged in user.


It might a good idea to set a password as if someone finds out your IP address they too can log on through vncviewer.

---

### Post by moshuptrail on 2007-01-07
Yes.  I was using the :0   what's the diff between :0 and :1 ?

Correct me if i'm wrong - isn't 192.168.x.x a non-public IP address?  you would have to be behind my NAT router to access an IP there, right?  How careful do I need to be?

Or, if I know the public IP of someone's router,(eg. 62.24.23.107) then it's a good bet that 192.168.1.1 is a valid address on the other side and I can get to it somehow?

---

