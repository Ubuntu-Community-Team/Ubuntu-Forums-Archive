---
title: "update-notifier - how do i get it back?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-12-20
I accidently removed the update notifier from the panel.  (that's the little asterisk orange icon on the top bar)
Now I can't seem to get it back.

I was able to add a custom application launcher, but the icon is too big and doesn't show the number of updates available.  What's also wierd:  The update-notifier is still running (even after rebooting).  I can see it with ps -ef | grep update

There seems to be something special about this icon.

---

### Post by moshuptrail on 2006-12-21
does anyone know this tonight?

---

### Post by tc10b on 2006-12-21
Go to 

System -->Preferences -->Sessions

Click on the startup programs list, if it's not there already add a new command and type

update-notifier

then reboot and it should be back, but you won't know until there are updates to be done.

Hope that helps.

Tom

---

### Post by moshuptrail on 2006-12-22
Well, that's the odd thing.  Update notifier is listed in the sessions screen.  As I said before, I can also prove that it's running by doing a $ ps -ef | grep update command.  It shows up in the process list.  It's the just icon that's missing from the panel.  Also, I know there's at least one kernel update that is out there that I haven't installed yet.  So it's not a lack of updates.

RESOLVED!   I just discovered the secret.

Right-click on the panel and select +Add to Panel.  
Slide all the way down to 'Utilities'
Choose the icon labeled 'Notification Area' (it does not look at all like the orange asterisk)

Why it's not called update notifier I'm not sure.  Maybe the same icon is used by other notifications. (?)  Also, the icon shown doesn't look anything like what will appear on the panel after you choose it.  I can see an improvement suggestion coming....

---

### Post by mwww on 2007-01-23
thanks a lot - had the same problem. 

Actually, on my machine the "Notification Area" has a little dotted handle on its left side and it consists of the Notification icon (=orange asterisk) and the Power Manager icon. I had lost both of them and they reappeared after following the procedure you described.

I recommend to rightclick the "Notification Area" handle and select "Lock to Panel" so hopefully I won't be able to accidentially remove it again.

[Googling around, I was initially mislead because I got lots of hits referring to "adept_updater" (seemingly part of Kubuntu).]

---

