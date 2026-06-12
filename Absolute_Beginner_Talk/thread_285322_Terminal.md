---
title: "Terminal"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by CeeDub on 2006-10-26
I can't get the terminal running in edgy.  I click on the button, but nothing happens.  Can someone please help me?

---

### Post by localuser on 2006-10-26
Do you have /usr/bin/gnome-terminal?

Try to get to it with File Browser, and if its there, double-click it.

---

### Post by CeeDub on 2006-10-26
I clicked it, but the same thing happened.

---

### Post by localuser on 2006-10-26
> **CeeDub said:**
> I clicked it, but the same thing happened.

I hate to ask for fear of offending, but did you click or double-click?

---

### Post by CeeDub on 2006-10-26
I'm not offended, you never know.  I've clicked, double clicked, triple clicked.  I've even tried alt-f2 and trying to run terminal applications through that, but that doesn't work either.

ps. It was working earlier today.

---

### Post by raqball on 2006-10-26
> **CeeDub said:**
> 
ps. It was working earlier today.

Was it working earlier in edgy or dapper?

In other words do you think the upgrade broke it?

---

### Post by dbott67 on 2006-10-26
A few suggestions:
- CTRL-ALT-BACKSPACE
- Reboot and try again in normal mode
- Reboot and try again in safe mode

-Dave

---

### Post by localuser on 2006-10-26
> **CeeDub said:**
> It was working earlier today.

I see you're on 6.10, was that an upgrade?  If so then I assume you mean that it was working after the upgrade.  Assuming nothing else was changed on the system...

Did you try a reboot?

---

### Post by raqball on 2006-10-26
One last suggestion is to go into add/remove programs and make sure it is installed. If not check it to install. Another option is to check the Konsole option and use it in it's place.

---

### Post by CeeDub on 2006-10-26
Yes it was working in edgy just fine, I've rebooted and no change, I haven't tried safe mode yet, I'll get back to you.  The Konsole seems to be working, but I would still like to get the gnome-terminal working.

edit: recovery mode did the same thing.

---

### Post by scrillamaan on 2006-10-27
I'm having the same problem, except gnome-terminal never worked for me in edgy (I upgraded earlier this evening).

---

### Post by kerry_s on 2006-10-27
Does xterm work? If so try to launch gnome-terminal from there so you can see the error.

---

### Post by rumli on 2006-10-27
The problem might be related to Xinerama and nvidia-glx.  See [this thread]("http://ubuntuforums.org/showthread.php?t=276354") for more info and a possible solution.

---

### Post by CeeDub on 2006-10-27
Thanks rumli.  That was the problem.  Man these forums are great.

---

