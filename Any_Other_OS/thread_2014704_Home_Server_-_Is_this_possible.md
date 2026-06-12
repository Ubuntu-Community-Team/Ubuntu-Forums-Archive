---
title: "Home Server - Is this possible?"
date: 2012-07-02
forum: Any Other OS
---

### Post by ghandi69_ on 2012-07-02
Hello folks!

This is not an ubuntu question necessarily, but was hoping to at least spark a discussion.

With companies like OnLive and Splashtop beginning to show what can be done with remote desktop.. I am beginning to see how I would want my future home computer setup to look.

I would want a headless... home server that would be as performance capable as possible (up to date.. fast processer... lots of ram.. etc etc) This home server would likely run windows for the following reasons.. 

- Hardware intensive software performance (Photoshop, videogames, video editiors, etc etc)
- Driver support to run above mentioned software

This would give me the freedom to to choose any OS (ubuntu laptop, macbook air, etc) for my 'everyday usage' for e-mail, web browsing and so on.  Having this setup would also be nice because most hardware upgrades could be focused on the server machine... and I could pick my personal products based more on screen quality, form factor, and asthetics. 

I would want the ability to remote login into my server to do the following..

- play graphic intensive games (starcraft 2 for example)
- use 'professional' type software (photoshop for example)
- be able to stream sound/music

The current issue is that remote desktop has never been well suited for fast motion video or providing sound... which I would want.  

Assume within reasonable limits that I could have hard wired, fast ethernet connections made to his machine.

What type of software is available to allow me to do this?  Has anyone tried Splashtop?

---

### Post by Dlambert on 2012-07-02
So my understanding is that you wish to USE the server as a PC as well (for gaming and what not) but also have it run serves for your house?

---

### Post by ghandi69_ on 2012-07-02
> **Dlambert said:**
> So my understanding is that you wish to USE the server as a PC as well (for gaming and what not) but also have it run serves for your house?

Negative.

Ideally the server would be headless... and everything I use it for would be through a remote desktop of sorts.  

I envision the super powerful server in the basement... Then I would run a really cheap PC... hooked up to a really nice monitor.  I would use the cheap PC for web browsing and day to day tasks... but I would log in to use more compuatational intensive applications.

This also mixes well the the new 'multiple mobile device' trend that is happening.

Lets pretend I have a mac mini at my desk... a ubuntu laptop... and a tablet of some sorts.. I could remote desktop into the server with any of the devices and run intensive applications.

The nice part about it.. is I would then choose my personal devices based solely on design and screen quality.. and not have to worry about processor and performance as much.

Upgrading the server would then also improve my expereience while using any of the other devices.

---

### Post by ghandi69_ on 2012-07-04
Thought I would try to help myself here.

Do you think I am not getting many responses because this isn't possible yet?

Or.. do you think people just think its a dumb idea?

Or.. am I not doing a good job of explaining what I'm trying to do?

Any advice would be appreciated.

---

### Post by insane_alien on 2012-07-04
playing a videogame remotely is going to be a whole mess of lag. especially if its graphics intensive.

if your going to be doing something that is dependant on low latency interaction you'll be far better off doing it locally rather than remotely. even if you do have a future 100G ethernet connection between them

---

### Post by cipherboy_loc on 2012-07-04
With a big enough intranet capabilities, it should be doable. While this namely would only work Linux/Unix to Linux/Unix, try a ssh tunnel. When running Armagetron normally (i.e. no remote desktop), it uses 20-50% CPU, however tunneling it via ssh puts it between 10-15%. This is probably because actual display of graphics is offloaded to the client (i.e., a mac laptop in this case) versus the server. 

BTW, my server in this example is by no means powerful, but there is a gigabit intranet (wired to router, then wireless to mac). No doubt wired to wired would be faster for more intense games.. 

Two players actively playing armagetron off of the same system. I am tunneling mine via ssh, user is running on the desktop. 
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 6318 user      20   0  144m  22m  11m S 52.7  0.8   6:04.56 armagetronad.re
     7054 cipherbo  20   0 53288  14m 8628 S 10.4  0.5   0:59.16 armagetronad.re    

```

Cipherboy

---

### Post by ghandi69_ on 2012-07-05
> **insane_alien said:**
> playing a videogame remotely is going to be a whole mess of lag. especially if its graphics intensive.

if your going to be doing something that is dependant on low latency interaction you'll be far better off doing it locally rather than remotely. even if you do have a future 100G ethernet connection between them

I agree that the normal methods of doing this with VNC and such provides subpar performance.

However, there a few things that suggest that this is by no means a bandwidth limitation but instead... a protocol problem.

1. OnLive, using some clever compression methods.. lets you play close to lag free games from a server not even located in your own home.  Including sound.  I've used OnLive.. and the performance they have achieved would be suitable for me. (But.. unfortuantely... OnLive is limited to just games..)

2. Another method that would work would be to setup a twitch.tv stream from the server in your house.  You could then log into Twitch.Tv on the remote computer... and watch the Twitch.tv stream coming the computer in your own house.  I've tried this and it actually doesn't work too bad.  The main issue with this however.. is that you need to have a directly connected mouse and keyboard.. and my wireless devices only reach so far.

I'm hoping the above two methods at least show that this type of setup is technically possible...  but as far as I know know there has not been software written to fulfill this need.

---

### Post by ghandi69_ on 2012-07-05
> **cipherboy_loc said:**
> With a big enough intranet capabilities, it should be doable. While this namely would only work Linux/Unix to Linux/Unix, try a ssh tunnel. When running Armagetron normally (i.e. no remote desktop), it uses 20-50% CPU, however tunneling it via ssh puts it between 10-15%. This is probably because actual display of graphics is offloaded to the client (i.e., a mac laptop in this case) versus the server. 

BTW, my server in this example is by no means powerful, but there is a gigabit intranet (wired to router, then wireless to mac). No doubt wired to wired would be faster for more intense games.. 

Two players actively playing armagetron off of the same system. I am tunneling mine via ssh, user is running on the desktop. 
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 6318 user      20   0  144m  22m  11m S 52.7  0.8   6:04.56 armagetronad.re
     7054 cipherbo  20   0 53288  14m 8628 S 10.4  0.5   0:59.16 armagetronad.re    

```

Cipherboy

During my online reading I have read that X11 forwarding is a much more efficient protocol than VNC, so this make sense.  I will admit however... at this point, I'm leaning heavily towards Windows due to my current investment in software I wish to use (Games, Photoshop, etc)

If it turns out that this is the only acceptable method.. I would probably looking into the long term learning of open source tools and seeing if the few games I play run well in Linux or Mac, and go from there.

---

### Post by cipherboy_loc on 2012-07-05
In theory you should be able to tunnel VirtualBox (assuming you have a server that can handle vbox emulating windows playing a game) over SSH. Haven't tried it yet, somebody want to give it a whirl? Also, try using wine and see if that works. 

Cipherboy

---

### Post by ghandi69_ on 2012-07-05
> **cipherboy_loc said:**
> In theory you should be able to tunnel VirtualBox (assuming you have a server that can handle vbox emulating windows playing a game) over SSH. Haven't tried it yet, somebody want to give it a whirl? Also, try using wine and see if that works. 

Cipherboy

I could probably test that out with the PC's I have now.  Fits in with the overall idea a little because the the idea make the sever as fast as possible.. so it might be able to handle games and such.  However.. can you get sound this way too?

---

### Post by cipherboy_loc on 2012-07-05
It looks like you would have to forward sound separately:
[http://superuser.com/questions/231920/forwarding-audio-like-x-in-ssh](http://superuser.com/questions/231920/forwarding-audio-like-x-in-ssh)'

I have a Mac that is up to the job of running VirtualBox, going to try and forward it from there. Audio will be an issue trying, as the rest of my computers are Macs... Wonder if I can get it to run from an Ubuntu VirtualBox image on one of them.

Cipherboy

---

### Post by ghandi69_ on 2012-07-05
> **cipherboy_loc said:**
> It looks like you would have to forward sound separately:
[http://superuser.com/questions/231920/forwarding-audio-like-x-in-ssh](http://superuser.com/questions/231920/forwarding-audio-like-x-in-ssh)'

I have a Mac that is up to the job of running VirtualBox, going to try and forward it from there. Audio will be an issue trying, as the rest of my computers are Macs... Wonder if I can get it to run from an Ubuntu VirtualBox image on one of them.

Cipherboy

Cool.

I have a Mac Mini as a HTPC, and a Windows laptop.  I'm installing a Virtual Box of Ubuntu on my Win Laptop, and will try connecting via X11 to the mac.

Two different methods we'll see how it goes.

---

