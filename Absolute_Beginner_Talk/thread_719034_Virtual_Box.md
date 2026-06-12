---
title: "Virtual Box"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-08
I've installed XP. Works perfect!

But...
I want seemless mode to work but its blanked off.

Why?
And how can I get it to work?

---

### Post by gpilkay on 2008-03-08
Is this the open-source edition from the repos, or the enterprise (but still freeware) release?  Currently I think the seamless windows is limited to Windows guests (which you've got) and the enterprise release (which I'm not sure of).

You may also want to try the VirtualBox forums, though they are not quite as informative as those here.

---

### Post by PeterJS on 2008-03-08
I'm setting this up right now, so I can't confirm this is the case, but you probably need to install the guest tools first which can be installed from Devices > Install Guest Additions on the VM window itself.

---

### Post by Tom--d on 2008-03-08
Thank you :)
I have no seemless mode. 

But one more thing. 

How do I get shared folders to work?
Its harder than I fought.

---

### Post by Tom--d on 2008-03-08
Ah done it! :D

This is what you need to do:

> 

I have set this up this week from a clean install and haven't put in Samba or anything.

I just did these steps.

#install xp in virtualbox
#install the virtualbox additions
#made a folder in my home folder on ubuntu called virtualboxshare
#without xp running, went to settings in the xp machine, shared folders and navigated to this folder
#boot xp, then click start, run and entered the command:

```


net use x: \\vboxsvr\virtualboxshare

```
#Give it a moment and then in My Computer in XP you should have a shared folder.

Good luck

---

### Post by ODF on 2008-03-08
For seemless mode you need to keep a windows application on top at any time or it will get ugly and you'll need to ctrl+l to clearly see what you're doing.

some people run a clock software under the start bar.

---

