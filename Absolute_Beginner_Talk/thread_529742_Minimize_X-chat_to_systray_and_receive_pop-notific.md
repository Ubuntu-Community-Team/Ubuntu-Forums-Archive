---
title: "Minimize X-chat to systray and receive pop-notifications"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Barleyman on 2007-08-19
Hi all, did some searching for how to Minimize X-chat to systray and receive pop-notifications, but all talk is over 2 years old.

I currently have xchat version 2.8.0 installed from universe repo, but I am unable to see how to minimize to systray on close and receive pop up notifications.  This is the default behavior in Fedora Core 7.   

I tried to install systray-chat plugin but it did not seem to have any effect even after configuring it.

Any help would be appreciated.

---

### Post by walkerk on 2007-08-19
Settings > Preferences > Chatting > Alerts.

Enable system tray.. Hope this helps.

---

### Post by Barleyman on 2007-08-19
> **walkerk said:**
> Settings > Preferences > Chatting > Alerts.

Enable system tray.. Hope this helps.

Thanks, that is what I tried and currently have enabled, however when I hit 'X' to close xchat it shuts down completely (can no longer see xchat process running).   I was hoping to start it once and then when I hit close, it just minimizes to systray.

---

### Post by moredhel on 2007-08-19
click on the system tray icon itself :P

---

### Post by walkerk on 2007-08-19
> **Barleyman said:**
> Thanks, that is what I tried and currently have enabled, however when I hit 'X' to close xchat it shuts down completely (can no longer see xchat process running).   I was hoping to start it once and then when I hit close, it just minimizes to systray.

If you enable the systray icon you need to click that icon to minimize to tray.. :)

---

### Post by Barleyman on 2007-08-19
Thanks, I knew that worked, but wanted a way to make sure if I closed it, it would just minimize to systray.

I found a solution for this though.  Here it is ->

Go to chat window and and enter this message.

/set gui_tray_flags 1

I now am able to hit close button and xchat is minimized to tray.

Thanks for your help though.

---

### Post by bionnaki on 2007-10-30
exactly what i needed thanks.

---

