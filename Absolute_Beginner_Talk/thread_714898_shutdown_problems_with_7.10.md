---
title: "shutdown problems with 7.10"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by scotboi on 2008-03-04
I am pretty new to UBUNTU but am determined to stick with it as just do not like M.S stranglehold.
I installed Feisty Fawn even though Gusty Gibbon (7.10) had come out as the there were no idiots guide for 7.10. i was getting frustrated at so many things not being there (like Java) and constantly having to go and see if there was an upgrade - finding there was but told had to do manual install and had no clue how to do that -so in then end decided to go for 7.10.

Installed it and had two problems. First one was the message "gnome manager not properly installed". Went and looked on this site and found others had same problem, posted messages but no replies. I went and tried to sort it out myself and did - how I do not know!

The other problem is that the shutdown button - whenever I hit it it automatically shuts down and restarts - no options or anything - just reboots! I have resorted to hitting it and as it shuts down - switching it off at the mains; know this can not be good for the system - but have  no other options. Can anyone help me with how to make the exit button give you the choice shut down/log off/restart etc as this must be making a real mess of my system

ta in advance for any help.

chris

---

### Post by lswest on 2008-03-04
that's very, very strange.  I'm not sure how to fix it, but for your information, to shutdown run ```
sudo halt
``` from the terminal.  Also works with reboot.  If you wanted, you could add that into a launcher and use it to replace your "quit" icon.  If you want to, right-click your panel, choose "add to panel" -->custom application launcher (at the top, one of the 2 tabs) then make one of type: application in terminal; Name: shutdown or w/e you wanna call it; command: sudo halt; comment: shuts down the computer.  Hope it helps you be a bit less frustrated, maybe someone else can fix the quit menu for you.

---

### Post by {BzF}~JOKesTER on 2008-03-04
As For The Gnome Manager:  In The Tray Goto: System>>Administration>>Update Manager And Update As Necessary. 

As For The Auto Restart Of CPU When Pressing The Power Button : In The Tray Goto >>System>>Preferences>>Control Center - Find "Power Management" Click It, Goto The General Tab:
And Change "When The Power Button Is Pressed" To: "Ask Me"

Hope This Helped!!

---

### Post by scotboi on 2008-03-08
Thanks guys: I tried your suggestion Iswest - it works - though slightly longway round - but not much and it works - ta :-)

{BzF}~JOKesTER. I treid update manager and it said was up to date. I went to power manage as you suggested and it was already set up for "ask me". I have thought changed it to "shut down" and am just going to see if that has made a difference.

but thanks again guys for taking time to try and help me with this annoying problem

:)

---

