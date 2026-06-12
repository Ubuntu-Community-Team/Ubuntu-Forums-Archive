---
title: "Keep getting 'can't open display' for whatever remote client i try"
date: 2016-01-24
forum: Any Other OS
---

### Post by martin183 on 2016-01-24
I am not using ubuntu but tinycore linux. I am desperate and the forums over there are abandoned from what I can tell so I posted here so that maybe I'd get a response. I installed command line only install so had to install X etc manually. 

I kept getting that message 'can't open display' on the tinycore command line. I tried with tight vnc and rdesktop. 

  I have installed the xstart thing and now the core install loads into  the desktop by default. As a side note how do I stop that? I want x for  rdp etc but i still want to boot into core and load X only as needed. 
  Anyhow I was reading an article which said:[INDENT] If you have problems the first thing to do is to see the value of the  variable DISPLAY on the client. If it is not set at all or set  incorrectly you need to fix that, for example
  export DISPLAY=10.10.10.1:0.0
 [/INDENT]
So I put that line into the command line. Then I tried the clients  again. Now it seems to hang for like two mins on the pressing of return  but eventually it just returned: ERROR: Failed to open display: 10.10.10.1:0.0
  What should I do now?
  btw I'm trying to connect to windows 8.1. I initially tried with rdp/rdesktop but tightvnc is looking more appealing to me now.
  oh yes I also tried running both from within the startx gui. rdesktop  gave me another errror of could not connect or similar and tightvnc  just dissappeared after I entered the server ip and nothing else  happened.


I try and connect via rdesktop gui and get: Error: connect: Network is unreachable.
  I try in to use both the public ip address and the local one that shows in ip config.
  I tried putting: DISPLAY=myactualipofserver:1 and also DISPLAY=myactualipofserver:5901
Also export DISPLAY=myactualipofserver:0
  All that did was change the can't open display to the ip I changed it  to. Am I supposed to be putting the ip of the server I'm trying to  connect to? which is what I did above?
  I also tried xvhost + and that did nothing.
  What to try next?

I feel like I am grasping at straws as I've been looking online all day and have no idea if I'm even searching in the right direction. I'm getting a bit fed up with tinycore's 'hardcorenes' now. I thought it would be a nice challenge but I'm almost ready to throw in the towel and install a better supported distro like arch. I did get this far tho so I am making a last effort.

---

### Post by howefield on 2016-01-25
Thread moved to the "*Any Other OS*" sub forum.

---

### Post by Bashing-om on 2016-01-25
martin183; Hello,

Hey, I have but limited experience with tinycore, and even less with Windows - however......
I do know in a minimal install it is on you what is installed, and for a display ( GUI) to be available we must install in debian the package "xorg".
You advise :
> 
I installed command line only install so had to install X etc manually.
 but fail to say what you installed.

Is 'X' available ? 
```

dpkg -l xorg

```

As a place to start the trouble shooting .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

