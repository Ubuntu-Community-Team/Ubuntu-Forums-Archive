---
title: "Can't access shared files on Windows box"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-02-01
Hey there,

I'm on a wireless network in my house, and used to, from Windows, be able to access the shared files on my mum's PC downstairs...Heck, I could even do it from the liveCD, but now, I can't?

When I click on "Places >> Network servers", it comes up with "Windows network", and when I click on that, I see nothing. 

I tried with and without static IP, but this made no difference...
I installed Samba aswell, this made no difference either...

So how can I view the shared files?

Thankyou in advance

---

### Post by davmac on 2006-02-01
Jimmey,

I think samba is the answer to your problem. After installing it did you make changes to the configuration? If not this could be the issue.

Have a look at [http://www.ubuntuforums.org/showthread.php?t=76647](http://www.ubuntuforums.org/showthread.php?t=76647) for info about setting up Samba to access shared files on a Windows machine.

Hope this helps,

Dave Mac

---

### Post by Jimmey on 2006-02-01
Ahh, I never knew it needed to be configured 
:oops: 

Thankyou

---

### Post by Jason_25 on 2006-02-01
Browsing with windows machines can be troublesome.  But you shouldn't need samba just to connect to windows shares.  Nautilus can do this.  Go to places > connect to server.  Then choose windows share and then in the server field type 
//name of windows computer

---

### Post by davmac on 2006-02-08
A thought just occurred to me. Do you have any sort of personal firewall (like zonealarm or kerio) running on the windows box?

If so, it might be worth disconnecting yourself from the outside world, shut down the firewall and then seeing if you can access the windows box.

If this works you'll just have to "poke the right holes" in the firewall to get this up and running once you're connected to the outside world again.

Hope this helps,

Dave Mac

---

### Post by bartbes on 2006-02-08
or you can just check if there is (in the log or something) an incoming and blocked signal, this is much easier than unplugging the network and disabling the firewall

---

