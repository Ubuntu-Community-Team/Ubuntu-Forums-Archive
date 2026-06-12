---
title: "Cannot start X server"
date: 2005-05-25
forum: Absolute Beginner Talk
---

### Post by F1_error on 2005-05-25
I'm a complete Linux newbie, and I just installed Ubuntu on a blank system. No other OS on there. 
When I go to start I get a message:
"I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Of course looking at the X server output is greek to me at this point. Is this normal? Is there more I have to do to set this up? Basically what do I do now?

---

### Post by Xian on 2005-05-25
[QUOTE=F1_error]Of course looking at the X server output is greek to me at this point. Is this normal? Is there more I have to do to set this up? Basically what do I do now?[/QUOTE]
The Ubuntu installer attempts to automagically configure your peripherals and graphics, but it occasionally does not do the job properly. Boot into either rescue mode, or just drop to the login prompt after that error message, and use the command below to reconfigure your system manually.
```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by poofyhairguy on 2005-05-26
What this means it that your install went badly. Ubuntu is VERY sensitive on the install and the slightest thing off can mess up the xserver. try reinstalling. If that doesn't work, your install CD is a dud (happens to me alot). Then reburn the install the at lower speeds on better media and try again.

A music cd player can just skip over imperfections. Installing requires much higher quality.

---

### Post by F1_error on 2005-05-26
Awesome sudo worked it all out for me. Huge thanks for that.

---

### Post by crimsonrevolverl on 2005-05-26
Hi, I'm a new user and I'm having the same problem only I did what was recommended and came up with a message that said that xserver-xorg was not installed. Do I have to re-install Ubuntu?

---

### Post by Xian on 2005-05-26
[QUOTE=F1_error]Awesome sudo worked it all out for me. Huge thanks for that.[/QUOTE]
Yeah, sometimes it just takes the manual touch. :)

[QUOTE=crimsonrevolverl]Hi, I'm a new user and I'm having the same problem only I did what was recommended and came up with a message that said that xserver-xorg was not installed. Do I have to re-install Ubuntu?[/QUOTE]
Not if you are running the Warty version of Ubuntu.
It doesn't use Xorg. You would need to issue this command:

```
$ sudo dpkg-reconfigure xserver-xfree86
```

---

