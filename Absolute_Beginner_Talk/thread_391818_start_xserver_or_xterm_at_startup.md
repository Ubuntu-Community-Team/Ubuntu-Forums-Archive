---
title: "start xserver or xterm at startup"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by krazyman on 2007-03-23
Hi All,

I have two Ubuntu machines running on my home network. I want to connect to the second machine after starting it up, but without having to log that machine in first. I have VNC running ok, but is there a way I can connect via an xterm session that can run 'in the background'? I am hoping this would also be smoother than VNC... 

Many Thanks,

Andy

---

### Post by Kobalt on 2007-03-23
I guess there is a way to do it through [SSH]("https://help.ubuntu.com/community/AdvancedOpenSSH"). Have you digged towards this solution yet ?

---

### Post by martinw89 on 2007-03-23
To have a computer skip asking for a password you can use [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s01.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s01.html)

If you just want terminal access to the other computer, you could use SSH.  You could make a script that would automatically sign in (I don't know how exactly but I'm sure a Google search for something like "ssh login script" could find it).

---

### Post by krazyman on 2007-03-23
Thanks for your replies. I want gui access to the other machine, but I was wondering whether there is some sort of remote desktop capability that I can use, akin to terminal services or remote desktop in windows. That would be neater and more secure than making the machine log in automatically? Plus the screen wouldn't be 'echoing' everything I was doing. I plan to use the second machine as a server in the long term, but have installed the standard ubuntu so I was more familiar with things as I set it up.

---

