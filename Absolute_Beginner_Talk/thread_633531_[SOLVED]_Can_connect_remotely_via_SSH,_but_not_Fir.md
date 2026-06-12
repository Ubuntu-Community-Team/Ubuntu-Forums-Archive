---
title: "[SOLVED] Can connect remotely via SSH, but not Firefox"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by ResumeMan on 2007-12-06
I suspect I'm missing something fairly basic here.

I have an Ubuntu box at home, which I'm establishing as a file server. I have set up SSH server on this, and I forwarded Port 22 on my router to its IP address. Using PuTTY, I can connect to the PC from work. Using Cygwin/X I can even launch graphical apps, though it is agonizingly slow (I think we are getting more bandwidth at work soon; hopefully that will help -- but that's not relevant here).

However, I also have a couple of web-based apps running that I am having less success accessing. Specifically, I have enabled the Web UI of Deluge, and I have Webmin running. Both work fine over the LAN, but I'm not able to connect to either of these remotely. I forwarded both ports to the server IP.

I have tried both http://<my IP> and setting up a connection through no-ip.org, with a colon and the port number. I'm getting a "Firefox can't establish a connection to the server at <IP>:<port>." I also tried both via http: and https:

Is there some key thing that I'm missing here that will let this work? I haven't tried to access from any other external site, so I can't be certain that it isn't some kind of filter on my employer's side, but it doesn't "feel" like it. They run Websense, but usually I have no problem accessing any sites that aren't specifically in prohibited categories (porn, music downloads, etc) and when I do Websense tells me pretty clearly that that's what happened.

Thanks!

---

### Post by camccall on 2007-12-06
I don't use Ubuntu as a server so I'm not as informed as I would like, but is it possible that your security setting for apache are prohibiting outside connection?

---

### Post by ResumeMan on 2007-12-06
Well. I don't *have* Apache installed. So there is no problem stemming from Apache :)

BUT -- is that somehow the problem? Do I *need* Apache to have a web UI accessed from outside the LAN?

If so, there's nothing keeping me from setting it up, I just haven't. (but if I do prepare for more questions about setting up apache ;) )

---

### Post by Swmmrman on 2007-12-06
I use webmin myself,  But i also have apache.  I have bouned off PHP proxies and it loads.

---

### Post by camccall on 2007-12-06
well I guess it depend on the apps, what apps are you trying to access?

Wait, you said you can access them from the LAN.  Grrrr need to process what I read.  

Okay first it may help to let us know what apps you are trying to access.  Also if there is any security limiting what networks can access your apps that might be a problem.  If you could use ngrep when you are accessing your maching remotely and try accessing the web apps that might let you know where the problem is occring.  Try running  ngrep port 80 and see if anything is happening when you try and access the apps.

---

### Post by ResumeMan on 2007-12-06
At least at this point, It's webmin (which uses port 10000) and the Web UI of [Deluge-torrent]("http://deluge-torrent.org/"), which uses port 8112. I could see others getting added later.

As I said, I have forwarded the ports on my router and I know that port forwarding works to *some* degree because I can SSH into the box on Port 22.

I truly have no clue at this point how apache functions, so I've no idea whether it's needed for an app like these

---

### Post by Dr Small on 2007-12-06
Did you forward port 10000 on your router to your network IP?
Did you open port 10000 on your firewall by using Firestarter and apply the policy ?

---

### Post by Slim Backwater on 2007-12-06
If you can ssh into your box, and when you are at home you can access Webmin on port 10000 (probably with something like [http://localhost:10000/](http://localhost:10000/) ) then you can use SSH to tunnel a connection.

I'm not sure what SSH client you are using at work, but if it's like ordinary SSH you could try something like this:

ssh -L 8080:localhost:10000 [email]user@myhost.no-ip.org[/email]

If you get logged in with this, then with your work browser connect to [http://localhost:8080/](http://localhost:8080/)  (I'll also say to make sure that you don't have your browser configured to use any proxy server, as the request will go out to it, and miss the ssh tunnel)

What's happening here is that your work SSH command is listening for connections to port 8080 and anything it gets there, it tunnels over the ssh connection to your home computer, and then through to localhost:10000 from your home computer's point of view.

Likely, Webmin at home is configured to only accept connections from localhost, which is why you can't get connected from outside, but the ssh tunnel is so cool as all your traffic is encrypted, and you can setup other tunnels to other devices or services.

This is a good one:

ssh -D 8080 [email]user@myhost.no-ip.org[/email]

And set your work browser to use a SOCKS proxy on localhost port 8080.  Then you can browse the web like normal, but all the outbound connections are made through your hom computer.  being encrypted to your home, no one@work can tell what websites your browsing.

HTH.

---

### Post by Slim Backwater on 2007-12-06
> **ResumeMan said:**
> At least at this point, It's webmin (which uses port 10000) and the Web UI of [Deluge-torrent]("http://deluge-torrent.org/"), which uses port 8112. I could see others getting added later.



I missed your Deluge interface, here's an example:

ssh -L 8080:localhost:10000 -L 8081:localhost:8112 [email]user@myhost.no-ip.org[/email]

there's nothing special about my choices of 8080 and 8081, they are simply unused ports on your work computer.  You even could use ports 10000 an 8112, if nothing on your work computer was using them.

._.

---

### Post by camccall on 2007-12-06
Good idea Slim, I seem to forget about ssh forwarding quite often.

---

### Post by Dr Small on 2007-12-06
Unless work closes all ports except 80 and 443. Then you need to set SSH to listen on port 443 or whatnot, and feed the tunnel through 443 to "fake" the firewall.

---

### Post by ResumeMan on 2007-12-06
OK, that's interesting. I'm home now but will be sure to try that in the morning.

Now, this is substantively different from X11 forwarding right? X forwarding works, but as I said above, it is painfully slow. But it sounds like the local firefox process will be doing most of the work in this case, yes?

Thanks for the help, I'm intrigued and will let you know how it works out.

---

### Post by ResumeMan on 2007-12-07
Well I"m giving it a try.

I ssh'd to my home box using Cygwin/X. I used the command ssh -L 8080:localhost:8112 username@ip.

It connected me no problem. I went to [https://localhost:8112](https://localhost:8112) and Firefox still gives me "can't establish a connection to the server at localhost:8112"

My network connection is set to "direct connection to the internet." Is that right? All the proxies are turned off. Is there another, basic setting I need to adjust?

Also, per Dr. Small, I tried port 443 as well. No dice. Is there a way I can figure out what ports are open?

Thanks, I think I'm getting closer!

Edit: also, on the console, when I try to connect I get the response: "channel 2:open failed:connect failed:connection r

---

### Post by ResumeMan on 2007-12-07
> **camccall said:**
> Okay first it may help to let us know what apps you are trying to access.  Also if there is any security limiting what networks can access your apps that might be a problem.  If you could use ngrep when you are accessing your maching remotely and try accessing the web apps that might let you know where the problem is occring.  Try running  ngrep port 80 and see if anything is happening when you try and access the apps.

Uh....you lost me.

I tried typing ngrep into putty and learned I needed to install it, so I did. But the man page is rather confusing.

If I just type "ngrep port 80" i get the response: no suitable device found. operation not permitted.

But I'm probably just leaving out some operators there.

Any guidance on this??

---

### Post by camccall on 2007-12-07
I believe ngrep should be run with sudo, though there may be a better and more secure way.

---

### Post by ResumeMan on 2007-12-07
Ah, ok I should have thought of that. Usually sudo-required commands spit back something like "permission denied".

the response I got was 

> interface: eth1 (192.168.1.0/255.255.255.0)
filter: (ip or ip6) and (port 80)

Then it sat there for awhile with no prompt. I eventually ctrl+c'd out and it said

> exit
2 received 0 dropped

Does this tell us anything? :) Should I do it with other operators or let it sit longer?

---

### Post by camccall on 2007-12-07
Okay so first were you trying to access the web app at the time?  I have to ask :). Additionaly can you please tell us what apps you are using?  It would be a big help.

---

### Post by ResumeMan on 2007-12-07
Well.

I spoke too soon. The terminal soon spit out a lot of stuff that looked like this:

```
interface: eth1 (192.168.1.0/255.255.255.0)
filter: (ip or ip6) and ( port 80 )
#
U 192.168.1.50:6881 -> 91.122.144.146:80
  d1:ad2:id20:..da.C .xQ.}s+..K.X.e1:q4:ping1:t2:.y1:v4:LT..1:y1:qe
#
U 91.122.144.146:80 -> 192.168.1.50:6881
  d1:rd2:id20:&..O..&|g....l....}.e1:t2:.y1:y1:re
#
U 86.56.61.110:80 -> 192.168.1.50:6881
  d1:ad2:id20:..z...._.5....o.E.Q.e1:q4:ping1:t8:..s.v.j.1:y1:qe
#
U 192.168.1.50:6881 -> 86.56.61.110:80
  d1:rd2:id20:..da.C .xQ.}s+..K.X.e1:t8:..s.v.j.1:v4:LT..1:y1:re
#
U 117.47.62.154:80 -> 192.168.1.50:6881
  d1:ad2:id20:..}.{.e40q....xyfCn.6:target20:...1......Ae.q.....ee1:q9:find_n
  ode1:t8:.......J1:y1:qe
```

And on and on...

I wasn't specifically trying to access the home server via my work Firefox at that time, but I know that at some point during the run I did. But I don't think that's what this is telling me :)

I redirected the output to a text file and let the thing run a couple hours; I now have a 12kb file if you'd like to see the whole thing :confused:

I'll be heading home for the weekend shortly, so won't be able to play with this remotely till Monday, but am interested if anyone knows what's happening here...

---

### Post by ResumeMan on 2007-12-07
Oh, and I'm not sure what you mean by "what apps." The things I'm trying to access on the home computer are a Deluge bit-torrent and Webmin. What do you need to know?

Thanks

BTW another minor update -- I asked my wife to try the url from her office, to see if it was something unique to my location. She got a "The requested URL could not be retrieved." Obviously, she could have security issues too, but it's another data point.

---

### Post by ResumeMan on 2007-12-10
Well it magically started working today :S - at least Slim's workaround. I still can't get directly to the box remotely using the IP address. 

Thanks!

---

### Post by camccall on 2007-12-10
Is the IP address from the ngrep output the address for your work computer?  So is the web interface to Deluge setup for port 80 or did you select a different port?  Also webmin usually listens on port 10000 by default, did you change that?

---

### Post by ResumeMan on 2007-12-10
The first ip in the output is the internal ip of my server box at home. I have NO idea what any of the others are; they aren't my home's world-facing ip and they aren't my company's world-facing ip.

The web interface for deluge is set up to 8112. Actually I may not have opened port 10000 in firestarter (DEFINITELY did open 8112).

I'm also working on setting up apache. I've set apache to listen to port 9876 and have that open and forwarded.

---

### Post by camccall on 2007-12-10
Ok in that case your ngrep command should have been ngrep port 8112.  Port 80 would not do any good in that case.

Also, is their anyway you can run netstat lp on your server and post the output.

---

### Post by ResumeMan on 2007-12-15
OK, well everything seems to be working as planned at this point. I have no idea why since I didn't change anything :-k

Thanks for the help!

---

