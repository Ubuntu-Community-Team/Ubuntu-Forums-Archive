---
title: "VNCviewer (remote desktop client) problem: keyboard not working at password prompt"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by econmit on 2007-10-23
Using ubuntu 7.10. 

I have the following problem in the VNCviewer (remote desktop). Oddly it only occurs when I have the visuals set to Normal or Extras (i.e. compiz enabled)

If I try to connect to a server then I get the password prompt but the keyboard does not respond. 

The problem is not that I do not get visual feedback of typing in my password! For example, I hit enter and nothing. So I literally cannot enter my password and login.

The same problem does not occur if I have the visuals off.

Any ideas.

---

### Post by evilregis on 2007-10-23
What system are you using to VNC into your Ubuntu machine?  Windows?  Another Linux machine?  If it's Windows perhaps try a different VNC client?  RealVNC, TightVNC, UltraVNC are a few...

---

### Post by wyth on 2007-10-23
I have the same issue -- and the default VNC viewer is xvncviewer.

I found if I click on another window alongside -- but not covering -- the login prompt, and then click back to the login prompt, I can type in anything.

But yeah, it's an annoying little problem.  It happens when entering the IP address and the password. I didn't try it outside of Compiz, so I don't know if it's an issue with that, but I'm guessing so.

Is there a way to report this?  Is it a VNC or a Compiz issue, and if so, does this go to Launchpad or someplace?

---

### Post by econmit on 2007-10-23
> **evilregis said:**
> What system are you using to VNC into your Ubuntu machine?  Windows?  Another Linux machine?  If it's Windows perhaps try a different VNC client?  RealVNC, TightVNC, UltraVNC are a few...
I am using my Ubuntu 7.10 to VNC to another machine (on my network and running Linux Fedora; although I suspect that is not the most relevant thing here given the dependence of this error on the desktop visual setting I use on the client side). I am using the vncviewer that comes with 7.10. I get the same problem whether I start it from the command invoking "vncviewer" or whether I click through >applications>internet>Remote Desktop [selecting VNC there]

Note: so the crucial thing is that I am able to connect to the host VNC server if I turn the visuals off. [in addition I can connect from other machines running other operating systems; or if I dual boot into windows on the machine I was running Linux 7.10] so the key issue seems to be the interaction between the visuals on 7.10 and the vncviewer.

---

### Post by jwiener3 on 2007-10-23
I am having the same issue and it also works if I disable the visual effects.

---

### Post by econmit on 2007-10-23
> **wyth said:**
> I have the same issue -- and the default VNC viewer is xvncviewer.

I found if I click on another window alongside -- but not covering -- the login prompt, and then click back to the login prompt, I can type in anything.

Yes, that worked for me, decent work around to the problem. Thanks

> **wyth said:**
> Is there a way to report this?  Is it a VNC or a Compiz issue, and if so, does this go to Launchpad or someplace?

Yes, it would be nice to get this bug fixed.

---

### Post by econmit on 2007-10-23
OK some one else. Seems like a real bug then.

BTW, I am using a 1920x1200 resolution and the Nvidia driver enabled.

What do you guys have?

---

### Post by wyth on 2007-10-24
I'm at 1280x1024 on an ATI Radeon R250 using the open source drivers.

---

### Post by wyth on 2007-10-24
[I filed a bug at Launchpad]("https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/156827").

Give some feedback there to make 'em believe.

([https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/156827](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/156827))

---

### Post by econmit on 2007-10-24
Yes, I did. If there are any more of you out there with the same problem please leave a comment as well.

---

### Post by isecore on 2007-10-30
I experience exactly the same things as you guys do.

I'm trying to VNC into a Windows-machine (don't ask why! :) ) but can't input the password for it. I disable Compiz, everything works fine.

The workaround works for me, although it's extremely annoying having to do so. I'm off to launchpad to add my input to the bugreport as soon as I'm finished writing this post.

EDIT: Seems people are aware of this. Hopefully a fix will trickle down to us users.

---

### Post by msrk on 2008-01-07
Yes, I have the same problem with vncviewer as the rest of you.  Only it is January 2008 now and you all posted last October. Has anyone found a way to fix this yet?

Thank you,
Marc

---

