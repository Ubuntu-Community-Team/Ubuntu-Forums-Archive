---
title: "Unable to login"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by noorez on 2008-01-22
I am unable to login to my gutsy installation. It just suddenly happened today...it was fine yesterday.

What happens is this:

1. I get the proper login screen
2. I put in my username/password and press enter
3. It then looks as if it were going to login fine  but then it suddenly goes back to the login screen....as it i had been logged out...

any ideas as to what is wrong ?

---

### Post by fatality_uk on 2008-01-22
Seems like a vid driver error. If you git as far as the login, the gnraly kernel bits have loaded. Can you see if you can bring you a CLI login by hitting crtl+alt+F1? If you can login there, then to

---

### Post by sports fan Matt on 2008-01-22
I had this same situation 24 hours ago..However I was impatient and reinstalled, but hopefully this solution works for u

---

### Post by dannyboy79 on 2008-01-22
this actually has happened to me before. it was due to my hard drive being out of space. get to one of the getty's by hitting ctrl-alt-f1 and then if you enter your username there, and then your password. issue

df -h

that will show you disk usage.  

if it were an X issue, it would tell you it was an X issue. good luck

---

### Post by noorez on 2008-01-22
I don't think this could be an issue with diskspace ?. I still have quite a bit left. I've also had my hard disk quite full for while some time ago and it worked just fine. If it is a problem with my nividia driver, should I just try and reinstall it ?

---

### Post by noorez on 2008-01-22
I attempted to reinstall my graphics driver....i managed to login but now the gui is all messed...
This error message came up:

There was an error starting the GNOME Settings Daemo.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a prely. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by noorez on 2008-01-23
It appears it was a video driver problem. I have removed the nvidia driver and went back to the generic one and was able to login fine except now I can't use any of the compiz stuff I was using before.
What was the proper driver again for a GeForce Go 7600 ?

---

