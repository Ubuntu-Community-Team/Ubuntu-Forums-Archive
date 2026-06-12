---
title: "How Do I Get Rid of this FISH?!"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-12-12
I pressed alt+f2 to run a program
typed in:
free the fish

and now i can't get rid of it!
How can i make this guy go away without restarting?
also, is there a function similar to ctrl+alt_delete? to see what processes are running and shut them down if i wish?

thanks.

---

### Post by Rocket2DMn on 2007-12-12
Clicking on it works for me.

---

### Post by jordank on 2007-12-12
yeah, but she just swims away and comes back seconds later

---

### Post by JillSwift on 2007-12-12
Oh my! What an adorable little easter-egg.

Plus it entertains my cats =^_^=

---

### Post by rsambuca on 2007-12-12
It should just quit when you click on it.  The fish is just an accessory you can add to your gnome panel.  Right click the panel and select "Add to Panel".  It is under accessories.

---

### Post by jordank on 2007-12-12
no, the one you add to panel is a fortune teller. this one swims around my screen. it gets very annoying!

---

### Post by MRiGnS on 2007-12-12
You have to do:

```
killall gnome-panel
```

---

### Post by short3000y on 2007-12-12
i gots same prob, it wont stay gone...

---

### Post by rsambuca on 2007-12-12
I stand corrected.  It doesn't leave for good!

---

### Post by jordank on 2007-12-12
thank you sir. killall worked.

---

### Post by FuturePilot on 2007-12-12
I see you've met Wanda :lolflag:

---

### Post by zabien1970 on 2007-12-12
For running processes you could go to
System > Administration > System Monitor
 Then under  Processes click on the file and hit End Task, Ithink this was what you were looking for

---

### Post by erginemr on 2007-12-12
> **zabien1970 said:**
> For running processes you could go to
System > Administration > System Monitor
 Then under  Processes click on the file and hit End Task, Ithink this was what you were looking for

Correct, but "Wanda the Fish" has been tightly integrated into Gnome processes (namely, gnome-panel), so you do not have a separate pid (process id) for it and therefore cannot terminate it except using:
```
killall gnome-panel
```
as suggested before or by logging out and back in.

Actually, this is one of the two Gnome easter eggs, the other one being a cute space invaders clone game that can be activated by pressing Alt+F2, and then, by typing "gegls from outer space" without the quotes.

---

### Post by zabien1970 on 2007-12-12
[QUOTE=erginemr;3937485]Correct, but "Wanda the Fish" has been tightly integrated into Gnome processes (namely, gnome-panel), so you do not have a separate pid (process id) for it and therefore cannot terminate it except using:
```
killall gnome-panel
```


 I did not know that, lol, one more thing I learned today,  I was mostly replying to his opening post though where he asked about something similar to the Ctrl/Shift/Delete function in windows.

---

