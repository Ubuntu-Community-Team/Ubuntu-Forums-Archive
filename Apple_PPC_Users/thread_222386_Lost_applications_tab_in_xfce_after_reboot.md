---
title: "Lost applications tab in xfce after reboot?"
date: 2006-07-24
forum: Apple PPC Users
---

### Post by sbmd on 2006-07-24
Hello i did an install of the server edition on an old G3. I then install the xfce desktop and was working great, but now after an update and reboot it does not have the Applications tab, how can I get this back? Thankx alot for any and all help in advance. ](*,)

---

### Post by eXisor on 2006-07-26
This happened to me too - a complete linux n00b.

Why it happened... 
As best I can figure it happened because I selected save session for future login as a default (via sessions and startup config - I don't do this anymore) and then got a system freeze so I had to do a hard reboot. When I got back in the menu was gone. (On another occasion I lost everything this way, even the top and bottom panels). Since it happened on a normal reboot for you, I think something failed/broke during the logout process.

To fix...
When you get to the login screen, select the sessions icon and choose the default. Make this the new default, and then login. The menu should be back. 
I'd advise switching of the save sessions option and doing it consciously when you need it, ie. as you restart/shutdown/log out.
Alternatively, you can re-add the menu by right-clicking on the top panel, selecting add item and then choosing the xcfe menu (it seems to be the same thing, although I don't know if it'll get automatically updated when you install a new menu enabled package). Anyone know?
Then move it back to the left by right-clicking on the newly added xfce menu and selecting move. Drag it across to the left. Remember to save this session for future and use/make default this session for the next login.

I hope this helps.

---

### Post by sbmd on 2006-07-26
Yes awesome, I have tried replacing menu.lst and a few others things I have read hear but yours worked for now, so I guess i will continue tring this. Thankx alot.

---

### Post by eXisor on 2006-07-26
I'm glad you got it going again. Which method did you use?

There's a new beta of xfce out which seems - in the changelog - to acknowledge that this is a problem and reckons to fix it.

There's a thread about this [http://www.ubuntuforums.org/showthread.php?t=213348&highlight=xfce+beta](http://www.ubuntuforums.org/showthread.php?t=213348&highlight=xfce+beta)
if you're interested.

---

### Post by sbmd on 2006-07-26
Nice I may have to check that out. Thankx again

---

