---
title: "Need a scrap notifier.."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-15
Hello all
I use Orkut (Google services). I used to have popups with google-talk whenever I got a new scrap.. Is there any plugin for pidgin that would work as a scrap notifier?

---

### Post by forrestcupp on 2008-03-15
I know it's probably not at all what you're looking for, but would [Alltray](http://alltray.sourceforge.net/) help?

---

### Post by sayakb on 2008-03-15
> **forrestcupp said:**
> I know it's probably not at all what you're looking for, but would [Alltray](http://alltray.sourceforge.net/) help?

Not exactly.. I do have alltray, just dosn't seem to work (I can't dock anything :( )
Anyway, just as thunderbird gives a notification when we get a new mail, I wish pidgin shows a notification when I get a scrap on orkut..

---

### Post by forrestcupp on 2008-03-15
Sorry, I don't know about a notification for pidgin.

But if you want to dock something with alltray, you just have to change the launcher command.  Like if the command for opening Thunderbird is
```
thunderbird
```
You just change it to 
```
alltray thunderbird
```
Then when you open it, it will dock to the notification area.

---

### Post by sayakb on 2008-03-15
> **forrestcupp said:**
> Sorry, I don't know about a notification for pidgin.

But if you want to dock something with alltray, you just have to change the launcher command.  Like if the command for opening Thunderbird is
```
thunderbird
```
You just change it to 
```
alltray thunderbird
```
Then when you open it, it will dock to the notification area.

When I do this:
```
alltray firefox
```

A new firefox window appears. When I minimize it, it goes to the AWN icon.. when I close it, it simply closes, but the command is still active in the terminal. Plus, I don't have the "Window List" applet on my panel (because I use AWN).. will that matter?

---

### Post by forrestcupp on 2008-03-15
You need to include the Notification applet in your AWN dock.  It's ugly, but it works.  I think they're working on creating a nicer looking notification applet.

---

### Post by sayakb on 2008-03-17
But where can I get the notification applet??

---

### Post by forrestcupp on 2008-03-17
Did you install the default version in the repos, or did you install the bzr version?  If you installed the default version, you need to uninstall it, and go by [this guide](http://ubuntuforums.org/showthread.php?t=385981) to get the bzr version.  It is newer, and it has all of the applets.

After you do that, you can set the preferences, and you will find the notification applet in the applets section.

---

### Post by sayakb on 2008-03-17
Okay.. I added the notification applet.. But surprisingly, no new applet/icon turned up in the dock (while it shows that I am running the notification applet in the AWN Settings manager.. Plus, I still have no notifications for Orkut.com scraps.. Any clue??

---

