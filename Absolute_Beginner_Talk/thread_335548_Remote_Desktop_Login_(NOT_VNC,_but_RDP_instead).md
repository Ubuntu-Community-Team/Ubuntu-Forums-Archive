---
title: "Remote Desktop Login (NOT VNC, but RDP instead)"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2007-01-10
Hello All!

I know that this topic is always popping up in the forums, but I havn't been able to quickly find a solution to what I would like.

I have two Ubuntu PC's now on my internal network connected with a linksys router.  I would like to be able to login to Ubuntu from my laptop to my desktop without kicking my wife off.  In other words, I would like to login to the desktop machine with my own UN and PW and still get the GUI without disrupting the current destkop user.  So, no VNC on this one (VNC works, it's just not what I want).

On Windows, it's pretty standard to have more than one concurrent user (with a bit of a hack on XP Pro of course).  I've done this before and it's extremely helpful.  I believe the protocol is RDP or RDC (I get them confused).

Is there a way to do this with Ubuntu?  I've heard of ssh -x to get the GUI, but I would like to hear what options I have.

Thank you in advanced for the help.  Again, sorry about bringing this up for the 1000th time.

---

### Post by moeFinley on 2007-01-10
RDP (Remote Desktop Protocol) is the XP protocol.  You can use this with [Gnome-RDP]("http://gnome-rdp.linuxforge.hu/").  But I don't know about multiple users. :-k

---

### Post by SendDerek on 2007-01-10
Thank you very much.  This sounds like what I was needing.

Is there anybody who can confirm the ability to have multiple users?

---

### Post by hal10000 on 2007-01-10
Do I understand you well???, you want to login to your desktop and get your own gnome or kde or whatever to your laptop?

If so, then you need a server that provides this on your desktop's side, so why not vnc? You might install vino, which is a vnc server for the GNOME desktop.

On the client side (your laptop) you might install then Gnome-RDP or another remote clent program to get a connection to your desktop.

With vnc (on the server side) I'm almost sure you can get multiple cononections.

If you just want to run progarms which are nistalled on your desktop computer, then you don't need vncserver or rdp, just typing [COLOR="Red"]ssh -X yourname@yourdesktop[/COLOR] (Note: this is an upper case X) and from the appearing terminal you can run any program you like.

---

### Post by steve.horsley on 2007-01-10
Ubuntu cannot serve RDP. It only has an RDP client. 

To remote-control an Ubuntu server, there are 3 possibilities:

1) VNC
Vino is a VNC server that you run within a GUI and it serves the current desktop. This is the way VNCserver works on windows - not what you want. But vnc4server package serves a different (headless) desktop, so this package will probably do what you want, except I have never been able to make it work.

2)
freenx from [http://www.nomachine.com/](http://www.nomachine.com/) - the server is afree download for Linux, and clients are free for Linux and Windows. I haven't tried it, but have seen good reports on performance.

3)
An X server on windows will allow Linux to use its native Xwindows protocol. There are lots of X server packaged for windows.

---

### Post by seuaniu on 2007-01-10
I've gotten this done with xdmcp. 

System --> Administration ---> Login window ---> Remote tab.

Change the drop-down box from "Remote Login Disabled" to something else (any will do).  This should start up the xdmcp server. 

Start up the same config program on your laptop.  On the "Local" tab, Check the boxes for "Show Actions Menu" and "Include Hostname Chooser (XDMCP) Menu Item".  When you login, there'll be a menu item to search for other computers to login to.  Your main machine should show up on the list after a minute.  Choose that, and login normally.  

I do this over an 802.11b connection (slow!) and can get a usable desktop, but certainly not video or games.  Even flash animations run really slow, so its a bit limited.  If you're on a faster connection you might get better results.

Good luck!

---

### Post by SendDerek on 2007-01-10
> **seuaniu said:**
> I've gotten this done with xdmcp. 

System --> Administration ---> Login window ---> Remote tab.

Change the drop-down box from "Remote Login Disabled" to something else (any will do).  This should start up the xdmcp server. 

Start up the same config program on your laptop.  On the "Local" tab, Check the boxes for "Show Actions Menu" and "Include Hostname Chooser (XDMCP) Menu Item".  When you login, there'll be a menu item to search for other computers to login to.  Your main machine should show up on the list after a minute.  Choose that, and login normally.  

I do this over an 802.11b connection (slow!) and can get a usable desktop, but certainly not video or games.  Even flash animations run really slow, so its a bit limited.  If you're on a faster connection you might get better results.

Good luck!

Perfect!  :D 

I'm excited to try this out as soon as I get home.  


@hal10000:

Just to clarify, 2 computers are connected via router.  One laptop (mine) one desktop (wife's).  Sometimes, I would like to be able to use her computer through mine (Remote Desktop) without disrupting her.  A VNC connection where I control her mouse is definately going to disrupt her.  So, I setup another account on her machine where I can login to the same computer concurrently while she is still logged.  So, now, two users are signed onto the same computer running totally different sessions.  This is similar to Microsoft's RDP and Terminal Services.

Is that a little clearer?

---

### Post by hal10000 on 2007-01-10
Ok, i just got it, thanks.

---

### Post by SendDerek on 2007-01-11
Okay, great.  So using XDMCP was pretty much exactly what I wanted.  It would be nice if I could get it in a nested window instead of having to switch users.  But, it went very well.  Thank you for that advice.

So, that takes care of a ubuntu -> ubuntu Remote login connection, what about a windows -> ubuntu Remote login connection?

Thanks for any help in advanced.

---

### Post by seuaniu on 2007-01-11
> **SendDerek said:**
> Okay, great.  So using XDMCP was pretty much exactly what I wanted.  It would be nice if I could get it in a nested window instead of having to switch users.  But, it went very well.  Thank you for that advice.

So, that takes care of a ubuntu -> ubuntu Remote login connection, what about a windows -> ubuntu Remote login connection?

Thanks for any help in advanced.

Your welcome :)

I'm not sure if there's an xdmcp client that exists for free (or at all) for windows, but there is a freenx client available.  Freenx is a bit like vnc, and a little bit like xdmcp, and faster than both.  It will allow two people to be logged into the same computer at the same time, ala xdmcp.  I didn't bring it up before since xdmcp is the simplest answer to the problem.  Freenx also has the advantage of being able to run over ssh, so the connection is encrypted and suitable for transmission over the internet.   You can also run it in a window.  My understanding is that it will not run with beryl, but i may be wrong about that.

[Here's a good thread to get you started.]("http://www.ubuntuforums.org/showthread.php?t=1968&highlight=freenx+howto")

---

### Post by charon79m on 2007-01-17
You can get a nested window.  Your Terminal Server Client under Appplication and Internet has the ability to do XDMCP in a nested window.  I believe the only package you need to add for this is xnest.

Mike K.

---

### Post by hal10000 on 2007-01-17
Freenx (client and server appl.) can easily be tested if you have (recent) knoppix live-cd. You can then test it without installing on your main system.

---

### Post by SendDerek on 2007-01-22
> **charon79m said:**
> You can get a nested window.  Your Terminal Server Client under Appplication and Internet has the ability to do XDMCP in a nested window.  I believe the only package you need to add for this is xnest.

Mike K.

Thank you very much for the suggestion!  I installed xnest and it works perfectly!  Thank you!

---

### Post by Endolith on 2007-02-10
> **seuaniu said:**
> I'm not sure if there's an xdmcp client that exists for free (or at all) for windows[/url]

[Cygwin/X]("http://en.wikipedia.org/wiki/Cygwin/X"), [Xming]("http://en.wikipedia.org/wiki/Xming"), [WeirdMind]("http://www.tam.cornell.edu/Computer.old/remoteaccess/weirdmind/") and [WeirdX]("http://en.wikipedia.org/wiki/WeirdX")

I have had the best results with Xming, though I'm still trying to figure out how to get it to work.  :-)

---

