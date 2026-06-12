---
title: "FreeNX on kubuntu/ppc 6.06? (or x11vnc)"
date: 2006-08-01
forum: Apple PPC Users
---

### Post by paulsomm on 2006-08-01
I was using Vino under gnome and was quite happy.  I switched to KDE and tried using KRFB, but it disconnects after a few seconds after causing 100% CPU spikes, and when it does stay connected it seems to send dozens of copies of each keystroke.  I switched to x11vnc using the howto posted on this forum, but it also seems a bit clunky as it tries to turn on the screensaver every time I click away from VNC, and it seems to skip a character of keystrokes randomly.

I saw posts about how wonderful people think FreeNX is, so I thought I'd give it a try.  I added the saveas repository for dapper, imported the GPG key, ran an aptitude update, and saw "freenx" available for install.  However, if I choose to install it, "nxagent" is not available so I can't actually install it.

Does FreeNX work on PPC (K)Ubuntu?  If so may I ask for some assistance in setting this up?

If not, does anyone have a usable, working x11vnc install (that doesn't seem to grab keystrokes)?  Or, heck, I'd settle for KRFB if it was useable . . .

Thanks guys/gals

Edit: I've confirmed the x11vnc losing keystrokes to only be a problem in KDE.  Works great in gnome and xfce.  I did notice that I don't think it's so much losing a key as the focus appears to shift to some invisible process every 5-10 seconds for about a second.

In any event I'd still rather love to get FreeNX working.  It sounds to be a much better solution.

---

### Post by paulsomm on 2006-08-01
While I'm still investigating getting FreeNX to work, I thought this might be useful for people to know.

I rebooted my machine and, of course, had no :0 console to connect x11vnc to.  Did you know you can have x11vnc grab control of the greeter (kdm/gdm/xdm, etc)?  Simply append the following to your x11vnc command:

-auth /var/run/xauth/A:0-WD3PoW

where "/var/run/xauth/A:0-WD3PoW" is what you see after running:

ps wwaux | grep auth

If you read the output of x11vnc when you try to run it with no :0 session, it tells you how to do this.  Of course, for me, as soon as KDE starts up the flaky behavior of the screensaver starting and keystrokes disappearing happens again . . .

---

### Post by krunge on 2006-12-12
There is some info here now:

[http://www.karlrunge.com/x11vnc/#faq-kde-screensaver]("http://www.karlrunge.com/x11vnc/#faq-kde-screensaver")

---

