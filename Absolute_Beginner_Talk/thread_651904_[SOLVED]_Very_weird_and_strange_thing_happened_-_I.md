---
title: "[SOLVED] Very weird and strange thing happened - I cannot login"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-12-28
Ok it went like this.

I watched a HD trailer from a CD. It ran fine. After that movie finished; I tried to launch another. However, MPlayer complained about the vo device. I don't know why like I said. Then, the screen went black with green stripes; and finally I was redirected to a login screen which said 'Authentication failed', without me needing to enter anything.

I tried everything; but couldn't login. Then I did a force-shutdown. When I tried to power the pc back on; it shut itself down after 2 seconds. I tried to revive the pc several times however same scenario took place. I then left the comp for 15 mins or so and when I tried turning it back on; I saw that it ran fine this time. But it once again got to that login screen and read "Authentication failed" again.

I ran the pc in recovery mode and could run a startx without any problems. However it was root mode and also I was unable to connect to the internet. So I restarted to see the same authentication failed screen.

Not being sure what to do; I popped in the LiveCD and am writing from there (or trying to write, as I have Turkish laptop keyboard and am forced to use US layout. for some reason it won't accept the changes to the layout).

I am not completely clueless however, and have several ideas; as follows:
1. To try to recover with minimal loss, I will try to change the pass to something random and then back to the original password and will try to see if it will say "Authentication failed" again.

2. Second best idea is to plug in the wired connection and try to change from gdm to xdm (I am running Xubuntu, and I have no idea why gdm is installed by default), but since this involves a configuration change I am saving this for later.

3. And the worse idea is to delete my user and create a new one. I don't know if it will fix the "authentication failed" dialog, and it is generally a bad idea to delete my user since I have made a few configurations.

If you ask me, I will first try the 1st option (I don't know how to change the pass for a user but I can always google or search these forums), and if it doesn't work, I will try the 2nd, and if that doesn't work either I will go with the 3rd or even a format.

What do you suggest I do?

---

### Post by stijngysemans on 2007-12-28
Another option if things really go wrong: backup your home directory on an external drive and reinstall the system.

But maybe it is an hardware problem?

---

### Post by The Cog on 2007-12-28
It might be instructive to switch to a text console (Ctrl-Alt-F2) and try to log in there and then
> startx -- :1
I don't know where you go from there, but it may help to figure out where the problem lies.

---

### Post by eternicode on 2007-12-28
Hmm...try the shiny passwd command...

```
SYNOPSIS
       passwd [options] [LOGIN]

```

With this option?

```
-d, --delete
          Delete a user’s password (make it empty). This is a quick way to disable a password
          for an account. It will set the named account passwordless.
```

Or maybe this, though it doesn't look as promising.

```
-e, --expire
          Immediately expire an account’s password. This in effect can force a user to change
          his/her password at the user’s next login.
```

Good luck!

---

### Post by Majorix on 2007-12-28
OK I fixed it.

Apparently, there was no problem with my password. It was an issue with the gdm, like I had thought. I completely removed it (which also removed the xubuntu-desktop metapackage) and then reinstalled the metapackage. It forwarded me to the login screen - but this time without that authentication failed dialog!

I believe this is a bug with the gdm in Hardy. I also found another bug, which I talked about in my post. Actually I haven't told you guys about it in detail.. When you force shutdown your pc while it is not on AC power, it can't be turned back on. You have to plug it in and then you can switch it on again. Weird!

I should report these bugs probably, but I don't like the approach to things in launchpad. I am still using Ubuntu alpha, I don't know why. Yes I am weird too :lolflag:

Thanks a lot for the replies people!

---

