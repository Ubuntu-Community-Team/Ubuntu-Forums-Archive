---
title: "K3b will not run"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-11-08
I just installed K3b after reinstalling Ubuntu and now it will not start.
I have read something about KDE but not sure if this needs to be installed or not.
what do I need to check to get K3b working.
Thanks 
larry

---

### Post by taurus on 2007-11-08
Why created two threads of the same thing--double post?

[http://ubuntuforums.org/showthread.php?t=606834](http://ubuntuforums.org/showthread.php?t=606834)

---

### Post by philinux on 2007-11-08
Any error messages?

---

### Post by larry Gaminde on 2007-11-08
k3b: symbol lookup error: /usr/lib/libqt-mt.so.3: undefined symbol: _ZNinkAuServer9classNameEv

---

### Post by larry Gaminde on 2007-11-08
Sorry
the first one was different, it said k3bn and I tried to corect it and it double posted.

---

### Post by philinux on 2007-11-08
Did you install k3b through add/remove or synaptic.

I installed mine through synaptic and it works fine.

---

### Post by larry Gaminde on 2007-11-08
synaptic
I have had it running for the last few months I upgraded to 7.10 and lots of things messed up mail server, apache2, so I reinstalled everything back to 7.04 and now I can't get K3b working, I have read about deleting ICEathority (done this) and DCOPserver file (can't find this) and also installing KDE which is not installed (I think).

---

### Post by groovomata on 2007-11-09
Hmmm, I too am having problems with k3b. I installed it through synaptic and it won't run. I entered the command 'k3b' into a terminal and this is what I got in response:
> 
erik@silver-surfer:~$ k3b
trying to create local folder /home/erik/.kde/share: Permission denied
trying to create local folder /home/erik/.kde/share: Permission denied
trying to create local folder /home/erik/.kde/share: Permission denied
trying to create local folder /home/erik/.kde/socket-silver-surfer: Permission denied
trying to create local folder /home/erik/.kde/socket-silver-surfer: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/erik/.kde/socket-silver-surfer/kdeinit__0'
ERROR: KUniqueApplication: Can't setup DCOP communication.
erik@silver-surfer:~$ 

Do I need to run k3b as sudo? I've never done that before. If anyone has an ideas of what to do I'd be happy to hear it!
Thanks,
Erik.

---

### Post by groovomata on 2007-11-09
I just tried running: 'sudo k3b' and it seemed to start fine. I didn't actually burn anything as it put up a message saying that it is not recommended to run k3b as sudo. I suppose this must be a permissions thing then.
Erik.
Update: I ran 'sudo k3b' and successfully burned a project which was fine. What would be the best way to solve this problem? K3b itself says it should not be run as sudo. Any suggestions would be helpful.
Thanks,
Erik.

---

