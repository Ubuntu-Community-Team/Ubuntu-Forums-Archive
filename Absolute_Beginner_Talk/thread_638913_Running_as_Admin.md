---
title: "Running as Admin"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2007-12-12
Maybe this is a really stupid question that I should already know since I've been running Ubuntu for a while, but just for my peace of mind...

Since I setup Ubuntu I have just always used the profile that I installed with.  (My wife has a profile now as well).  Should I create another account for me?  Or rather create an administrative account since I have settings and programs setup how I like them in my profile?  (Then degrade the original account to be more consistent with a normal user)

I've always just assumed that it was setup to where I wasn't running as root since I have to sudo or enter my password for synaptic and such.

---

### Post by jken146 on 2007-12-12
You are correct in thinking you're not running as root all the time.  You only act as root when you run a command with sudo, su, gksu or gksudo.

Using an admin account all the time with sudo should not give you any security problems.  If you want you can reduce the timeout for sudo (the time between entering your password and needing to re-enter it).  There are some instructions and more here: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

