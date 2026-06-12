---
title: "Please help out with a silly error. Mousemovement options aren't saved."
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by BjornHaland on 2006-05-18
At login screen, mouse movement is normal.

As soon as I enter desktop, the mouse all of a sudden moves very slowly.

Of course, all I have to do is enter mouse settings in the system menu. And so I do, and I'm happy to observe there is a slider there for the mouse movement. All I have to do is slide the bar a little to the right, and no problem. This is where it stops. This setting isn't saved. I've tried several times, but it just isn't saved. 

Is there any way around this? Thanks in advance.

---

### Post by Mustard on 2006-05-18
You might want to bring this up in the Dapper Drake sub forum, as it could well be a bug relating to Dapper.

---

### Post by BjornHaland on 2006-05-18
Will do.

---

### Post by mlind on 2006-05-18
open gconf-editor from terminal

navigate to /apps/desktop/gnome/peripherals/mouse/


do you see these values being changed (in real-time) when you modify mouse
settings from Preferences menu?

if not, you may need to delete ~/.gconf/desktop/gnome/peripherals/mouse
folder and relogin.

---

### Post by BjornHaland on 2006-05-18
I didn't see anything change in real-time, so I did:

rm -r ~/.gconf/desktop/gnome/peripherals/mouse

That seemed to work the first time, so I pushed ctrl+alt+backspace. However, I still couldn't make it work via the GUI.

Hm, I just manually set motion_acceleration to 1.2, that worked.

Guess that's solved then. If the problem persists and the problem loops, I'll just have to do that manually until this bug is fixed.. if it is indeed a bug. Thanks for all your trouble helping me out.

---

### Post by mlind on 2006-05-18
strange, looks like gconf keys are being read from wrong place.. 

If you create a new useraccount, and login on that account - does the mouse
preferences of new user get saved?

---

