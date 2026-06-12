---
title: "Zorin: 2 Errors"
date: 2013-01-12
forum: Any Other OS
---

### Post by ProxyCyber on 2013-01-12
Firstly, when I try to update it says  W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)    W: Some index files failed to download. They have been ignored, or old ones used instead. E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.   ---   Second, from the Software Center I installed Matlab which basically just helps installments. But it's annoying and I want to remove it. I click remove in the Software Center but it doesn't do anything actually. Everytime I try from Synaptic, when I click to open it says: "Unable to get exclusive lock This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first." First how do I fix that? Second, what's the command line to remove Matlab? Thanks a lot!  Please don't just move this topic, moving topics doesn't help unless you post the new link. I just need help right now, so I'd appreciate a response without seeing "topic moved." why not just respond to users?

---

### Post by howefield on 2013-01-12
As you knew it would be, thread moved to the "Other OS/Distro Talk" forum.

Link to Zorin support forum is : [http://www.zoringroup.com/forum/viewforum.php?f=3&sid=a022f69311a014a8e105ef0a393592fa](http://www.zoringroup.com/forum/viewforum.php?f=3&sid=a022f69311a014a8e105ef0a393592fa)

---

### Post by 2F4U on 2013-01-13
> W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)     W: Some index files failed to download. They have been ignored, or  old ones used instead. E: dpkg was interrupted, you must manually run  'sudo dpkg --configure -a' to correct the problem

Did you do as suggested and run the command as suggested in the message?

> "Unable to get exclusive lock This usually means that another package  management application (like apt-get or aptitude) is already running.  Please close that application first."

Most likely, another update manager is running at the same time, for example the automatic software update. You can find out what is currently running by looking at the processes, for example in Task Manager.

---

