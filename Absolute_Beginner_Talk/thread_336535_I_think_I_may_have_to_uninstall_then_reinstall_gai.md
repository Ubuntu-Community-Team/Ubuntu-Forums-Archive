---
title: "I think I may have to uninstall then reinstall gaim"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-11
I first got the message from the Yahoo portion that I'd logged in at another location and would not allow it until I rectified it. Just now got the same message from the MSN portion. It will not start up at all now. I have it at work (logged in and out on both), and on this home 'puter (ditto). Any suggestions other than an uninstall/reinstall? if not, how would I do that?

---

### Post by kj1h234lkj1234 on 2007-01-11
Not sure how to rectify your problem.

To reinstall:

```
sudo aptitude reinstall gaim
```

Or use Synaptic (System->Administration->Synaptic) to "mark it" for reinstallation.

---

### Post by kliljedahl on 2007-01-11
Tried that, thanks. Got this message:
 E: Internal Error, ordering was unable to handle the media swap
A package failed to install.  Trying to recover:

Nothing after that.

---

### Post by kj1h234lkj1234 on 2007-01-11
Do:

```
sudo aptitude remove gaim
```then

```
sudo aptitude install gaim
```and copy/paste the output from whichever command gives you the error.

---

### Post by kliljedahl on 2007-01-11
Thank you very much. I tried "uninstall" on my own, I obviously have a lot to learn. I'll try in the morning.  It's late now, I must sleep.

---

### Post by kliljedahl on 2007-01-12
It worked the second time, it's re-installed. I'm still getting that message from both MSN & Yahoo. Jt will not allow me to log in.

---

### Post by kj1h234lkj1234 on 2007-01-12
If you want to try something a little more desperate... :D

Your gaim config files/logs/etc. are stored in /home/username/.gaim, so do the following:

```
cp -R ~/.gaim ~/.gaim-backup
```This makes a backup copy of your settings/logs.

Now, completely blow away gaim and reinstall:

```
sudo aptitude purge gaim
sudo aptitude install gaim
```

See if the problem still persists. Purging removes all the configuration files and anything installed by gaim, so when you install it again, it's as if it was installed for the first time.

If the problem STILL persists... I have no idea what to tell you. Complain to the gaim developers. ;)

---

### Post by kliljedahl on 2007-01-12
That didn't work either. I may just re-install ubuntu and see if that works.

---

