---
title: "Remote Desktop over Internet"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-01-24
I can use VNC over the LAN no problem but how do I use it at my business to home? The box has a static IP behind the router and modem is dynamically assigned but, I use DynDNS to keep track of it. So how do I do it?

Hamm

---

### Post by dimeotane on 2007-01-24
check out freenx..  its faster and more useable than VNC.

---

### Post by Hamm on 2007-01-25
> **Hamm said:**
> I can use VNC over the LAN no problem but how do I use it at my business to home? The box has a static IP behind the router and modem is dynamically assigned but, I use DynDNS to keep track of it. So how do I do it?

Hamm

no one has any ideas?

---

### Post by bernied on 2007-01-25
I do it like this:
- there is a ssh server on the linux box at home (with public/private key security), and port 22 is directed by the router/firewall to that box
- On my windows box at work I use Pageant to manage my private key then ssh using PuTTY (Pageant comes with PuTTY)
- In putty I tunnel port localhost:5901 to server:5901
- if I haven't got a vnc session running, I then start one on the server
- once the putty session is open I use Tightvnc localhost::5901
This is secure unless someone  gets hold of my private key, and cracks the passphrase on it (as far as I know).

I believe you can establish the tunnel without opening an ssh terminal, so could accomplish the windows end with a single command, but this is too much effort for me to figure out. I think the command is plink (also with putty).

---

### Post by yota on 2007-01-25
Have you set up port forwarding ( [http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding) ) in your router?
You should forward port 5900 for vnc from the router to the static ip of the pc on which vnc is actually running.

Hope this helps!

---

### Post by bernied on 2007-01-25
> **yota said:**
> Have you set up port forwarding ( [http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding) ) in your router?
You should forward port 5900 for vnc from the router to the static ip of the pc on which vnc is actually running.

Hope this helps!
Just remember that there is no security in vnc - everything is sent as jpegs and plain text (so I'm told), so very easy to intercept and even gain control of the server machine - hence the recommendation of the ssh tunneling gubbins.

---

### Post by Hamm on 2007-01-27
> **bernied said:**
> Just remember that there is no security in vnc - everything is sent as jpegs and plain text (so I'm told), so very easy to intercept and even gain control of the server machine - hence the recommendation of the ssh tunneling gubbins.

I have OpenSSH on the server. How do I check to see if I am using it to connect with VNC?

---

### Post by bernied on 2007-01-27
If you don't know whether you are or not using tunneling, then you are not.

You can try this out on your local LAN. Normally, to vnc, you would do something like:
```
vncviewer server:5901
```
where server is either the name or IP address of the vnc server, and 5901 is the port number to use. To tunnel the vnc session through ssh, you would start your ssh session like this (in linux):
```
ssh -L 5901:server:5901 server
```
Again where server is the name or IP address of the server, 
That -L option tells ssh to listen on port 5901 on the local machine, and forward all traffic on that port to port 5901 on server, but encrypting it for the journey using the same encryption as the ssh terminal.
Then, to open the vnc session, you use
```
vncviewer localhost:5901
```
So the traffic goes to the local port 5901, is encrypted by ssh, forwarded to the ssh server, unencrypted, then picked up by the vnc server.

For windows, you have to translate the commands above to work with whatever GUI you are using. In Putty, there is a section for tunneling in the configuration.

Remember if you are tunneling, then you vnc to localhost, not to the server, after the ssh session with the tunnel has started. If this doesn't work, then the tunnel isn't set up properly.

---

### Post by bernied on 2007-01-27
[Here's](http://www.gb.nrao.edu/pubcomputing/tunnel-howto.shtml) a howto that uses Putty for tunneling.

---

### Post by Hamm on 2007-01-27
> **bernied said:**
> If you don't know whether you are or not using tunneling, then you are not.

You can try this out on your local LAN. Normally, to vnc, you would do something like:
```
vncviewer server:5901
```
where server is either the name or IP address of the vnc server, and 5901 is the port number to use. To tunnel the vnc session through ssh, you would start your ssh session like this (in linux):
```
ssh -L 5901:server:5901 server
```
Again where server is the name or IP address of the server, 
That -L option tells ssh to listen on port 5901 on the local machine, and forward all traffic on that port to port 5901 on server, but encrypting it for the journey using the same encryption as the ssh terminal.
Then, to open the vnc session, you use
```
vncviewer localhost:5901
```
So the traffic goes to the local port 5901, is encrypted by ssh, forwarded to the ssh server, unencrypted, then picked up by the vnc server.

For windows, you have to translate the commands above to work with whatever GUI you are using. In Putty, there is a section for tunneling in the configuration.

Remember if you are tunneling, then you vnc to localhost, not to the server, after the ssh session with the tunnel has started. If this doesn't work, then the tunnel isn't set up properly.

Therefore if I use UnltraVNC veiwer from offsite (not my local LAN) and connect to remote Desktop use the password that I set up in remote desktop. I am not using a secured connection. Right?

---

### Post by bernied on 2007-01-27
Correct - the password is sent as clear text (I believe) and the session is not encrypted. If the session is intercepted what is on the screen can be seen (as jpeg files) and your keystrokes can also be read.

So don't be doing any internet banking like this.

---

### Post by Hamm on 2007-01-29
I have openSSH running on my ubuntu server. On a windows machine off site I run PuTTY and then run a VNC using the same port. Am I secure now?

---

