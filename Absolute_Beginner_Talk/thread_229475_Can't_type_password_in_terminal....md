---
title: "Can't type password in terminal..."
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by DrBobert on 2006-08-04
This is probably gonna a be a very n00bish question, but it's coming from a n00b.

I'm trying to chnage file permissions so I can install the latest version of Firefox. When I enter
```
sudo chmod w etc
```

it asks me for the password. However, despite my most frantic efforts, no characters appear to indicate I have typed anything, and as such, I can't enter the pass.

If I'm being stupid and missed out something I should no, I apologise, but please, what's going on?

---

### Post by r4ik on 2006-08-04
The passwrd doesnt show any *** just type it and hit enter.

---

### Post by DrBobert on 2006-08-04
So, I just type my password and hit enter?

---

### Post by ciscosurfer on 2006-08-04
No characters will appear when you enter your password.  Use the password that you setup initially when you installed Ubuntu.  

When you say the "latest" version are you refererring to Firefox 2.0?  Otherwise, you can simply install firefox via Synaptic.

---

### Post by Tomosaur on 2006-08-04
Yes, you just type your password and press enter. You will not be able to see your password as you enter it.

---

### Post by _simon_ on 2006-08-04
> **DrBobert said:**
> So, I just type my password and hit enter?

yes :)

---

### Post by DrBobert on 2006-08-04
Cheers for that, it's working.

I was using Firefox 2 when I had Windows, but if I can use this Synaptic thingy to get the latest version, I will... If I knew what it was and how to use it...

---

### Post by ciscosurfer on 2006-08-04
Synaptic is the gnome package manager and is a graphical front-end for apt.  You will have to adjust your repos to grab the absolute latest Firefox from it (I don't think anyone is serving out FF 2.0 as an apt repo but you can check and see).

Or, if you are having trouble, you can try [this page]("http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/") or [this page]("http://forums.mozillazine.org/viewtopic.php?t=437885&sid=b2b64103d7c17ba5a15069bbadce95ac").  Be careful on them though and make sure everything looks legit (i.e., ask here in the forums if you don't know)

---

