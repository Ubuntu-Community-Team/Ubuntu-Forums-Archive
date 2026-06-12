---
title: "VNC into Windows XP"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Loonux on 2007-02-11
I have VNC Server (tightvnc) running on all the windows machines on my LAN, and would like to be able to connect to these from my kubuntu 6.10 laptop.
Im surpised to see there is no vnc viewer installed by default but just wondered what is the easiest way to connect to my existing VNC setup from this laptop?

Any ideas on a good vnc client to use/install that is compatible with kubuntu and my existing tight VNC server installs?
Thanks

---

### Post by KAL9000 on 2007-02-11
I found out that it has a server. but havent seen a preinstalled client. I use Ultr@VNC personaly and at some point will look to see if its on the package manager, if not then look on the website of your choise and see if they have a Linux version listed.

---

### Post by Ek0nomik on 2007-02-24
I have the same problem.  I'd appreciate any feedback on how to control a Windows XP computer from Ubuntu.

---

### Post by irish_flu on 2007-02-24
> **Ek0nomik said:**
> I have the same problem.  I'd appreciate any feedback on how to control a Windows XP computer from Ubuntu.


You're asking a different question than the original poster was, as that person has installed extra software called VNC on the Windows boxes.

If you want to control a Windows 2000, Windows XP, Windows Server 2003, or Windows Vista box then there's already software installed by default in Ubuntu that can do that for you.

It's called "Terminal Server Client" and it works just like "remote Desktop Connection" in Windows.  You must make sure that your Windows machine is set up to accept incoming Remote Desktop requests from whatever user you wish to use, but other than that you're golden.

---

### Post by Ek0nomik on 2007-02-24
> **irish_flu said:**
> You're asking a different question than the original poster was, as that person has installed extra software called VNC on the Windows boxes.

If you want to control a Windows 2000, Windows XP, Windows Server 2003, or Windows Vista box then there's already software installed by default in Ubuntu that can do that for you.

It's called "Terminal Server Client" and it works just like "remote Desktop Connection" in Windows.  You must make sure that your Windows machine is set up to accept incoming Remote Desktop requests from whatever user you wish to use, but other than that you're golden.

I don't want to use the default Windows Remote Desktop though.  I currently use UltraVNC as a server, and UltraVNC viewer on my laptop to control them.  The built in Windows Remote Desktop logs you out of your session.  Any ideas?

---

### Post by irish_flu on 2007-02-24
Ah.  sorry, I didn't know you were using VNC on your Windows boxes.  I have never used tsclient as a VC client, although I see that it's a choice when you're making a connection....

Have you tried out "vncviewer"?  It's available through the Repositories.

---

### Post by mgmiller on 2007-02-24
I have used the terminal server client to control a windows XP pro machine running tight VNC.  I just selected the vnc option in TSC and it hooked right up, no problems.  The fellow at the other end could see everything I was doing.  Worked like a charm.

---

### Post by Ek0nomik on 2007-02-24
> **irish_flu said:**
> Ah.  sorry, I didn't know you were using VNC on your Windows boxes.  I have never used tsclient as a VC client, although I see that it's a choice when you're making a connection....

Have you tried out "vncviewer"?  It's available through the Repositories.

I tried Terminal Server Client, as I had before.  The Windows XP Professional box running UltraVNC Server.  I chose my connection as VNC, and put in my IP.  This is what I get:

VNC viewer version 3.3.7 - built Jul 4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
see [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocal version 3.4 (viewer 3.3)
Unknowne authentication scheme from VNC server: -6

I have no idea what those details mean, but that's what I got.  I left the Domain, Client Hostname, and Protocol File options blank.  On my UltraVNC server, I have it make the connector type in the username and password of the account, but I tried removing that and connecting and still no dice.

When you refer to vncviewer in the repositories, do you mean through the Synaptic Package Manager?  How do I install it?

---

### Post by irish_flu on 2007-02-24
I opened Synaptic and did a search for "vncviewer".

You can also go to a terminal and type "sudo aptitude install vncviewer".

What I'm truly not sure of, though, is whether or not tsclient is already acting as a front-end for the same piece of software....

---

### Post by Ek0nomik on 2007-02-24
Alright, well, new news.

I took off the MS Logon Requirement on UltraVNC Server, and I was able to connect to my Windows Box through Ubuntu.

So, while it was able to work, I still had a bit of an issue.

[IMG]http://webpages.charter.net/muznic/Screenshot.png[/IMG]

Do you see the solid black rectangles where I should be able to scroll?  What's up with that?  After I move either the horizontal or vertical scrollbar even once, I can't move it again.  Any ideas?

**Edit**:  Sorry I didn't resize image, I don't know the BBCode to do it.

---

### Post by Ek0nomik on 2007-02-24
> **irish_flu said:**
> I opened Synaptic and did a search for "vncviewer".

You can also go to a terminal and type "sudo aptitude install vncviewer".

What I'm truly not sure of, though, is whether or not tsclient is already acting as a front-end for the same piece of software....

In the Terminal, I typed vncviewer.  It prompted me for a username and password, and I connected.  (Still the black box problem).  Also, when I use TSClient, it appears to look exactly the same as vncviewer.  So, I don't know much about "front-ends" on software (if you could explain more I'd appreciate it), but from my guess it appears it acts as the front-end.  The TSClient and VNCViewer produce the same GUI from the looks of it.

Regarding the black box, here is the output from the terminal after I ran vncviewer in it:

```
fleur@fleur-laptop:~$ vncviewer
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See http://www.realvnc.com for information on VNC.
VNC server supports protocol version 3.6 (viewer 3.3)
VNC authentication succeeded
Desktop name "love ( 137.28.247.127 )"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Using default colormap and visual, TrueColor, depth 24.
Got 256 exact BGR233 colours out of 256
Using BGR233 pixel format:
  8 bits per pixel.
  True colour: max red 7 green 7 blue 3, shift red 0 green 3 blue 6
Using shared memory PutImage
Throughput 6519 kbit/s - changing from 8bit
Using viewer's native pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Throughput 10334 kbit/s - changing to Hextile
ShmCleanup called

```

Also, I used to know a way you could run a program without it taking away your usability of the terminal.  How do you do that?

Thanks!

---

### Post by stupid head on 2007-02-24
It's also possible for you to use the UltraVNC client through Wine. That allows you to take advantage of UltraVNC-specific features like encryption.

---

### Post by Ek0nomik on 2007-02-24
Thanks for that suggestion!

I'll have to try Wine.  I have never done it before.

---

### Post by bmt on 2007-02-26
... and the weird scrollbars can be improved by using xvnc4viewer -- also in the repositories -- instead.

---

### Post by houstonbofh on 2007-02-26
The TS client uses vncviewer.  They are installed by default.  The Windows logon thing is a Windows thing...  Hard for us to fix.  The black scrollbar I have seen before, but not every time.  I don't know.

To launch a program but keep useing your term, "vncviewer&" however, if you close the term, you loose your vnc.  Also hitting alt-F2 gives you a run box.

---

### Post by Ek0nomik on 2007-02-26
> **bmt said:**
> ... and the weird scrollbars can be improved by using xvnc4viewer -- also in the repositories -- instead.

Awesome.  xvnc4viewer seems like a much better application than the default install one.  Thanks a lot!

---

### Post by jm2003uk on 2007-02-26
I'm just trying out xvn4cviewer (running it in the console so i can see any output messages). When i type in the ip address, i get a message saying that its connected to the host.....but nothing else happens. I've tried a few other clients and they all do the same :confused:. Anyone got any suggestions on whats wrong? (probably something i've done, lol)

---

### Post by Ek0nomik on 2007-02-26
What Windows VNC Server are you using?

I use UltraVNC 1.0.2 Server.

Also, post your output from the Terminal into the forum.

---

