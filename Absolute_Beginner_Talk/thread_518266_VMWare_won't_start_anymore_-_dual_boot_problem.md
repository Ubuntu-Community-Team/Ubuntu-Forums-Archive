---
title: "VMWare won't start anymore - dual boot problem?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Ansible on 2007-08-05
I got VMWare installed, and I've been using it to boot my windows partition while I'm running ubuntu.  Its been working fine.

I think I have a problem now though - I was playing around with seamlessrdp and started up the windows vmware session.  Then I shut down the vmware server console, leaving the session running.  Then when I opened vmware console again, it wouldn't let me log in, giving me an authorization error (I don't remember the exact message unfortunately).  Eventually I gave up and shut down ubuntu.  

At some later point, I booted directly into windows.  Now, when I boot into ubuntu and try to start up the VMWare Server console, I get a minimized window at the bottom of the desktop that says  'Starting VMWare...'.  After about 30 seconds the minimized window vanishes, and thats it.  No VMWare console comes up, and no error message, unfortunately.

So I'm thinking what may have happened was that when I shut down ubuntu with VMWare running, it saved a snapshot of the running XP session.  Then I booted into XP directly and did some work, which got the XP partition out of sync with the saved VMWare session.  When I try to start the VMWare console now, it tries to restore the old XP session, but that doesn't work.  

All that is leading up to my question, which is:  is there some way to blow away the old VMWare sessions so that VMWare will start up?  Or maybe this is a symptom of another problem that someone recognizes?  

Also, assuming I get it running again, how do I attach to a running session with VMWare console without the authorization error?  I tried running it with sudo but no dice.

---

### Post by xopher_mc on 2007-08-05
I had a similar problem and "fixed it" by deleting the .vmware directory in my home folder.

---

### Post by Ansible on 2007-08-05
That worked for me too, thx.

---

