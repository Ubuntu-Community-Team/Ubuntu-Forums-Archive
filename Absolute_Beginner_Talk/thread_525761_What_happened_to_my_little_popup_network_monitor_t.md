---
title: "What happened to my little popup network monitor thing?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by animeanonymous on 2007-08-14
Well, I just started using ubuntu and I decided to  reconfigure my desktop panels.  Well when you first install it, it has that neat little popup network manager that lets you choose between a wired connection and a wireless connection.  I deleted the panel that had that, and created a completely new one.  I added the Main menu, window list, clock, and power button among a few other things. 

 But the Network Monitor is different.  It doesn't have a neat popup but just a window and for some reason, it can't detect my wireless network like the other thing can.  I know there are two different programs that you can add to the panel.  How do I get the one with the neat popup thing back.

Thanks in advance

---

### Post by Blutack on 2007-08-14
It is a little program called nm-applet, which lives in the "Notification Area" (where you get popups about system updates and stuff.  It sounds like you didn't put one on your new panel so you need to add one.  You can either logout and login again or if you are impatient
press alt and F2
and type in
nm-applet --sm-disable

---

### Post by Arthur Archnix on 2007-08-14
Go to >System  >Preferences  >Sessions

Click "New"

In name put "Network Manager"

In Command put "nm-applet --sm-disable"

No quotes of course.

Ok, make sure a checkbox is in it. Logout. Log back in.

Edit: Yes, if you've just removed it from the panel, blutack is right, logout and then back in. Only if it's not there after you logout and back in should you follow my steps.

---

### Post by animeanonymous on 2007-08-14
Oh I see. So it just lives in the notification area and will always be there when I log in.  Correct?

---

### Post by Arthur Archnix on 2007-08-14
Provided you have a notification area on your panel, and you haven't removed it from your session startup, yes.

---

