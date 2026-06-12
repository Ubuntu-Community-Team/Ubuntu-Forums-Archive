---
title: "Can't disable root"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Perogies on 2006-08-02
When I try the command "sudo passwd -l root" it just tells me "Password changed", and still lists me as root. It feels like the commands never work out for me.

---

### Post by stormblue on 2006-08-02
What exactly are you trying to do?

---

### Post by RavenOfOdin on 2006-08-02
It sounds like you performed an expert install.

Maybe a simple one would be more to your liking.  That'll take care of disabling root automatically.

---

### Post by Perogies on 2006-08-02
I'm not even sure anymore, to be honest.

---

### Post by Perogies on 2006-08-02
> **RavenOfOdin said:**
> It sounds like you performed an expert install.

Maybe a simple one would be more to your liking.  That'll take care of disabling root automatically.

I didn't even know there was an expert install option.  All I did was pop in the live cd, clicked install, and off I went.

---

### Post by stormblue on 2006-08-02
Maybe we can help you if you can explain exactly what the problem is and what you're doing to try to fix it.

---

### Post by Perogies on 2006-08-02
In the terminal I entered "sudo passwd root", entered a password twice.  Now I wanted to disable it, "sudo passwd -l root" (as found [here]("https://help.ubuntu.com/community/RootSudo#head-b06dbcd33c40480dcfd3aada1ca67bbd77f80594"), and it tells me "Password changed."  That's it.  As far as I can tell this command did not disable it.

I'm just trying various things, playing with Ubuntu... trial and error I guess.  Something I wanted to learn about was using root (just how to enable and disable it).

---

### Post by stormblue on 2006-08-02
try running that command then doing a "su name" and replace your username used during normal use.

You may want to reread this:

"n Linux (and Unix in general), there is a superuser named root. The Windows analog of root is Administrator. The superuser can do anything and everything, and thus doing daily work as the superuser can be dangerous. You could type a command incorrectly and crash the system. Ideally, you run as a user that has only the privileges needed for the task at hand. In some cases, this is necessarily root, but most of the time it is a regular user.

By default, the root account is locked in Ubuntu. This means you cannot login as root or use su. Instead, the installer will setup sudo to allow the user that is created during install to run all administrative commands.

This means that in the terminal you can use sudo for commands that require root privileges. All programs in the menu will use a graphical sudo to prompt for a password. When sudo asks for a password, it needs YOUR USER Password; this means that a root password is not needed."

Root isn't really necessary in ubuntu.

---

