---
title: "Typing Issues on MacBook pro"
date: 2007-06-24
forum: Apple Intel Users
---

### Post by xelapond on 2007-06-24
OK, This one really annoys me.  I type a lot on my laptop, and this have been fine in Mac OS X.  In my recent switch to Ubuntu linux, which I like much more then mac OS X.  99% of it works, but the biggest annoyance to me is the typing issues.  When i am typing, my palms will occasionally touch the trackpad.  in the mac this is no problem, the mac disables the trackpad while you are typing.  but in linux, when my palms touch it the cursor jumps and all of a sudden I am typing somewhere else.  This happened on my PC laptop, and was one of the many things that made me switch to getting a mac.  Does anybody know how to fix this issue?  Like just make the cursor hidden and inactive when you type like the mac does?

Thanks,

Alex

---

### Post by ivesjd on 2007-06-24
There is a thread in here somewhere, I think its disable touch while typing or something like that. And there is a fix in there.

---

### Post by Gen2ly on 2007-06-24
You probably gotta get gsynaptics it sounds like.  it can disable certain synaptic actions.

---

### Post by ivesjd on 2007-06-24
Here's what to do: ```
sudo nano /etc/rc.local
```
and put this in before the final exit ```
# Disable touchpad for 1 seconds after last key press 
# to prevent accidental touchpad activation while typing. 
syndaemon -d -k -K -i 1
```
Then reboot.
rc.local is a bootup script and this way it will run when you boot. You can change the 1 in the code for longer, but I don't think you can do anything less then 1. Hope that helps.

---

