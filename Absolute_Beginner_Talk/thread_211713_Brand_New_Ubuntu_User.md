---
title: "Brand New Ubuntu User"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by runbmd on 2006-07-08
Hello, everyone.  I recently installed Ubuntu on my laptop...dual boot, dual boot with Windows XP.

Everything seems to be working well, but I have a couple of problems.  First of all, I have no sound.  I've tried a few of the solutions I've found in the forums, but to no avail.

Also, I have been unable to add new applications, or complete any updates.  When I try to do these tasks through the menus...on the first try, I get a prompt for a password.  After I enter my password, nothing happens.  

I've also tried through the terminal.  For instance, when I try to open synaptic, it says I must be logged in as the root user.  If I do a sudo, I get an error.

I know that these issues are kind of vague, but I'm hoping that maybe someone has had similar experiences and can point me in the right direction.  I will provide more detail if it will help.

So far, I really like Ubuntu!  I just hope I can get these things fixed!

Thanks to everyone in advance for your helpful answers!

---

### Post by aysiu on 2006-07-08
For Synaptic, there should already be a launcher. If not, you can create one with the command: ```
gksudo synaptic
```

---

### Post by runbmd on 2006-07-09
> **aysiu said:**
> For Synaptic, there should already be a launcher. If not, you can create one with the command: ```
gksudo synaptic
```


Thanks for the response.  When I do the gksudo synaptic, it asks for a password...I enter it...then nothing happens.  It just goes right back to "brian@ubuntu:~$"  No windows open...nothing.  Any other suggestions?

---

### Post by lamego on 2006-07-09
Check that everything is ok with your repositores, from the terminal:
```
sudo apt-get update && sudo apt-get upgrade
```
And check for any error messages.

---

