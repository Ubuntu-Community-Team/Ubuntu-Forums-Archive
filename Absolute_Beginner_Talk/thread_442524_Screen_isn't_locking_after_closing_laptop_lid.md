---
title: "Screen isn't locking after closing laptop lid"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Dritzen on 2007-05-13
It was working fine before I updated the HAL device manager when Feisty prompted me to.

What was happening before:
Close laptop lid
Screen gets locked
I have to type a password to get back in to Gnome

What happens now:
Close laptop lid
I think the screen is turning off but it's not locking
Anyone can use my PC unless I specifically lock it.

/var/log/acpid  shows this info:

```

[Sun May 13 17:14:59 2007] completed event "button/lid LID 00000080 00000055"
[Sun May 13 17:15:03 2007] received event "button/lid LID 00000080 00000056"
[Sun May 13 17:15:03 2007] notifying client 5267[0:0]
[Sun May 13 17:15:03 2007] notifying client 325[106:110]
[Sun May 13 17:15:03 2007] executing action "/etc/acpi/lid.sh"
[Sun May 13 17:15:03 2007] BEGIN HANDLER MESSAGES
[Sun May 13 17:15:03 2007] END HANDLER MESSAGES
[Sun May 13 17:15:03 2007] action exited with status 0
[Sun May 13 17:15:03 2007] completed event "button/lid LID 00000080 00000056"

```

cat /proc/sys/vm/laptop_mode  shows 0

Just to make sure, I made sure that ACPI is running by doing:

```

sudo /etc/init.d/acpid stop
sudo /etc/init.d/acpid start

```

I'm using a Dell Inspiron 9300 laptop and this was working fine a few days ago.

Any suggestions?

---

### Post by Jonne on 2007-05-13
I don't have any suggestions, but where do I turn off that behaviour? it's kinda annoying to me (it's not like it offers any real security, everyone can just read my whole HD with any liveCD).

---

### Post by FuturePast on 2007-05-13
> **Jonne said:**
> I don't have any suggestions, but where do I turn off that behaviour? it's kinda annoying to me (it's not like it offers any real security, everyone can just read my whole HD with any liveCD).
Try $ gconf-editor and look in key /apps/gnome-power-manager/...

---

### Post by Dritzen on 2007-05-15
Any other ideas guys?

---

### Post by deol on 2007-05-22
I have noticed that if I right mouse click the battery in the top bar, I get a preferences option.  From there it ask what I would like the laptop to do when I close the lid.  I set it to "do nothing" to keep from having to log in.  However, if you have it set to "blank screen", it asks me to log in when I re-open the lid.  Try making sure it's set to "blank screen" and see if that works.

---

### Post by Bluecircle on 2007-06-23
Bump

I have it set to "blank screen", but it doesn't. Of course I am on Gutsy so who knows.

---

### Post by Inxsible on 2007-06-23
Press Alt + F2. Type in gconf-editor, then press enter. Navigate to apps --> gnome-power-manager.

The flags to look for would be :
```
lock_on_blank_screen
``` Check mark it, if you want to lock the screen and uncheck it if you don't

Additionally you can choose to change the values of ```
lock_on_hibernate
lock_on_suspend
```Hope that helps !!

---

### Post by Bluecircle on 2007-06-23
> **Inxsible said:**
> Press Alt + F2. Type in gconf-editor, then press enter. Navigate to apps --> gnome-power-manager.

The flags to look for would be :
```
lock_on_blank_screen
``` Check mark it, if you want to lock the screen and uncheck it if you don't

Additionally you can choose to change the values of ```
lock_on_hibernate
lock_on_suspend
```Hope that helps !!

That key didn't even exist for me, I added it, but nothing. The screen does go black like it tries to lock, but then it just comes back when I move the mouse. It did work in feisty so we'll see.

EDIT: Awesome I fixed it! All I had to do was check the two checkboxes in Screensaver Settings. :)

---

### Post by elleP on 2007-10-24
> Press Alt + F2. Type in gconf-editor, then press enter. Navigate to apps --> gnome-power-manager.

The flags to look for would be :
Code:
lock_on_blank_screen
Check mark it, if you want to lock the screen and uncheck it if you don't

Additionally you can choose to change the values of 
Code:
lock_on_hibernate
lock_on_suspend
Hope that helps !!

In gutsy it's navigate to apps --> gnome-power-manager->lock.
and the lock_on_ prepends are no longer there.

---

### Post by Kingsley on 2007-12-02
> **elleP said:**
> In gutsy it's navigate to apps --> gnome-power-manager->lock.
and the lock_on_ prepends are no longer there.
Go to "apps > gnome-power-manager > lock" and then check the "blank_screen" box.

---

### Post by atlanta800 on 2008-01-05
Had the same issue but found another, similar, fix. Thought I would share in the event that anyone needs it.

My laptop, Fujitsu T4215 running Gutsy, failed to lock the screen when I closed the lid like it always did in Edgy and Feisty.
I had the System->Preferences->Power Management set to blank screen on close
I had the System->Preferences->Screensaver set to both "activate on idle" and "lock screen when active"
Yet it still did not lock when I closed the lid (until it was closed for longer than the idle time set in the screensaver settings).

Here is my solution:

Load up gconf-editor navigate to and enable: /apps/gnome-power-manager/lock/use_screensaver_settings

Checking this overrides your individual settings for blank_screen, hibernate, and suspend to match whatever you have set in the screensaver for "lock screen when active" which is the effect I wanted, but it is, of course, up to you!

---

### Post by opakedragon on 2008-06-17
> **FuturePast said:**
> Try $ gconf-editor and look in key /apps/gnome-power-manager/...

I have Dell Inspiron 9300 and this work perfectly just had to check /apps/gnome-power-manager/lock/blank_screen and I close lid + open lid = locked screen. :-) thanks FuturePast!!!

---

