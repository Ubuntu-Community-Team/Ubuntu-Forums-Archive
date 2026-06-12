---
title: "[SOLVED] Enabling access to &amp;quot;mount&amp;quot; command without sudo"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by naporeon on 2007-12-10
Let me start by saying that I am more or less a Linux noob (I've been using Unix or Linux environments at work for about 2 1/2 years, but this is my first foray at home), and after test driving several different Linux flavors, I settled on Ubuntu, which is now the only OS installed on my laptop, and will soon be at least a dual-boot option on all of the machines in my home network.

In one of the previous Linux flavors I tried out (which obviously used root, rather than sudo), I wrote a small folder of shell scripts, basically for the purpose of unmounting a filesystem from a specific directory, mounting a new filesystem (namely, a CD image) to that directory, and executing a specific sequence of commands.  I used these scripts so that I could do things like, say, create a link to instantly do everything I needed to run a game in DOSBox.

Since switching to Ubuntu, however, I have been hobbled by the fact that only root can mount images.  My answer at this point is to add "sudo" to a few of the lines in the script, and simply enter my password when the script starts.  Ideally, however, I would just be able to mount without any of this sudo hoohaa.

What I want is to enable full access to the "mount" command for my primary user account at the very least.  Or, more specifically, I want a method of mounting CD images to a single folder (namely, /mnt/virtual), that I have created solely for the purpose of mounting CD images.  I don't care if accomplishing this means enabling filesystem mounting privileges for ALL users...I just want to be able to do it without sudo.  The problem is that I can't find anything on accomplishing this.  I've tried looking at fstab and mountconfig tutorials, but I haven't gotten anywhere.

Ideas?  I'd be more than happy to provide any pertinent details I may have left out of this message.

---

### Post by Pumalite on 2007-12-10
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by The Cog on 2007-12-10
There is a file called /etc/sudoers that controls what commands users are allowed to use. I think you can edit that such that you can **sudo mount** and **sudo umount** without requiring a password.

Another option is to add all the cd images to /etc/fstab, using the options **user,noauto**  (along with any others that you need). These options are:
user - users are allowed to mount/umount this, not just root
noauto - don't mount this one at startup
but of course this solution is only viable with a limited and predefined set of images.

---

### Post by naporeon on 2007-12-11
> **The Cog said:**
> There is a file called /etc/sudoers that controls what commands users are allowed to use. I think you can edit that such that you can **sudo mount** and **sudo umount** without requiring a password.
Thank you!  This is precisely what I was asking.

Once you pointed me toward sudoers, solving my problem was frustratingly simple.  I spent about five minutes looking up 'visudo', and then spent all of two minutes adding permissions for my personal account to '/bin/mount' and 'bin/umount'.

Thanks again for the clear, quick answer!

---

