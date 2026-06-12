---
title: "nonstop network activity"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-11-19
How can I find out what is using my network, 'cause it's always working.
The system monitor is showing 25-45kb/s constant activity, even when every application is closed.

I installed firestarter, but even if I lock the firewall, the traffic is still on, no disturbance.
The single active connection is firefox-bin.
And something uses up the cpu, too, maybe they are connected.

Thanx fo any help

---

### Post by bodhi.zazen on 2007-11-19
[http://www.builderau.com.au/program/linux/soa/Monitor-network-traffic-with-ntop/0,339028299,339281712,00.htm](http://www.builderau.com.au/program/linux/soa/Monitor-network-traffic-with-ntop/0,339028299,339281712,00.htm)

---

### Post by Shazaam on 2007-11-19
The Windows version of Firefox has a bug where it will run another instance of itself in the background but I don't know if the linux version does that.

```
top
```
to see whats running.
Auto updates turned on and running?

Open terminal...

```
ifconfig -a
```

Go to System>Administration>Networking Tools. Run netstat from there.
Or you can use the terminal.

```
netstat --help
```

for the commands.
Another one I use is iptraf. It's in the repos. When you get it installed run...

```
sudo iptraf
```

Hmm. I will have to try ntop out as well.  :)

---

### Post by duruttye on 2007-11-19
I'm already installing gutsy, got tired, but still, thanx for the help, it looks like I will have the same problem, because the live cd does the same thing...
So probably I will be back...:)

---

### Post by duruttye on 2007-11-20
Well, I'm confused.
The IPtraf does show some traffic, but when the network is showing constant package reception, the IPtraf doesn't show anything.
When I close everything what could use the internet, the Iptraf shows no connection, and the network monitor shows incoming packages.

---

### Post by duruttye on 2007-11-20
Tried Firestarter.
No active connections, still the activity is sometimes 150-200 kb/s, when I lock the firestarter, the firefox doesn't work, but the activity is still going strong.

It slowly becomes windows or what the hell?

---

### Post by duruttye on 2007-11-20
Hey, bodhi.zazen
I tried the ntop, but I got stuck at installing it. Followed the steps (first 3) then cd-ed in the folder, and the ./autogen.sh command says:

bash: ./autogen.sh: No such file or directory

Also tried in different folders in here, no luck.

---

### Post by duruttye on 2007-11-20
I tried this command: 
sudo netstat -tcp
and I'm seeing a lot of this:

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        1      0 ubuntu.lan:49714        fk-in-f147.google.c:www CLOSE_WAIT 7842/npviewer.bin   

and this:
tcp        0      0 ubuntu.lan:44131        ohiggins.canonical.:www TIME_WAIT  -                   
tcp        0      0 ubuntu.lan:44246        ohiggins.canonical.:www TIME_WAIT  -                   
tcp        0      0 ubuntu.lan:44178        ohiggins.canonical.:www TIME_WAIT  -                   
tcp        0      0 ubuntu.lan:44130        ohiggins.canonical.:www TIME_WAIT  - 

Any ideas what that could mean??

---

### Post by bodhi.zazen on 2007-11-20
> **duruttye said:**
> Hey, bodhi.zazen
I tried the ntop, but I got stuck at installing it. Followed the steps (first 3) then cd-ed in the folder, and the ./autogen.sh command says:

bash: ./autogen.sh: No such file or directory

Also tried in different folders in here, no luck.

Try :

```
sudo apt-get ntop
```

It's in the repos :)

---

### Post by duruttye on 2007-11-20
well, shame on me...

---

### Post by duruttye on 2007-11-20
Slowly giving up...
Ntop doesn't do anything either.
Got tired of  it all.
If something uses the network, I'm gonna let it be.

thanx anyway!

---

### Post by bodhi.zazen on 2007-11-20
My guess is the loopback interface.

[http://www.geekcomix.com/cgi-bin/classnotes/wiki.pl?UNIX01/The_Loopback_Interface](http://www.geekcomix.com/cgi-bin/classnotes/wiki.pl?UNIX01/The_Loopback_Interface)

---

