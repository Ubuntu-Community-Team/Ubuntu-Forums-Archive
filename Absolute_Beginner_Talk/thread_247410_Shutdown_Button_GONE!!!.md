---
title: "Shutdown Button GONE!!!"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-08-30
I have no idea what has happened but on my friends machine the shutdown button has dissapered from the logout and such menu. Now he has to log out then shutdown. Is there anyway to fix it?

---

### Post by toasted on 2006-08-30
Did you just install XGL/Compliz?

---

### Post by PPAAUULL on 2006-08-30
Nope never installed any of that on it.

---

### Post by Jeroen2006 on 2006-08-30
hi,

rightclick in the taskbar:

click add to panel and hey presto the quit knob is present mark it and click add.... then you can quit buntu again

---

### Post by toasted on 2006-08-30
> **PPAAUULL said:**
> I have no idea what has happened but on my friends machine the shutdown button has dissapered from the logout and such menu. Now he has to log out then shutdown. Is there anyway to fix it?

Do you mean the menu that is at top left under the system heading? The button at the bottom of that menu?

---

### Post by Jeroen2006 on 2006-08-30
no the taskbar with applications,places,system in it

---

### Post by PPAAUULL on 2006-08-30
> **toasted said:**
> Do you mean the menu that is at top left under the system heading? The button at the bottom of that menu?

Ya I mean the on the menu when you click the button on the task bar at the top on the right.

---

### Post by 2DC on 2006-10-14
Got the same problem here.. only I have compiz/aiglx enabled. I guess it has something to do with my sessions but when I looked at it the ask on logout was checked as normal.. can anyone help??

---

### Post by faithsnathan on 2006-10-21
Yeah, I have the same problem.  There is a "Quit" button, but it only logs me out.  I then can shut down (though not restart) from the options menu there.  I wonder why we can't shutdown/restart/whatever from within the screen name.  Oh, well.

---

### Post by DaveBorealis on 2006-10-21
> **faithsnathan said:**
> I wonder why we can't shutdown/restart/whatever from within the screen name.

In a way, you can.  Open a terminal and type"
```
sudo /sbin/shutdown -h now
```

Or if you'd like to reboot:
```
sudo /sbin/shutdown -r now
```

'man sudo' gives a nice overview of the command.

Best regards,
Dave

---

### Post by faithsnathan on 2006-11-03
> **faithsnathan said:**
> Yeah, I have the same problem.  There is a "Quit" button, but it only logs me out.  I then can shut down (though not restart) from the options menu there.  I wonder why we can't shutdown/restart/whatever from within the screen name.  Oh, well.

Update:  Well, I figured out what I did.  :)  If you go to System --> Sessions --> and make sure "Ask on Logout" is checked.  It's not where I would have thought to look, but whatever.  I sure hope this helps someone else.

---

### Post by Nigori Zake on 2007-02-20
I just had a similar problem after changing my Login Window Screen.  I only had the options to 'Suspend' or to 'Hibernate.' The buttons for 'Suspend' and 'Shut down' had disappeared from my quit menu. After playing around with settings I fixed it by:

Go to the panel: System>Administration>Login Window
Then check "Show Actions menu" under the "Menu Bar" setting.

---

### Post by SaltyCrak on 2007-11-28
> **Nigori Zake said:**
> I just had a similar problem after changing my Login Window Screen.  I only had the options to 'Suspend' or to 'Hibernate.' The buttons for 'Suspend' and 'Shut down' had disappeared from my quit menu. After playing around with settings I fixed it by:

Go to the panel: System>Administration>Login Window
Then check "Show Actions menu" under the "Menu Bar" setting.

LEGEND!

---

