---
title: "Remote Desktop"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by amrclutch1 on 2007-08-08
What could I use to help my grandpa on his ubuntu without him being on my network, he lives somewhere else and I want to have something similar to windows remote assistance. Is there any alternative?

---

### Post by eentonig on 2007-08-08
System\Preferences\Remote Desktop

---

### Post by amrclutch1 on 2007-08-08
Yes I have tried that. but i can hardly imagine that it would be possible to connect to him just using vncviewer roger:0, since there may be more than one roger, would I input his IP address anywhere?

---

### Post by bodhi.zazen on 2007-08-08
1. Try this : [http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

2. Or this : [http://ubuntuforums.org/showthread.php?t=256102](http://ubuntuforums.org/showthread.php?t=256102)

If you vnc, tunnel with ssh :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
	
	See also [denyhosts](http://denyhosts.sourceforge.net/) ~ it is in the repos, but you should read the config file ...

	[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)


3. And, last FreeNx is popular as well ...  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by medley on 2007-08-08
> **amrclutch1 said:**
> Yes I have tried that. but i can hardly imagine that it would be possible to connect to him just using vncviewer roger:0, since there may be more than one roger, would I input his IP address anywhere?

You'll have to specify the IP address of his system. If he's behind a router, you'll have to specify the router's IP then port forward 5800-5900 to his system (assuming you only want to have one connection).

One challenge you'll have is that his IP address will change from time to time. You can get around this by setting up a dynamic to static IP client on his system. Check out dyndns.com or others like it. That way you can just refer to his system as roger.com:0 for example, if that's the domain you set up for him. I've been doing this for years.

This only addresses the access to his system, but it seems you're at least somewhat versed on how to use vnc.

Good luck.

---

### Post by bodhi.zazen on 2007-08-08
you can always add 

roger <ip> to your hosts (/etc/hosts), then you can use roger rather then ip ...

---

### Post by amrclutch1 on 2007-08-08
thanks for the help, i got it working with reverse vnc!

---

