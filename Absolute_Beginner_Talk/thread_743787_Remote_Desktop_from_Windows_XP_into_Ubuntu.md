---
title: "Remote Desktop from Windows XP into Ubuntu?"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2008-04-03
Hi,

I would like to be able to use remote desktop (or something similar) to get to my Ubuntu machine from Windows XP.  

How would I setup the Windows machine & the Ubuntu Server to be able to connect to it?  

Does it cost the Ubuntu machine much "overhead" in terms of resource usage?

Thanks,
Rich

---

### Post by Xiong Chiamiov on 2008-04-03
Do you need a screen control program, or just shell access?  The latter will of course take much less in the way of resources, but is limiting to what you can do, especially if you're not familiar with the terminal.

---

### Post by smartboyathome on 2008-04-03
I would say use NoMachine's NX server and client. Just install it and you are ready to go.

---

### Post by ghost_ryder35 on 2008-04-03
Vnc

---

### Post by RichTJ99 on 2008-04-03
I would like the whole graphical interface.  

I dont mind if it is resource intensive, when I am connected remotely & doing things.  I just dont want it to take resources when I am not using the software (99% of the time).  

Is NoMachines NX server more or less of a resource hog when not running than VNC?

How do I install either of them?

---

### Post by Xiong Chiamiov on 2008-04-03
As far as which client to use, I can't help you.

As far as how to install them, [this]("http://monkeyblog.org/ubuntu/installing/") is quite an excellent (and extensive) guide.

---

### Post by RichTJ99 on 2008-04-03
Hrmm, Nomachine looks like it costs 800+ dollars.

---

### Post by IsawSp4rks on 2008-04-03
If you're going to use VNC, look at TightVNC - it's VNC with compression and optimisations for speed.

[http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by ghost_ryder35 on 2008-04-03
yep, VNC is already installed on Ubuntu, just go to System, Preferences, Remote Desktop.  Make sure to enter a password to ask someone who is logging on, and make sure "Ask for your confirmation" is unchecked.  On 8.04 you can use encryption, on 7.10 the encryption option is not there.  On Windows just go to [www.tightvnc.com](www.tightvnc.com) and download and install.

---

### Post by RichTJ99 on 2008-04-03
Does the remote desktop option in 7.10 use a lot of resources when its not running?

---

### Post by ghost_ryder35 on 2008-04-03
> **RichTJ99 said:**
> Does the remote desktop option in 7.10 use a lot of resources when its not running?
practically none, its probally running right now and you dont know it :)

---

### Post by vol_freak on 2008-04-03
> **RichTJ99 said:**
> Hrmm, Nomachine looks like it costs 800+ dollars.

No, there is a free version and I prefer it over VNC. 

[http://www.nomachine.com/download-package.php?Prod_Id=5](http://www.nomachine.com/download-package.php?Prod_Id=5)

---

### Post by RichTJ99 on 2008-04-03
Is there a guide to setting this up or is it just very easy to do?

---

### Post by thisiam on 2008-04-03
its really simple, in Ubuntu go to system->preferences->remote desktop and enable sharing and check out the other options there. Now go to windows and install tightvnc and run vnc viewer and connect to your ubuntu box.

---

### Post by RichTJ99 on 2008-04-03
One last question.  Is this secure to leave open on the internet (the server)?

---

### Post by thisiam on 2008-04-03
I wouldn't,it would give people something to try to connect too.
even having password and user prompt enabled i wouldn't be able to sleep without turning it off.

---

### Post by RichTJ99 on 2008-04-03
Hrmm, then how should I be using it if I shouldnt leave it on?

---

### Post by Tristam Green on 2008-04-03
I use VNC when I need to do anything from one machine to the other.  While running, I notice a large slowdown, especially when browsing Windows XP from Ubuntu.

Best of luck for you :)

---

### Post by RichTJ99 on 2008-04-04
> **thisiam said:**
> I wouldn't,it would give people something to try to connect too.
even having password and user prompt enabled i wouldn't be able to sleep without turning it off.

Im confused, if you cant leave VNC running (due to security), how should you use it (practically speaking)?

I would want to leave it on so I have access whenever I need it.

---

