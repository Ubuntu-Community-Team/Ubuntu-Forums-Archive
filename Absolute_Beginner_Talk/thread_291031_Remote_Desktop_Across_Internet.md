---
title: "Remote Desktop Across Internet"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-11-01
I'm trying to connect to another machine via the internet with the ubuntu's
 default client (vino). I am able to connect through the lan, but am having a
 hard time connecting across the internet. He's got his port opened, but I'm
 getting "unable to connect to VNC server". Am I to forward a port also? I've
 seen something like that, but my linksys interface won't allow me to forward 
ports to public IP addresses. Please guide me towards the right method to get
 this working. Thanks!

---

### Post by dmizer on 2006-11-02
don't do it.  that's my advice.
1) it's WAY insecure.  like parking an unlocked mercedes in the projects ... with the doors open ... and keys in the ignition ... running ... with a signed bill of sale and title laying in the passenger seat ... right next to the checkbook full of blank signed checks.
2) it would most likely be prohibitively slow anyway.

is the machine you're trying to connect to a windows box or a linux box.  if it's a linux box, just use ssh.  you can forward x with the -X option:
```
ssh -X userid@ipaddress
```

then you have command line access with x enabled.  so you can have gui apps open on your desktop as though the terminal was right in front of you.

if it's a windows box, dunno if i have any suggestions for ya.

---

### Post by JayTee on 2006-11-02
> **dmizer said:**
> don't do it.  that's my advice.
1) it's WAY insecure.  like parking an unlocked mercedes in the projects ... with the doors open ... and keys in the ignition ... running ... with a signed bill of sale and title laying in the passenger seat ... right next to the checkbook full of blank signed checks.
2) it would most likely be prohibitively slow anyway.

is the machine you're trying to connect to a windows box or a linux box.  if it's a linux box, just use ssh.  you can forward x with the -X option:
```
ssh -X userid@ipaddress
```

then you have command line access with x enabled.  so you can have gui apps open on your desktop as though the terminal was right in front of you.

if it's a windows box, dunno if i have any suggestions for ya.

I don't think it's quite as bad as Dmizer describes it. ;) More like parking your Mercedes in an unsafe neighborhood with a spare key in the glove box unlocked and the garage door opener clipped to the visor and your home address listed on several papers in the glove box. Vnc sends passwords unencrypted over the network unless you tunnel through ssh. Someone would have to intercept the packets, (not easy but not too too difficult either) which is like smashing the Window, then they've got your password which is the key in the glove box, from there with a little extra effort they can find your house and use the garage door opener to loot your crib of all your bling. Like dmizer said, better to use ssh. If you have to use vnc there are a few How-To's on tunnelling it through ssh and that'll give you the added encryption you want to have for security. Does your friend have his vncserver running? Is this linux to linux or linux to Windows?

---

### Post by Joeak on 2006-11-02
I agree; if VNC isn't working over the internet LEAVE IT ALONE.  If you've got ssh working between the two, you can tunnel vnc through ssh:

> vncviewer -via account@ipaddress localhost:0

If you have ssh working to just one machine on the remote network, you can specify any VNC machine on the local network by replacing "localhost" with their remote IP addresses, such as:

> vncviewer -via [email]root@mydomain.com[/email] 192.168.1.100:0

If you do have SSH open to the internet, you should take steps to control it well.  I use hosts.deny, hosts.allow to allow connections only from my known haunts, and run snort and logcheck to send myself messages about unusual acivity on the system.  (I am no expert, there are certainly better methods...this is just what I'm doing so far).  I did detect someone banging away with bad usernames and passwords (Joe, Bob, Mary, Dick, Harry, etc., etc.) for a while before I did the hosts.deny thing to block most attempts of that type.

---

### Post by dmizer on 2006-11-02
> **Joeak said:**
> I agree; if VNC isn't working over the internet LEAVE IT ALONE.  If you've got ssh working between the two, you can tunnel vnc through ssh:

> vncviewer -via account@ipaddress localhost:0
that's brilliant!  about as responsive as a freight train, but at least it's more secure than forwarding 5900 to the front door of a user end system.

and with a local linux server in the loop, you could easily and relatively securely connect to a windows system.  both ends would need gigabit local networks and blindingly fast fiber service to make it tolerable for any length of time, but at least do-able.

i've always known that this was a possibility, but i've never seen the commands for it.  

@JayTee ... sorry man, sometimes i can't resist a little hyperbole. lol.

oh yeah, almost forgot.

@shanepardue ... been jonezin for some [arthur bryants]("http://www.arthurbryantsbbq.com/") for ages now :(

---

### Post by shanepardue on 2006-11-03
Thanks for the tips guys! I think I would have to disagree with some of the 
comments mentioned on the security of it though. I believe that with 
encryption (ssh for example) would allow for a safe vnc experience.

---

### Post by Joeak on 2006-11-04
You can also set up openssh on Windows.  Some people do it with Cygwin manually (load Cygwin, then load openssh).  I found some precompiled Windows binaries that had limited Cygwin installs and Openssh already compiled.  [www.openssh.org]("http://www.openssh.org"), [sshwindows.sourceforge.net]("http://sshwindows.sourceforge.net")

---

### Post by AHS on 2006-11-09
Hi I am a newbie and I just download Ubuntu. I set up System->Preference->Remote Desktop for remote access and the least I can do is to check out the log file and make sure there's no abnormal activites (no one is trying to break in). Does anyone know where the log is located?

Thx,
AHS

---

