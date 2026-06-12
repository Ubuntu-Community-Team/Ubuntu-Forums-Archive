---
title: "Dapper problems.."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by NeonBlue on 2006-06-11
Upgraded to Dapper from Breezy using apt- get and it took forever to install, fine.  Then, I boot it up and I come to the login screen.  It accepts my user name and password, progresses, then reverts to the same login screen.  No matter what.

---

### Post by user1397 on 2006-06-11
when you say it "progresses" do you mean it goes to a screen similar to this:

---

### Post by NeonBlue on 2006-06-11
Doesn't make it there.  It goes to the black screen with the flashing underscore then reverts.

---

### Post by aysiu on 2006-06-11
I don't know if I can help, but I can at least help you diagnose where the problem lies.

Can you press Control-Alt-F1 and see if you can log in non-graphically?

That way we can know whether it's a user login issue or a GDM login issue.

---

### Post by NeonBlue on 2006-06-12
Yes, I can login non-graphically.

---

### Post by aysiu on 2006-06-12
Something's wrong with GDM, then. I'm not sure how to fix it, though.

Can you try this? It's only a temporary fix, but maybe it'll at least allow you to log in... ```
sudo aptitude update
sudo aptitude install kdm
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm start
```

---

### Post by user1397 on 2006-06-12
aysiu, can you turn on your PM's because i need to ask you personal questions, especially about aptitude (like things that we've discussed before, and i can easily discuss them again on a one on one basis)

---

### Post by NeonBlue on 2006-06-12
Yeah, I performed those commands then went to login and it gave me the error:
Cannot open theme file /usr/share/apps/kdm/themes/kubuntu

---

### Post by aysiu on 2006-06-12
[QUOTE=NeonBlue]Yeah, I performed those commands then went to login and it gave me the error:
Cannot open theme file /usr/share/apps/kdm/themes/kubuntu[/QUOTE] Hm. Maybe ```
sudo aptitude install kubuntu-default-settings
```

[QUOTE=erik1397]aysiu, can you turn on your PM's because i need to ask you personal questions, especially about aptitude (like things that we've discussed before, and i can easily discuss them again on a one on one basis)[/QUOTE] PM is on.

---

### Post by NeonBlue on 2006-06-12
Exact same problem is happening.

---

### Post by aysiu on 2006-06-12
So... can't log in through GDM or KDM.

It must go beyond the display manager. But you can still log in via the terminal.

Hm. I have no idea. Hopefully someone smarter than I am will jump in on this.

---

### Post by NeonBlue on 2006-06-12
Thanks for trying to help.  I can't access even the old version now, so I'm stuck on Windows 98.  Lame :(

---

### Post by aysiu on 2006-06-12
Something else you can try... I know you're probably tired of this, but...

Control-Alt-F1, log in.
```
sudo adduser neonblue
``` Control-Alt-F7 and try to log in with the new user...?

---

### Post by NeonBlue on 2006-06-12
Yeah, didn't work.

---

### Post by elemental666 on 2006-06-12
try reinstalling gdm itself:
```
 sudo aptitude remove gdm
sudo aptitude update
sudo aptitude install gdm
```

or in synaptic, search for gdm and mark it for complete reinstallation...

see if synaptic lists any broken packages by clicking on custom in the bottom left then selecting broken from the list

---

### Post by NeonBlue on 2006-06-12
Did not work.  Got two errors.

I/o warning : failed to load external entity "/vary/lib/scrollkeeper/(null)/scrollkeeper_cl.xml"

invoke-rc.d: initscript gdm, action "reload" failed.

---

### Post by asimons999 on 2006-10-06
did you get this problem resoloved? it sounds similar to a problem im having.. except im using edgy.. and i dont to do anything too rash.. because beryl and dual monitors is setup..

---

