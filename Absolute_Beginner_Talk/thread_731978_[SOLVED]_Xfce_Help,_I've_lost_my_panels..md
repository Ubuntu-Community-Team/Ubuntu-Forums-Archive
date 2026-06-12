---
title: "[SOLVED] Xfce: Help, I've lost my panels."
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2008-03-22
Hi Folks,

As the title says, I've lost my panels in Xubuntu 7.10.

HISTORY: (an hours or so ago)
Turned on computer
Cheched my mail, answered three mails.
Opened  Firefox and logged in to Ubuntu Forums
 ... Conky shows:
 ... ... 2 of 96 processes running
 ... ... CPU Usage zipped up to 100%;
 ... ... Mem: RAM up to 28%;
 ... ... Swap: 0%
 ... Computer locked up, couldn't close Firefox
 ... [Ctrl]+[Alt]+[Backspace]
 ... Logged in
 ... Started nothing
 ... ... Conky: CPU Usage zipped up to 100%; Mem: RAM up to 40%; Swap: 0%
 ... NO PANELS

I checked out:  [Lost panels in XFce desktop]("http://ubuntuforums.org/showthread.php?t=614866") that has a link to:  [Xubuntu 7.10 Menu Bar disappeared]("http://ubuntuforums.org/showthread.php?t=608389") that links to: [Xubuntu 6.06 Desktop Menu Bar and Window Bar gone]("http://ubuntuforums.org/showthread.php?t=312394").

OK, in that last link I did what was suggested.

**Step 1:**
```

-(~)----------------------------------------------------------(13:25 Sat Mar 22)
bruloo@bruloo [136] --> pgrep -l xfce4-panel
-(~)----------------------------------------------------------(13:25 Sat Mar 22)
bruloo@bruloo [137] --> 
```
If it's not there, enter xfce4-panel and press return, and possibly your panels will reappear.

If it is there it will return something like this ...
```
5535 xfce4-panel
```
As you see above ... no returned code, no panels.

OK, panels not there. So I skipped the "it's there step" and went to "my" Step 2:

**Step 2:**
Next, let's back up the old configuration file, just to be safe.
```
cp ~/.config/xfce4/panel/panels.xml ~/panels.xml.old
```
DONE!

**Step 3:**
Now remove the old configuration file.
```
rm ~/.config/xfce4/panel/panels.xml
```
DONE!

**Step 4:** 
Now restart the panel process, and hopefully fresh panels should appear.

```
xfce4-panel
```
Perfect, I have the Generic Panels (missing Places)

Close Terminal and the Panels disappear!
Reopen terminal and re-issue the command and the generic panels come back.

Hmmmm. Close terminal, panels disappear again.
Reopen terminal and re-issue the command and the generic panels come back.

Open Thunar and go to: /home/bruloo/.config/xfce4/panels

**There is NO panels.xml file nor panels.xml.old file**

and the Generic panels have:

TOP: Applications (no Places) Firefox Help ... on the right: Time and Quit
BOTTOM: Desktop ... on the right: 2xWindows and Trash (empty)

Help is needed and would be appreciated.
Bruce

---

### Post by lloyd_b on 2008-03-22
I've had that happen a few times.  Try this:

1.  Open a terminal window
2.  Run "xfce4-panel"
3.  Log out (without closing the terminal window).

Using this method, when I log back in the panels are auto-starting again.  Hope this method works you.

And regarding the missing "panels.xml" and "panels.xml.old" - if what you posted is what you typed, the "panels.xml.old" is in your home directory, not in "~/.config/xfce4/panel"

Lloyd B.

---

### Post by Bruce M. on 2008-03-22
> **lloyd_b said:**
> I've had that happen a few times.  Try this:

1.  Open a terminal window
2.  Run "xfce4-panel"
3.  Log out (without closing the terminal window).

Using this method, when I log back in the panels are auto-starting again.  Hope this method works you.

And regarding the missing "panels.xml" and "panels.xml.old" - if what you posted is what you typed, the "panels.xml.old" is in your home directory, not in "~/.config/xfce4/panel"

Lloyd B.

Hi Loyd,

[CENTER]**THANK YOU!**[/CENTER]

:) You're right, in my "panic" I didn't realize that it went to my home folder. I just copied it to ~/.config/xfce4/panel where it'll be safe.

Bruce

---

