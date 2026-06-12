---
title: "VNC problems"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by _Lawless on 2005-11-11
Hi! I got your attention. Sorry about the naked pic thing :D 

Ok so I'm at work trying to continue setting up my home server.
Before I left home I set up remote desktop to allow connections and set a password.

Now that I'm at work, I can't get tightvnc to connect.
I can however connect using putty.

I have RDP access to another computer running XP Pro so I can get access to my router and have oppened up all ports I can think of, 22,23 5900 etc and even tried DMZ and so far no go.

After seaching the forums, I tried to see if vncserver was even an option as a command in terminal and it doesn' show up. (Not sure if that means anything lol)

Anyway, any suggestions?
Anyway to see if vncserver is running by way of the putty terminal connection?

Thanks a million!

---

### Post by zhorty on 2005-11-11
Use [Real VNC](http://realvnc.com/download.html)

---

### Post by dbott67 on 2005-11-11
> **_Lawless]Ok so I'm at work trying to continue setting up my home server.[/quote]
It sounds like your home computer is behind a cable/DSL router, correct?
[QUOTE=_Lawless]Before I left home I set up remote desktop to allow connections and set a password.[/quote]
Good.  Make sure you don't require confirmation for the connection (see attached pic).

Do you have another computer at home that you can check to make sure that you can connect?
[QUOTE=_Lawless]I can however connect using putty.[/quote]
This is good.  This means that you can cnnect through any firewall/cable router that is running.
[QUOTE=_Lawless]I have RDP access to another computer running XP Pro so I can get access to my router and have oppened up all ports I can think of, 22,23 5900 etc and even tried DMZ and so far no go.[/quote]
5800 and 5900 are the ports (5800 for the HTTP server said:**
> After seaching the forums, I tried to see if vncserver was even an option as a command in terminal and it doesn' show up.
It's actually vino-server in Ubuntu (I don't know why).

[QUOTE=_Lawless]Anyway to see if vncserver is running by way of the putty terminal connection?[/quote]
Yes.  To verify that vnc-server is 'listening' on the correct port (5900) type **netstat -t -l **(the -t is to only show TCP protocol; the -l is to show only listening ports):
```
dbott@breezy:~$ netstat -t -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN
tcp        0      0 localhost.localdo:32771 *:*                     LISTEN
tcp        0      0 *:5900                  *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN

```

As mentioned, VNC-server is actually vino-server in Ubuntu, so you could always list all processes (**ps aux**) and then pipe it to grep & search for vino (**| grep vino**):
```
dbott@breezy:~$ ps aux | grep vino
dbott     7621  0.0  2.3  17100  6100 ?        S    Nov09   0:07 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=27
dbott    10943  0.0  0.3   3068   772 pts/1    S+   20:41   0:00 grep vino
dbott@breezy:~$
```

A few other things to keep in mind:
1. Connecting to a linux box requires you to include the virtual desktop number (0,1,2,3,etc).  So, in the VNC viewer connection dialog box, you would need to type: **your.home.ip.address:0**
2. Some corporate firewalls block inbound AND outbound traffic.  Make sure your work firewall is not blocking outbound traffic on 5900.  If so, you can always configure your vnc (vino) server at home to listen on a permitted port # (here's a link to a [post that I wrote on another forum]("http://leovilletownsquare.com/fusionbb/showpost.php?post/26489/") on how to change the port # on vnc)
3. Make sure your work computer is not running a software firewall that is blocking 5900.

Hope this helps.

-Dave

---

