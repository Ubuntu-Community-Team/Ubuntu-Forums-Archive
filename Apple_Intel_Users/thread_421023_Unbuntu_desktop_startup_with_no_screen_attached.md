---
title: "Unbuntu desktop startup with no screen attached"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by Eguun on 2007-04-24
Hello Team,

I have freshly installed Unbuntu 7.04 on an Intel based Mac Mini. All installation worked flawlessly, system configuration is OK and it is now up and running without issue. I must emphasis on how amazed I was to discover this distribution, fully packaged and very lambda-user friendly.


My issue is when I unplug keyboard mouse and screen, the system will not start (it stops before the Ubuntu splash screen loadup). This is however how I intent to use this system: networked without peripherial and take control remotely with command line and graphical interface.
After some trial and error, I established that the system doesn't mind to miss keyboard and mouse, but needs a screen - I guess this is for the X server.

Is there a way to force the system to load even without a screen (i.e.: by hardcoding the screen characteristics in some config file and bypassing the auto detection)?

Any help here will be very appreciated: I have looked into google, help forums and mailing list (based on Ubuntu systems and generic X server), and cannot find a solution.

Cheers

---

### Post by magic-neophyte on 2007-04-24
Hi,

I read something somewhere ([www.mac123.com???](www.mac123.com???)) that you could use an electronic part to fool the DVI exit on the Mac Mini into thinking that an adapter is plugged in. There were pictures too. The article was about using the Mac Mini as a server. I got there from [www.apple.com/macmini](www.apple.com/macmini) through the links about the odd ways people were using mac mini at the bottom right hand of the page, but I cannot remember which and I have no time now.

Not much but hope it helps,

Magic Neophyte

---

### Post by Eguun on 2007-04-24
Thanks for the quick answer,

Based on your input, here's what I found: the device that connects the DVI cable to TV is described in this howto: [http://www.howtogeek.com/howto/apple/use-your-mac-mini-as-a-media-server-part-1/](http://www.howtogeek.com/howto/apple/use-your-mac-mini-as-a-media-server-part-1/)

and can be aquired here: [http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore?productLearnMore=M9267G/A](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore?productLearnMore=M9267G/A)


One thing bothers me though: if aquired and plugged, I will not connect a TV behind this adaptor, and I fear the system could still miss a screen and I'm left with the same issue.


Is there no software solution to force sending X server signal to a graphic card output no matter whether a screen is plugged in or not?


Cheers

---

### Post by Eguun on 2007-04-24
Hi team,

I made further research and came accross the following:

- On Ubuntu forums a bug has been notified for Mac Mini unable to boot without a screen.
Good news: a solution has been provided, bad news: I am not competent enough to know how to use it for my config
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/51519](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/51519)

- one level uglier is to solder a 75 Ohm resistor on a VGA plug to make the mac mini believe a screen is attached:
[http://www.mythic-beasts.com/support/macminicolo_howto.html](http://www.mythic-beasts.com/support/macminicolo_howto.html)

Please guys is there anyone else who made it happened to have mac mini run without a screen? I need input to get out of this hole.

Cheers

---

### Post by ronocdh on 2007-04-24
> **Eguun said:**
> Thanks for the quick answer,

Based on your input, here's what I found: the device that connects the DVI cable to TV is described in this howto: [http://www.howtogeek.com/howto/apple/use-your-mac-mini-as-a-media-server-part-1/](http://www.howtogeek.com/howto/apple/use-your-mac-mini-as-a-media-server-part-1/)

and can be aquired here: [http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore?productLearnMore=M9267G/A](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore?productLearnMore=M9267G/A)


One thing bothers me though: if aquired and plugged, I will not connect a TV behind this adaptor, and I fear the system could still miss a screen and I'm left with the same issue.


Is there no software solution to force sending X server signal to a graphic card output no matter whether a screen is plugged in or not?


Cheers
If you are comfortable with the command line interface already, I think the Server Edition (which does not have a GUI) might work well for you. As I understand it, you could access your Mac Mini with Ubuntu SE over a network, using a separate box with a GUI and communicating via command line.

Perhaps I miss understood the last line in your post I've quoted, but I don't see the logic in sending any X signal at all if you don't have a screen hooked up. You mean you want the X server output sent through the network, so you can view the Mac Mini desktop on a separate box, in a sense? I've no experience there, but try the Networking and also the Multimedia forums; they should be full of people who have tried similar things.

---

### Post by Eguun on 2007-04-24
Hi ronocdh,

Thanks mate. Quite rightly that last sentence deserve some bit of clarification.

The blocking factor that prevent the mini mac from booting is the lack of screen. Further up in the discussion thread, we've established that missing a screen is lethal for X server to load.

So the essence of my request was to find a software solution to force a signal to be sent in this graphic card, no matter if a screen is there or not, enabling the system to start. And once the workstation is loaded OK, to take control with VNC.

Software solution, as opposed to the hardware one: either by acquiring a converter, or by building a dongle with a 75 Ohm resistor (see previous posts).

Server edition is fine but without gui, it's sadly out of my needs: I'm very keen into keeping this mac mini as a VNC server box.
The alternative to VNC is a XDMCP client for X server, but it runs over UDP so cannot be secured by SSH. If you want to go for a secure solution, my understanding is that you'll only be able to summon window by window on your client - not get the whole desktop at once.
At my humble opinion, VNC over SSH is simple to setup and use and doesn't force me to tradeoff user-friendlyness over security.

Really I'd very much like to keep desktop edition, and find a software solution to enable this mini mac to boot without a screen.

I posted this request here, because it's platform related more than usage bound: our friends from OpenBSD are facing the very same issue.
[http://erdelynet.com/tech/openbsd/openbsd-on-intel-mac-mini/](http://erdelynet.com/tech/openbsd/openbsd-on-intel-mac-mini/)

I understand my request here is very borderline with Ubuntu support: it's not directly related to Ubuntu usage, which works fine. It's more targeted on Ubuntu Mac users to gather feedback whether someone suceeded in this task.

I'll be more than happy to try the suggested solution reported on my previous post if someone can give me a hand to understand the command and where to copy/paste it:

Quote from [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/51519](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/51519)
The kernel boots adding this option to the boot line:
video=radeonfb:ignore_edid
/quote

Cheers

---

### Post by Eguun on 2007-04-25
hi guys,

Final note on this thread: I went for the hardware solution, so to use a 75 Ohm resistor to have the mac mini running headless.
Based on various forums, this seems as of today the only valid solution.

For those facing similar issues and willing to go this route, please note this is a very cheap solution (count 0.10 euro for the resistor), and very easy to implement.

Here under a link to a forum (with pictures) where users just planted the resistor on VGA and DVI plugs, without even soldering:
[http://sneezr.net/](http://sneezr.net/)

Thanks for your suggestions, this problem is solved.

---

### Post by ronocdh on 2007-04-25
> **Eguun said:**
> hi guys,

Final note on this thread: I went for the hardware solution, so to use a 75 Ohm resistor to have the mac mini running headless.
Based on various forums, this seems as of today the only valid solution.

For those facing similar issues and willing to go this route, please note this is a very cheap solution (count 0.10 euro for the resistor), and very easy to implement.

Here under a link to a forum (with pictures) where users just planted the resistor on VGA and DVI plugs, without even soldering:
[http://sneezr.net/](http://sneezr.net/)

Thanks for your suggestions, this problem is solved.
Hey, congratulations! And thanks very much for posting back; hopefully someone searching will find the issue here and experience happy resolution. =)

Funny that such a kludge is necessary, but at least it works!

Edit: adding keywords for anyone searching, just to raise the chances: 
mac mini no monitor headless 75 ohm resistor screenless without a monitor

---

