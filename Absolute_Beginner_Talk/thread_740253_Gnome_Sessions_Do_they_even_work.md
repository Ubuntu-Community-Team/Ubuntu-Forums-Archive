---
title: "Gnome Sessions: Do they even work?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by softtower on 2008-03-30
I wanted to change a few things regarding applications that automatically start every time I login into Gnome.

So...
[LIST=1]
[*]I go to System/Preferences/Sessions and get Gnome's "Sessions" dialog. I switch to "Current Session" tab. 
[*]I find the application I want to get rid of, I read documentation (by pressing "Help" button). 
[*]I delete the app from the list and press "Apply". I reboot and see it there again.
[*]Ok, I change it's "startup settings" to "Trash", just like documentation suggests. I hit Apply, I reboot, the app is still there.
[*]Ok, I decided to change the startup order of that app. I do that, hit "Apply", reboot -> no effect.
[/LIST]
Basically this "Current Session" tab doesn't remember anything I do in it. WTF? Why is it even there? What does it do and what is it for? I am really frustrated... I've been using Ubuntu for over a year, and I keep getting back to this "session puzzle" that I can't solve.

Thank you in advance, I really look forward to solve this mystery.

P.S. The annoying app I want to get rid of is "trackerd". Because it also does not appear to index anything, regardless of my attempts to configure it via System/Preferences/Indexing Preferences.

---

### Post by TenPlus1 on 2008-03-30
Why not just goto System -> Preferences -> Sessions and under the Startup Programs tab, untick Tracker Applet, which will disable tracking altogether without the need to uninstall anything...

The Current Session tab just shows you what is currently running and allows you to close/remove things for THAT session only, it doesnt survive a reboot, only the Startup Programs tab is remembered...

---

### Post by caljohnsmith on 2008-04-16
> **TenPlus1 said:**
> The Current Session tab just shows you what is currently running and allows you to close/remove things for THAT session only, it doesnt survive a reboot, only the Startup Programs tab is remembered...

I'm having a similar problem, and based on what you are saying, I don't think I understand then why under the "Current Session" tab you can modify the startup order of the programs if it doesn't apply to the next reboot. Does changing the startup order in the "current sessions" tab only apply if you have checked "Automatically remember running applications when logging out" under the "Session Options" tab?

I don't really want Ubuntu to remember what programs I happen to have running on logout, and then restart them all; what I really want is for Ubuntu to simply load the apps listed under the "startup programs" tab, but I want to be able to modify their loading order. Is this possible? When I highlight an app and click "edit" it has no option to set its startup order.

Any help would be greatly appreciated. :)

---

### Post by caljohnsmith on 2008-04-21
*bump*

Can anyone please help me out? :confused:

---

### Post by Vadi on 2008-04-21
I'm not sure what order are they launched in, because it's pretty instantaneous for me :/

---

