---
title: "how ca I fast recconect to the internet ?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-10
tonight I just disconnected from the internet at night
it was ISP's fault - I'm pretty sure
I'm using ADSL - pppoeconf
but if I discconect when I'm not around or sleeping
can I make ubuntu to fast recconect to the internet ???

---

### Post by ciscosurfer on 2006-08-10
Can you ask your question a different way?  I'm not sure what mean.  Do you mean a script that reconnects you to the Internet when you get dropped?

Ani lo mayveen... :sad:

---

### Post by MaximB on 2006-08-10
> **ciscosurfer said:**
> Can you ask your question a different way?  I'm not sure what mean.  Do you mean a script that reconnects you to the Internet when you get dropped?

Ani lo mayveen... :sad:

no...I don't mean a script
I want it to recconect automaticly when the line drops.
like in winxp you have that option in the properties of the dialer "recconect automaticly" - or somthing like that..

---

### Post by ciscosurfer on 2006-08-10
Have you tried messing with a program called Network Manager?  I always have good results with it.  If my broadband flakes out, the NM tries to reconnect it automatically.  Most of the time if works great (my connection usually never drops, though).  When it does, a simple```
sudo ifdown eth0
sudo ifup etho
```does the trick.

If you're using dial-up, then yes, there is another option:  go to System > Administration > Networking.  Select your Modem connection in the connections window, go to Properties, then Options, and select the checkbox "Retry if the connection breaks or fails to start".  That will do it!

EDIT: I just re-read your original post.  Sorry, I didn't see you are an ADSL user.  There should still be an icon under connections from within your Networking window.  See if has other options to configure.  My apologies, I don't use and/or have DSL and so I'm not sure if this helps :sad:

---

