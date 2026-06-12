---
title: "KDE won't start anymore."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by HungLO on 2007-08-05
I've been playing around with KUBUNTU trying to find my way around and trying to customize it to my liking. Now the problem, after tinkering around with beryl setup (I'm not sure if this is the root cause of the problem) KUBUNTU won't start. It only fully starts from recovery. If I try to start it normally, after the login, it will go to a blank desktop with an active konsole session in which I type "startkde" (this used to happen with no user input before). Once I do that, it seem like is going to start normally; my modified desktop flickers briefly and the recycles back to my original login screen. During this process, I noticed a few errors scrolled by too fast to make note of them.

I've been trying o search everywhere for a solution. Please help.

Thanks in advance.

---

### Post by luisromangz on 2007-08-05
It seems that you are login into the failsafe session. You can change the kind of session you are going to use in KDM before you log in. Maybe you entered the failsafe mode while setting up Beryl, and it keeps using it because the default policy is to default to the last used session.

---

### Post by HungLO on 2007-08-05
I tried all possibilities (default, KDE, failsafe) prior to login in and none worked like before. The only option that work as before was "console login" (Alt+N); it puts me at the command line and ask for user name and password, once there I have to start X and everything runs like normal (old desktop). The only different thing that I've noticed is that there is no "shutdown" or "reboot" options under "K" menu. I have to shutdown from Konsole.

Any ideas?

---

### Post by luisromangz on 2007-08-12
Well it seems I missed the point of your first post as it seems you are actually not using Konsole in the failsafe session but a virtual terminal. Konsole can't run without a graphical desktop, the text mode console is called virtual terminal.

If you run startkde from the command line, it is normal that you don't get the shutdown and reboot options, as those options are provided by KDM, which you are bypassing, as it doesn't let you login into any kind of session but that of the virtual terminal.

I'm wondering that if startkde works, it is not a problem with kde setup itself, but maybe there is something else wrong.

I would check the files under /usr/share/xsessions. It should be one fille called KDE.desktop, which this lines at the start:

```

[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE

```

and some descriptions in various languages following. Check that the commands are right.

---

