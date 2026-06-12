---
title: "Synergy - XP with Xubuntu"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by brady618 on 2006-11-11
I'm trying to set up synergy so that I can use the mouse and keyboard plugged into my windows xp computer with my xubuntu computer at the same time.  I've gone through all the threads and wikis, as well as scouring google, and I still can't figure out how to get it configured correctly.  When I try to start the server in ubuntu, I get this.

 synergys -f --config synergy.conf
INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
DEBUG: synergys.cpp,1051: opening configuration "synergy.conf"
DEBUG: synergys.cpp,1062: configuration read successfully
DEBUG: CXWindowsScreen.cpp,840: XOpenDisplay(":0.0")
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00800001
DEBUG: CXWindowsScreen.cpp,110: screen shape: 0,0 1024x768
DEBUG: CXWindowsScreen.cpp,111: window is 0x03200004
DEBUG: CScreen.cpp,38: opened display
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds
WARNING: synergys.cpp,505: cannot listen for clients: cannot bind address: Address already in use
DEBUG: synergys.cpp,519: retry in 10 seconds

What am I doing wrong??

I'm also having trouble with the client on the xp side, but that may just be bc I can't get the server right.  My synergy.conf file looks like this

section: screens
	Brady:
	Home:
end
section: links
	Brady:
		right = Home
	Home:
		left = Brady
end
 
Brady = XP comp name
Home = Ubuntu comp name

Help, please?

---

### Post by brady618 on 2006-11-11
Ok scratch that.  I figured it out, but what I am trying to do is use my xp keyboard and mouse on the ubuntu system, and putting the server on the ubuntu system made it so i'd use IT's mouse and keyboard.  And now I'm getting this error trying to set up the client in Ubuntu:

sudo synbergyc -f <192.168.1.111>
bash: syntax error near unexpected token `newline'

What do I do??

---

### Post by brady618 on 2006-11-11
Well no one is replying to these threads so I assume no one really knows about this program, but here goes.  I've gotten the client to work but now i have a problem with it connecting to the server.  I'm getting this when I try:


INFO: synergyc.cpp,716: Synergy client 1.3.1 on Linux 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
DEBUG: CXWindowsScreen.cpp,840: XOpenDisplay(":0.0")
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00800001
DEBUG: CXWindowsScreen.cpp,110: screen shape: 0,0 1024x768
DEBUG: CXWindowsScreen.cpp,111: window is 0x04000004
DEBUG: CScreen.cpp,38: opened display
NOTE: synergyc.cpp,330: started client
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady
DEBUG: synergyc.cpp,237: retry in 1 seconds
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady
DEBUG: synergyc.cpp,237: retry in 3 seconds
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady
DEBUG: synergyc.cpp,237: retry in 5 seconds
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady
DEBUG: synergyc.cpp,237: retry in 15 seconds
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady
DEBUG: synergyc.cpp,237: retry in 30 seconds
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady
DEBUG: synergyc.cpp,237: retry in 60 seconds
WARNING: synergyc.cpp,265: failed to connect to server: address not found for: Brady

Please someone.  I'm running out of ideas. :(

---

### Post by skatotron on 2007-05-10
> **brady618 said:**
> Ok scratch that.  I figured it out, but what I am trying to do is use my xp keyboard and mouse on the ubuntu system, and putting the server on the ubuntu system made it so i'd use IT's mouse and keyboard.  And now I'm getting this error trying to set up the client in Ubuntu:

sudo synbergyc -f <192.168.1.111>
bash: syntax error near unexpected token `newline'

What do I do??

I'm getting this same error, except my client is a powermac G4 running ubuntu with the server running os x.

I would also like to know what to do.

---

### Post by aws910 on 2007-05-16
Been using Synergy for weeks now and it just stopped working.  Had the "address not found for" error and if anyone else is having it, this is what worked for me:  from the XP computer(client), I tried to ping the hostname of the server(Ubuntu) in a cmd window.  It wouldn't resolve to an IP address on a ping, so in the XP Synergy setup I tried entering the IP address directly and it worked.  I know the label says "hostname" but you can enter an IP address and it will work as well.

As for the other error you may get when trying to launch the Ubuntu side of things, I've found a program on Ubuntu that makes it pretty easy to set up that side of the Synergy connection.  It's called "QuickSynergy" and it can be installed from the synaptic package manager or from a command line("sudo apt-get install quicksynergy").  If it doesn't show up on your menu(under applications/accessories), you can run it from a command prompt by typing "/usr/bin/quicksynergy".

Quicksynergy is super-dumbed-down(perfect for me!).  If you're using QuickSynergy as the server, you would enter the hostname(or ip address) of the client(in my case the XP machine) in the location you want the screen to go.... then just click "start".  On the XP version of Synergy, you will see a little lightning bolt in the middle of the blue/green circular tray-icon when you are connected.  Sometimes it takes a few seconds to connect, but it's a great program, a real lifesaver. HTH 8)

---

### Post by noMScraig on 2007-05-19
I am using XP and ubuntu and Synergy.

QuickSynergy worked for my server setup on the Ubuntu side

I had to use the IP addresses in the server setup on ubuntu. 

 Additionally, I used the IP addresses on the client synergy setup on the XP machine.

Now it works perfectly and I have been using it for a couple of days now.

I can now say that I will not be using VISTA!

---

### Post by zorog on 2007-06-07
remove the < and > and all should be good.

---

### Post by cybohemia on 2007-11-24
Finally got it! Here's what I did:

On Windows XP (synergy server): open cmd shell and type ipconfig
(you'll see a listing of a few connections, you'll want the IP Address, say it's 192.168.1.100)

On Ubuntu (synergy client): synergyc 192.168.1.100 (or what it said above)

That should do it.  I had the same problem because I tried to use my XP machine name while synergy wanted the IP address.

Hope this helps - I know it's over a year after your posting but I just installed Ubuntu yesterday :-)

---

### Post by n0r1 on 2008-04-10
Even though this is an old post, since the question is answered and I found this by googling for the error message the above user is receiving, I thought I'd post my solution.

Yes, the "address already in use" error is about the port being already bound.  But no voodoo is required to fix this -- turned out that, when I got this (on my server side), I was already running an instance of synergys that I hadn't killed.  Grepping in the process list for 'synergys' and killing it freed me up to restart it.  (I suppose I could have just used the existing process, too -- I'll try that next time.)

Yay synergy!

HTH,

- nori

---

