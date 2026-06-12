---
title: "Dissapearing Panels, trash is full"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-10
I accidently borked something..All I know is my trash can is full..I can see everything I think but I cant figure out how to restore everything back to where it was..Am i screwed?  lol  I just want my panels back and my trash can empty

---

### Post by ShodanjoDM on 2008-03-10
I'm not sure if this will work without panels, but maybe you can try pressing Alt+F2 for  "Run Application" window to appear.

If it works, then type: gnome-panel

And enter.

---

### Post by sports fan Matt on 2008-03-10
The command "gnome-panel" failed to run:

Failed to execute child process "gnome-panel" (No such file or directory)

What else can i try?

---

### Post by sports fan Matt on 2008-03-10
I can readd things but not move them around, and I'm trying to figure out why my trash is full..Is there an easy fix to move all the standard icons like Trash, xfce menu, clock, quit, etc..Im so frustrated since i cant figure this out..lol  

I think all my configurations are in the trash, its a matter of getting them out of there...

---

### Post by ShodanjoDM on 2008-03-10
Didn't know you're using XFCE. Anyway, the command in the Run dialog should be:

xfce4-panel

---

### Post by Oldsoldier2003 on 2008-03-10
> **sox fan Matt said:**
> I can readd things but not move them around, and I'm trying to figure out why my trash is full..Is there an easy fix to move all the standard icons like Trash, xfce menu, clock, quit, etc..Im so frustrated since i cant figure this out..lol  

I think all my configurations are in the trash, its a matter of getting them out of there...

the folders that start with a . are configuration folders and probably (99.9% of the time) go back into your home folder

---

### Post by ShodanjoDM on 2008-03-10
about looking into trash, you can view the contents via terminal. The "formula" is the same (using ALt+F2 to bring the Run dialog) then type:

xfce4-terminal

or if that fails, try xterm

Once the terminal appears, you can check the contents of the trash by entering:

```
ls -hal ~/.Trash
```

---

### Post by sports fan Matt on 2008-03-10
ok, thatsc a bit better i guess, im just freaked cause when things are moved aroumd, its not right and trying to get them back is a long, painful journey,  Would reinstalling the xfce desktop be any good or no?

How can i get things moved to the proper folders and such out of the trash?

To recap:  I want to be able to put the "standard items" on a typical gutsy install in the panel up top, menu, quit, time, network connection..things like that...then have a bottom panel for my webpages that im viewing

And to get everthing out of the trash and back in their respective folders..Is it as hard as it seems?

---

### Post by sports fan Matt on 2008-03-10
that command gives me this: total 8.0K
drwx------  2 office office 4.0K 2008-03-09 16:34 .
drwxr-xr-x 35 office office 4.0K 2008-03-10 11:23 ..

---

### Post by ShodanjoDM on 2008-03-10
> **sox fan Matt said:**
> that command gives me this: total 8.0K
drwx------  2 office office 4.0K 2008-03-09 16:34 .
drwxr-xr-x 35 office office 4.0K 2008-03-10 11:23 ..

Your trash can is empty :)

So, no, I don't think you have deleted any config files, the icons might show it's full for some buggy reasons... I know in gnome it still could happens.

---

### Post by ShodanjoDM on 2008-03-10
> **sox fan Matt said:**
> Would reinstalling the xfce desktop be any good or no?

It's been a while since I used xfce, but is there any .xfce folder in your home directory?

You can try to rename the folder, then log out and log back in first before reinstalling the whole xfce packages.

---

### Post by sports fan Matt on 2008-03-10
If its empty, then where did all my panels I had this morning go..this is quite a mystery!

---

### Post by sports fan Matt on 2008-03-10
I just reinstalled Gnome..seems easier..Thanksw to all who helped!

---

