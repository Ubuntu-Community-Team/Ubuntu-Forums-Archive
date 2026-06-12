---
title: "Linux Mint 14, Tor Browser Not Working or Loading"
date: 2013-03-24
forum: Any Other OS
---

### Post by ProxyCyber on 2013-03-24
So I'm using Linux Mint 14, and it wouldn't work when I extracted and clicked "RUN" for "Start Tor Browser." All it said was "Vidalia exited abnormally.  Exit code: 127" Can you help me fix this?

---

### Post by Perfect Storm on 2013-03-24
Moved to Other OS/Distro Talk.

---

### Post by ProxyCyber on 2013-03-25
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

Ok, so you moved my topic.... Where are the answers?

---

### Post by cortman on 2013-03-25
Be patient, especially as you're asking this in an Ubuntu forum. You will probably have better luck getting Mint questions answered in a Mint forum.
I don't know how to fix Vidalia from the small amount of information you provided, but do know that you can use a normal browser with Tor as well- just set the SOCKS5 proxy address to 127.0.0.1 and the port to 9050 and you should be up and running.

---

### Post by mips on 2013-03-26
You really don't provide much information. 
Running 32 or 64 bit Mint?
Did you install it from the repos or download it from the tor webseite?
Was it the tor bundle?
Which version?
32 or 64 bit?
Did you extract it to your home folder?
How are you launching it?

It has a debug mode you can invoke with, ([COLOR=#ff0000]Warning, [FONT=Verdana]the --debug option logs every hostname Tor connects to to disk!!![/FONT][/COLOR][COLOR=#000000][FONT=Verdana])[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Verdana]./start-tor-browser --debug[/FONT][/COLOR]
```

---

