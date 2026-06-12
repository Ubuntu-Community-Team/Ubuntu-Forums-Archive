---
title: "Alt_R key not working in Feisty Beta on Dell Inspiron"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by kwilliam on 2007-04-17
I recently installed Kubuntu Fiesty Beta on a Dell Inspiron 6400, and the Right Alt key doesn't do anything.  With xev I determined that the right Alt key is 113.  Here's the output of xmodmap -pke
```
keycode  64 = Alt_L Meta_L
keycode 113 = ISO_Level3_Shift
```

I've tried ```
xmodmap -e 'keycode 113=Alt_R'
``` but it doesn't seem to have an effect.  What can I do, and who could I notify so that it can be "fixed"?  (Of course, it might already be fixed... I am not upgrading my packages until Feisty is officially released.)

---

### Post by kolinab on 2007-04-18
Huh, mine doesn't work either. I haven't ever tried to use it I guess. 

I'm on a Dell Inspiron 630m.

---

### Post by kwilliam on 2007-04-18
> **kolinab said:**
> I haven't ever tried to use it I guess.

I don't think I would have noticed it either if I hadn't tried to do Ctrl+Alt+Backspace with one hand.  :-)

---

### Post by kolinab on 2007-04-19
Good point. lol. I'll stay tuned to see if anyone else chimes in on this.

---

### Post by gribelu on 2007-04-19
Same problem here.. I noticed it a while ago but i decided to ignore it till now :)
Looking for a solution but no luck so far
---------------EDIT
Found a solution.. Well there's actually two solutions in there -> [http://ubuntuforums.org/showthread.php?t=287318&page=2]("http://ubuntuforums.org/showthread.php?t=287318&page=2")

---

### Post by TwistesdTexan on 2007-04-19
I just tried it on mine and it took me to the login screen Is that what it's suppose to do?(Ctrl-Alt-Backspace)

---

### Post by gribelu on 2007-04-19
Did you also edit xorg.conf as explained before that? Ctrl-Alt-Backspace just restarts X (the GUI)

---

### Post by kwilliam on 2007-04-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107768](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107768) [br].[/br] ---------------------------- [br].[/br] [br].[/br]> **gribelu said:**
> Found a solution.. Well there's actually two solutions in there -> [http://ubuntuforums.org/showthread.php?t=287318&page=2]("http://ubuntuforums.org/showthread.php?t=287318&page=2")

Wow!  Commenting out that line in xorg.conf worked perfectly!  I'm reporting this as a bug.  (I'll take a chance and assume it wasn't fixed in the few weeks between when I installed Feisty beta and the release of Feisty official today.)

@TwistedTexan:  Ctrl+Alt+Backspace restarts the X server, which is the program that draws stuff on the screen.  It is useful as a last resort if the screen seems hung (although the *real* last resort is Alt+SysReq+ a key sequence that make the computer shutdown more politely than pulling the power cord) and - more frequently - changing stuff in xorg.conf (for instance, if you're trying to change screen resolution) because it is quicker than logging out the normal.  Don't do it without saving any work though.

---

### Post by kwilliam on 2007-04-20
**This post is directly related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/76901](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/76901) [br].[/br] ---------------------------- [br].[/br] [br].[/br]				Ahh! This bug was already known and resolved: [https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/76901](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/76901)
However, it might still affect those who installed Feisty Beta, if I understand correctly:
> I think it's too risky to attempt to fix this on upgrades, so I haven't. If you want to do so yourself, change 'XKBOPTIONS="lv3:ralt_switch"' to 'XKBOPTIONS=""' in /etc/default/console-setup and remove the line 'Option "XkbOptions" "lv3:ralt_switch"' from /etc/X11/xorg.conf.  -- Colin Watson <cjwatson@ubuntu.com> Sun, 1 Apr 2007 16:49:02 +0100

Interestingly, my /etc/default/console-setup was fine, so either it was always good or it *did* get changed in upgrades.  My /etc/X11/xorg.conf file stayed the same, probably because I had edited it by hand so it doesn't get updated.

lv3:ralt_switch is an option for non-US keyboard layouts, it appears.

---

