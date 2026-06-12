---
title: "Port forwarding"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-08-21
Hi there, 
I want to redirect people (LAN) who access my computer on port 80 (Apache) to other port.
Like, when someone opens [http://my.ip.add.ress](http://my.ip.add.ress) they get redirected to [http://my.ip.add.ress:81](http://my.ip.add.ress:81)

Should I use iptables for that? What would be the syntax? (IpTables's manual has waay to much info).

Thanks, 
Klaidas

---

### Post by niteblind on 2006-08-21
Dont know the setup of you LAN but if you are using a router you can simply set the port forwarding up on that to forward all port 80 requests to your IP/DNS to port 81 instead.

niteblind

---

### Post by Klaidas on 2006-08-21
Well, I'm not the admin. I want users from inside of LAN to be redirected to [Http://my.pc.addreess:81](Http://my.pc.addreess:81) when they access [http://my.pc.address](http://my.pc.address), where [http://my.pc.address](http://my.pc.address) is an ip of a computer inside the LAN too (My PC).

So I need to configure it on localhost :)

---

### Post by Kilz on 2006-08-21
> **Klaidas said:**
> Well, I'm not the admin. I want users from inside of LAN to be redirected to [Http://my.pc.addreess:81](Http://my.pc.addreess:81) when they access [http://my.pc.address](http://my.pc.address), where [http://my.pc.address](http://my.pc.address) is an ip of a computer inside the LAN too (My PC).

So I need to configure it on localhost :)

Why not just add :81 to urls?

---

### Post by Chris Tucker on 2006-08-21
I am pretty sure this is possible with iptabes, or something of the like, because dns providers do it all the time
but if you have an apache server on port 80, just created a simple index.html, with a meta refresh with the value "0" in the <head> , and the new url, with port.
but if your running only 1 apache server, and thats on 81, the "other method" is the way to go, not sure on how to do it though.

---

### Post by Klaidas on 2006-08-21
> Why not just add :81 to urls?
Because I want to get the taste of how IPtables work :)

---

### Post by raptros-v76 on 2006-08-21
apparently, iptables can do this. 
```

iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 81

```

however, i dont know where to put that particular line.

---

### Post by edrodgers731 on 2006-08-21
I'd make it one of the first entries, but that's just me.  I always create a firewall script to maintain my firewalls, like:  [http://linuxcourse.rutgers.edu/lessons/lesson11/sec_13.html](http://linuxcourse.rutgers.edu/lessons/lesson11/sec_13.html)

(just an example.. I don't use this one)

---

### Post by niteblind on 2006-08-21
not able to check as in work currently on NT but I would expect IPtables will allow you to add it in before the last entry on the table????? assuming that they are similar to CIsco ACLs.

niteblind

---

### Post by steve.horsley on 2006-08-21
Nice one, raptros-v76.

That is a command, not a line in a configuration file. So you could run it by hand except that you need root privilege so if you are doing it by hand, you need to do:
> sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 81

It is normal to put such a thing (without the sudo) in a script that will be executed with root privilege near startup time. Not sure how best to do that. Maybe along with the script that starts the web service?

---

### Post by Klaidas on 2006-08-21
Hmm, the command doesn;t give an error, but doesn't seem to redirect :-k

---

### Post by edrodgers731 on 2006-08-21
firestarter is a popular tool for such a thing.  It runs an applet on the gnome-panel for setting up iptables..

---

### Post by Klaidas on 2006-08-21
Firestarter doesn't seem to give me that option.
Keep in mind that i'm NOT LAN admin that is trying to access computer in LAN from outside.

I'm inside the LAN, I'm not LAN admin, and I'm trying to forward port 80 from my PC to port 81 on the same (my PC) for in-LAN users like me.

---

