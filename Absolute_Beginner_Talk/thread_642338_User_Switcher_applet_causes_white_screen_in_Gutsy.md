---
title: "User Switcher applet causes white screen in Gutsy"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by mor gaiscioch on 2007-12-16
When using Panel's User Switcher applet, I often (though not always) get a white screen rather than a login prompt. I've read what topics I could find on the issue, and I did a little searching on launchpad for a bug (though I, admittedly, don't know where to look) and I've seen it being offered as a "fix" to disable the locking of the screen in the applet's preferences, but this won't really suffice in my particular case for security reasons.

In one particular instance, I had the same problem when switching user's from the quit... applet as well, though I don't often do it and haven't been able to replicate it from there since.

---

### Post by RIchard James13 on 2007-12-24
I too get this white screen. I find it is compiz crashing or something. Removing compiz stops the white screen from appearing. Note I get this constantly not once in a while.

---

### Post by RIchard James13 on 2007-12-25
Further I have just changed video card from an ATI to a NVIDIA one. Compiz still crashes. Furthermore when I tried to user switch and kill compiz I found two instances of compiz running. One fro each user. Killing the inactive instance of compiz gets rid of the white screen. Obviously there is something wrong with compiz running twice.

---

### Post by aonegodman on 2008-01-03
I just started having same problems and had to change my appearance effects back to NONE to get open windows back to normal.

I has a blank white screen with only mouse curser on start up desktop first and then after reboot I got my desktop back.

Next when I opened Terminal I got nothing but a white window again. I think its Compiz going nuts.

Just ran Ubuntu updates yesterday 01/02/08 before shut down. Could this have had some effect?

Any others experiencing similar results?

I have an Nvidia MX440 card.

---

### Post by CharlieFoxtrot on 2008-01-03
Yup, there's definitely a conflict switching users with Compiz, using the switcher applet or otherwise. When white-screened, typing the password of the orginal user (and enter) restores the first user's session. Turn off Compiz and there's no problem.

I've also run into another conflict with Compiz and Xsane scanning. When the scanned image window opens, it covers the entire screen including the panel and taskbar and is lacking a window title. Have to alt-tab to get to any other window or even a dialog. Turn off Compiz and there's no such problem.

---

### Post by argie on 2008-01-03
I have this problem too. It's like this. Compiz requires Direct Rendering to function. When I switch users the second user will never have direct rendering (I am unsure whether this is a limitation of Xorg or of my Intel driver) and, as a consequence, cannot use compiz. For some reason, compiz does not test for direct rendering or is unable to detect the fact that it is not available.

I noticed this because I tried switching back to the first user using Ctrl-Alt-F7 and it was all well.

---

### Post by Sukarn on 2008-01-05
There are so many of these threads popping up, its like people don't even search for anything before posting the same thing that has been said so many times already.

My suggested temporary fix is to switch to a virtual console like tty1 and then switch back to X-window system (graphical interface).

The required key combo is Ctrl+Alt+Fx,
Where x can be anything between 1 - 6 for tty1 - tty6, and for switching to X Window system it can be anything between 7 and 12 on a default install.

**EDIT:**
> **argie said:**
> I have this problem too. It's like this. Compiz requires Direct Rendering to function. When I switch users the second user will never have direct rendering (I am unsure whether this is a limitation of Xorg or of my Intel driver) and, as a consequence, cannot use compiz. For some reason, compiz does not test for direct rendering or is unable to detect the fact that it is not available.

To me it seems like its a problem specific to your hardware or software. On my computer, compiz seems to work fine for both users.
It may be a more widespread problem then I realize though, so please don't start a flame war here.

---

### Post by RIchard James13 on 2008-01-05
Thanks for you hint Sukarn but even if I switch to a Console and back X is still mucked up. The problem is that compiz when run twice by using the fast user switching system locks the screen to white. In order to bypass this you need to either
[LIST]
[*]Enter the users password into the blank screen
[*]Kill that users version of compiz from the console
[*]Or not use compiz and fast user switching
[/LIST]

I further believe that the problem lies somewhere within the fast-user switching code. I have tried using two simultaneous X servers by going into the console and logging in as the other user and typing startx -- :1 this allows me to switch between both instances of X (Ctrl-Alt -F7 - F9) with no problems, so it doesn't appear to be related to a compiz locking issue.

---

### Post by barbedsaber on 2008-01-05
Hey, at least its not a blue screen :lolflag:

---

### Post by Sukarn on 2008-01-05
> **RIchard James13 said:**
> Thanks for you hint Sukarn but even if I switch to a Console and back X is still mucked up. The problem is that compiz when run twice by using the fast user switching system locks the screen to white. In order to bypass this you need to either


Hmm... Interesting. On my computer, the second user has always logged out before trying to get back to the "white" login screen. Logging in works fine here by blindly typing the user name and password, but ofcourse, you can't see it. However, on this particular computer, the white screen has always gone away by the method I stated in my previous post, to be replaced by the normal login screen.

Logging in blindly (from the white screen) brings me to my normal desktop (not another white screen).

---

### Post by RIchard James13 on 2008-01-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes when I switch to another user it doesn't occur. When I switch back it does occur, if I type in my password at that point the white screen disappears and I can use the computer again.

I was getting really annoyed with this bug so I have looked around there is no bug logged with gnome 
[http://bugzilla.gnome.org/buglist.cgi?query=fast+user+switching+applet]("http://bugzilla.gnome.org/buglist.cgi?query=fast+user+switching+applet")
but there is a bug logged with Ubuntu.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264")

On that page they seem to think the problem is in the NVIDIA driver somewhere. 

> Based on this, I suggest a workaround for the bug. We must avoid window creation on inactive VT, so rather than just using Fast User Switch Applet one should lock the screen manually (ctrl+alt+L) and then use the Switch User button. Screensavers/time-based screen locking should be also turned off - use explicit lock instead. Fast User Switch Applet can also be configure not to lock the screen. *Andrey Vihrov*

Going by that if you right click the fast user switcher and select preferences you can turn off "Lock the screen after switching users". You need to do this for each user. This lowers security but does bypass this bug.

Waiting on NVIDIA to fix this bug.

---

