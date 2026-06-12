---
title: "WINE application disappeared from Gnome desktop"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by digitalcat on 2007-11-01
So I was playing with the cube desktop thingy today with Grabit running on WINE, and the next thing I know the Grabit window has totally disappeared and nowhere to be found in any of the workspace.  The process can be found in terminal by ps -e command, but I have no idea how to recover the window. Wonder if anybody here has had similar problem? BTW, 1st Ubuntu post, ):P

---

### Post by Factory on 2007-11-01
Hallo digitalcat! Welcome to the wonderful world of linux troubleshooting :).

I'd suggest trying to killall / restart the Grabit application.

Depending on how the program shows up in ps -e (I don't mess around with wine too often), you'll want to either issue

```

sudo killall wine

```

or

```

sudo killall Grabit

```

Then I'd suggest trying to re-run Grabit with wine from within a terminal so you can get any error output and try to re-create the situation.

Navigate to the grabit directory within a terminal and type
```

wine Grabit.exe

```
or whatever the executable might be named. Then try playing with the cube effect again and see what happens. Finally, post your output! Voila.

---

### Post by digitalcat on 2007-11-02
Thanks a lot for the advice. I killed the processes (wine and grabit.exe) by sudo kill -9 XXXX. They were actually zombies after I tried to kill it normally the first time. Then I restarted Grabit and so far haven't been able to replicate the same problem.

---

### Post by omnicore on 2008-02-16
I had the exact same problem happen to me today. I was using grabit and moved it to another desktop and when I moved over to that desktop the application disappeared.

---

### Post by stderr on 2008-05-02
Same problem here, except worse in Hardy.

It was similarly intermittent for me on Gutsy, with the added complication of tooltips from the Grabit window occasionally->frequently permanently sticking to the screen. If you switch workspace, they're still there - you have to restart X, or start another X server.

Since upgrading to Hardy, things have gotten worse - every time I start Grabit and either a) minimise it, b) place it on another workspace, or even c) just leave it for a period of time, as before, it will disappear from everywhere but ps aux etc. This disappearance is practically instantaneous for a) and b).

*scratches head*

---

