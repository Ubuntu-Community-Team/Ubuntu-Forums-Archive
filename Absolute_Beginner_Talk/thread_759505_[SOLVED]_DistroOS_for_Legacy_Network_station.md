---
title: "[SOLVED] Distro/OS for Legacy Network station?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by JohnLM_the_Ghost on 2008-04-19
Hello!
I want to build a little server / network station on my old (as hell) PC.
Specs goes:
```
Pentium 100Mhz (no MMX)
32Mb RAM
1MB Video
```

I'm now running [DSL]("http://www.damnsmalllinux.org/") and Win95 as dual-boot on it. 

I'm not really a network expert and not definitely Linux expert, but I know my way around.
I want to know what OS or Distro and programs should I use on it. GUI is not required and I want it to do following tasks:
[LIST]
[*]Act as FTP Server
[*]Run Backburner Manager through Wine in CLI (I dunno if it is possible though)
[*]Act as Web Server (optionally)
[*]Communicate with other PC's through SMB.
[*]and other optional network related stuff.
[/LIST]

The networking won't have lots of traffic, so it should do it pretty good.
I also want FTP to share files on other PC's on the network.

Just in case... Backburner Manager is software which queues and assigns 3ds Max's render jobs to Render Servers. I just need to run it and that's it. I don't need it to show any window and all interaction would be done remotely with Backburner Queue Monitor Utility.

So If you have any ideas how to achieve this, let me know!
Thanks!

---

### Post by schiznik on 2008-04-19
use the debian netinstall image. 

I dont whether the wine/cli stuff is possible at all, the rest should be ok

---

### Post by JohnLM_the_Ghost on 2008-04-20
Thanks! 
Though what is it and where do I get it?

And I did some research and it turns out it is potentially possible to run 'Windows console programs' in CLI with Wine. But I Don't know how (yet).

---

### Post by JohnLM_the_Ghost on 2008-05-30
Well it is quite good! I wish it could take a little less space on my already small HDD, but it ain't a big problem.

EDIT: So I use Debian Etch (CLI interface) for my File Server.

Solved!

---

