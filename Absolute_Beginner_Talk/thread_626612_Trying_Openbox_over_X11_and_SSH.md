---
title: "Trying Openbox over X11 and SSH"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by bensands on 2007-11-29
Hi
Have installed Dapper drake (6.06) server. Installed The X-windows components and xterm.

I can use my Apple mac to access the system via ssh (ssh -X i.p.add.ress -l user -p 23 (ssh is on 23. my doing!.))
I am using X11 on the mac.
then I check that x is working through ssh.
>echo $DISPLAY 
<localhost:10.0 - (which I assume is the ssh tunnel to my mac)
and then type
> xterm& 
Hey Presto! a new terminal pops up on my Mac.

Now installed openbox. I assumed that as the Display variable is set to point to my mac I should be able to type
> exec openbox
and would then get the openbox window manager through X on my mac, but I get the following error.

>(openbox:15205): Openbox-WARNING **: A window manager is already running on screen 0

>Connection to i.p.add.ress closed.

I checked on the VDU attached to my ubuntu box and there is only a login prompt.

Should I be able to do this? Or have I understood it wrong? If xterm works then why not a Window Manager?
Or does it mean that openbox has automatically started for screen 0 (wherever that is!?), in which case, how can I stop this and start manually.

Any assistance greatly appreciated.

---

### Post by bensands on 2007-12-06
Hello

Can anyone point me in the right direction with this??

---

### Post by ByteJuggler on 2007-12-06
If you set your display to point to your mac, then you'll be using the X-Server **and** window manager on your mac, hence (I think) why you're getting the "there's already a window manager running" message.  I think.

---

