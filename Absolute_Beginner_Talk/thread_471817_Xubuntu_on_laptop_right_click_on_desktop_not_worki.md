---
title: "Xubuntu on laptop right click on desktop not working"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ubuntumaybe on 2007-06-12
Hi,

I successfully installed Xubuntu but when I right click or left click on the desktop there is no menu. What now?

---

### Post by ugm6hr on 2007-06-12
If you want that function:

Applications->Settings->Desktop Settings
Behaviour Tab
Show desktop menu on right click (tick)

---

### Post by john.nicholls on 2007-06-12
This may indicate that the desktop manager is not running. Open a terminal and type ```
xfdesktop
```

---

### Post by ubuntumaybe on 2007-06-14
> **john.nicholls said:**
> This may indicate that the desktop manager is not running. Open a terminal and type ```
xfdesktop
```

Hi,
 

 Xfdesktop had not been installed. Is that normal? Now I can get the right click if I start xfdesktop in a terminal. How do I load this app when I log in? Thanks.

---

### Post by john.nicholls on 2007-06-14
> **ubuntumaybe said:**
> Hi,
 

 Xfdesktop had not been installed. Is that normal? Now I can get the right click if I start xfdesktop in a terminal. How do I load this app when I log in? Thanks.

It should normally be installed.
Go to Sessions & Startup and make sure Automatically save session on logout is ticked. Then when you log out with xfdesktop running, the session will be saved and the next time you log in it should start. If it doesn't, go to Settings | Autostarted Applications and add xfdesktop to the list.

---

### Post by colo505 on 2007-06-15
I have the same problem (no right-click menu on desktop) in Ubuntu 7.04. Can you please help?

---

### Post by john.nicholls on 2007-06-15
Check that Desktop Preferences | Behavior | Show desktop menu on right click is ticked, and that xfdesktop is running (see above)

---

### Post by rumour on 2007-06-17
Guys i am also having a similar prob.
I have UbuntuStudio with GL Desktop running just fine but the right click is not working nor i can see any desktop icon and the desktop background is black...
can any one tell me the reasons for this....
oh ya and i did install xfdesktop after that when i run the command xfdesktop in the terminal then i can see the icons but there is a error msg 
"Unable to contact the Xfce Trash service.

Make sure you have a file manager installed that supports the Xfce Trash service, such as Thunar"
and after i close the terminal the desktop goes black again.....
what should i do?

---

### Post by rumour on 2007-06-17
> **rumour said:**
> Guys i am also having a similar prob.
I have UbuntuStudio with GL Desktop running just fine but the right click is not working nor i can see any desktop icon and the desktop background is black...
can any one tell me the reasons for this....
oh ya and i did install xfdesktop after that when i run the command xfdesktop in the terminal then i can see the icons but there is a error msg 
"Unable to contact the Xfce Trash service.

Make sure you have a file manager installed that supports the Xfce Trash service, such as Thunar"
and after i close the terminal the desktop goes black again.....
what should i do?

the problem was solved after installing Thunar but i was wondering is there other way out by not installing Thunar.

---

