---
title: "Set beryl-manager to startup"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by kregg on 2007-02-03
I have used this [brilliant guide](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit) and so far I have compiz with Beryl working...

:guitar: 

Only problem is that I can't get Beryl to startup. I go to System, Preferences, Sessions, then the  *Startup Programs* tab. I add beryl-manager to the list and press the close button. Then if I open up Sessions again, it hasn't saved my changes. I don't know why. It's not like beryl-manager is not installed, since I created a launcher on the taskbar for the program and I have to manually start it up (grr!)

How do I overcome this problem? Thanks for any help!

---

### Post by kregg on 2007-02-03
anybody?

---

### Post by taurus on 2007-02-03
Remove the **Default** session in there, System -> Sessions.

---

### Post by phansiizwe on 2007-02-03
Strange, it works for me, but try to type in the complete path to beryl-manager in the Startup Programs dialog, e.g.

```
/usr/bin/beryl-manager
```

To find out the path on your machine, type (in a terminal):

```
which beryl-manager
```

---

### Post by unbuntu on 2007-02-03
kregg:

There's a fine tutorial on the official site of beryl which deals with automated startup of beryl-manager under Gnome, KDE, or XFCE.  Check this out: 
```

http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX

```

Assuming you're using Edgy with AIGLX

EDIT:  Oops, just realized you're using XGL
```

http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL

```

---

### Post by kregg on 2007-02-03
Thanks for all the replies.

I am using Dapper Drake, so I just replaced Edgy with Dapper on the link you gave me Unbuntu and I adjusted as necessary. I just hope it works!

---

### Post by kregg on 2007-02-03
> **phansiizwe said:**
> Strange, it works for me, but try to type in the complete path to beryl-manager in the Startup Programs dialog, e.g.

```
/usr/bin/beryl-manager
```

To find out the path on your machine, type (in a terminal):

```
which beryl-manager
```

```

/usr/bin/beryl-manager

```
The one that **should** run grrrr!

---

### Post by kregg on 2007-02-03
> **taurus said:**
> Remove the **Default** session in there, System -> Sessions.

Done that, still doesn't work...

---

### Post by offstump on 2007-02-08
I'm having the same problem after latest edgy installation. 

I previously added beryl-manager and gdesklets to the startup list without problem, but after an xp related disaster i had to reinstall everything and now i cant get anything to save in the startup list. 

I'm almost certain that i have done everything the same with this install so i can only presume that there is some kind of bug causing this problem. I have also tried all of the above advice with no success.

But if anyone has any suggestions they would be very welcome.

Thanks

---

### Post by PapaWiskas on 2007-02-11
> **phansiizwe said:**
> Strange, it works for me, but try to type in the complete path to beryl-manager in the Startup Programs dialog, e.g.

```
/usr/bin/beryl-manager
```

To find out the path on your machine, type (in a terminal):

```
which beryl-manager
```

I did all of this, first found out where beryl-manager was running from....
then just put in  the /usr/bin/beryl-manager command in my startup....now it automatically starts every time.

thanks phansiizwe

---

