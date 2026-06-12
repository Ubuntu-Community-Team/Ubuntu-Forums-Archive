---
title: "Closing MacBook while running"
date: 2009-07-12
forum: Apple Hardware Users
---

### Post by zacharyrs on 2009-07-12
I have three things left on my 'just to get Ubuntu working' check list, and this is one of them.

When using a Mac OSX on my MacBook, in the middle of running the laptop I was able to close the laptop, and this would put the laptop into 'hibernation/sleep' mode.

However, with U installed, when I close the laptop the computer keeps running - acting as if I never closed the laptop monitor. 

Is there a way to set the laptop up so when I close the laptop it puts it to sleep for me?

---

### Post by hajk on 2009-07-13
Sure there is.

---

### Post by zacharyrs on 2009-07-13
> **hajk said:**
> Sure there is.

Can you please point me in the right direction on where to learn this valuable knowledge you have?

---

### Post by hajk on 2009-07-13
Well, you should first check that your MacBook can be put to sleep with the```

$ sudo /usr/sbin/pm-suspend
```command, and that it can be brought back up when briefly hitting the power button. 

If that works, then you can associate that command with an action of the *acpid* daemon by editing an entry in the 
/etc/acpi/events directory, for example```

$ sudo nano /etc/acpi/events/lid
```and then give it contents```

event=button/lid.*
action=/usr/sbin/pm-suspend
```
The daemon should now put your MacBook to sleep when you close the lid, provided of course that it picks up on closing the lid...

---

