---
title: "something killed my dbus."
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by univremonster on 2007-12-06
I've had this problem ever since installed (successfully) Gutsy.  Whenever I have updates it gives me this big warning about how my last upgrade wasn't complete, even though everything seems to work fine after a few months of using it.  So it says I should do a partial upgrade, and when I click ok to do that it dies.  So I tried running it from terminal and I get this error that says 

"warning:  could not initiate dbus"

I have no clue what a dbus is or how to bring one back from the dead, but I would like to complete my installation if it really didn't finish.  By the way, if it's important, I downloaded Gutsy and did a fresh install because I'd upgraded from 6.06 to Fiesty and thought it was time to clean up a little bit, so there shouldn't be any upgrade problems.

---

### Post by p_quarles on 2007-12-07
dbus is a system that allows applications to "talk" to each other. Ubuntu sometimes has little issues with it, particularly if something gets misconfigured.

To revive it from the grave, you can run:
```
sudo /etc/init.d/dbus start
```
If that returns an "already running" error message, use this instead:
```
sudo /etc/init.d/dbus restart
```
On the one occasion that I ran into this problem, it was fixed by running that command once, and I never experienced it again.

It also sounds like there's a problem with one or more software packages. Packages can get broken if the download is corrupted, interrupted, etc. The first thing to try is:
```
sudo apt-get -f install
```
That will attempt to fix broken packages, and hopefully will resolve the issue. Let me know how it goes.

---

### Post by univremonster on 2007-12-18
Quarles,

Thanks for your reply and sorry I was slow in responding.  I tried reviving dbus as your post suggested, and it did indeed work in that there were no errors or problems.  I got the "your dbus is already running stupid" message when I tried to start it and a nice reboot (got to watch everything shut off and restart like internet connection and such).  Unfortunately that didn't solve the partial upgrade situation and it still says dbus fails to initiate.  I'm trying to upgrade to Hardy Heron right now, maybe that will help.

---

### Post by p_quarles on 2007-12-18
Hardy Heron is still 5 months away from release, and not stable at all. The only reason to use it is if you're willing to provide testing feedback to the developers, and in that case any problems would belong in [this sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=305").

---

### Post by univremonster on 2007-12-22
Rather than accept your advice I tried installing it anyway and it never even started up for me.  So it goes.  Anyway, I reinstalled Gutsy and I got the following message at the first startup:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

As I recall I got this at my last install and ignored it because it never seemed to cause any problems and I'm fine with the default theme.  Perhaps this is related to my dbus issue?

---

