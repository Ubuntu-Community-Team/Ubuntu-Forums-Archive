---
title: "Debian appeared suddenly"
date: 2012-12-19
forum: Any Other OS
---

### Post by Carllacan on 2012-12-19
Hi!

I installed Debian a few weeks ago, along with Ubuntu OO, but I couldn't make it appear on the Ubuntu GRUB. Since I had no time to search for a solution, I left it as it was until I could try again.

But, when I started my computer today, I got the Debian GRUB, showing me Ubuntu as well! Was it due to any of the updates I installed yestarday before shutting down?

Anyway, I can't start Debian, as I apparently forgot which username I gave to the first user. I'm sure about the password, though, and I've entered the Debian partition and looked up /etc/passwd, but none of the usernames I recognized on the list was right. What I'm doing wrong? Is there any way to reset Debian without reinstalling from scratch?

PD: Side question; why are there so many users? Shouldn't it be just two, the root and the first user?

Thank you!

---

### Post by zombifier25 on 2012-12-19
> **Carllacan said:**
> Hi!

I installed Debian a few weeks ago, along with Ubuntu OO, but I couldn't make it appear on the Ubuntu GRUB. Since I had no time to search for a solution, I left it as it was until I could try again.

But, when I started my computer today, I got the Debian GRUB, showing me Ubuntu as well! Was it due to any of the updates I installed yestarday before shutting down?

Sounds like it. Some Ubuntu upgrades must have ran "update-grub" and Debian shown up as a result.
> **Carllacan said:**
> 
Anyway, I can't start Debian, as I apparently forgot which username I gave to the first user. I'm sure about the password, though, and I've entered the Debian partition and looked up /etc/passwd, but none of the usernames I recognized on the list was right. What I'm doing wrong? Is there any way to reset Debian without reinstalling from scratch?
/etc/passwd won't help you, since it stores passwords in hashed forms. I found [this tutorial](http://www.debianhelp.co.uk/root.htm) for resetting your password in Debian, haven't tried them though.
> **Carllacan said:**
> 
PD: Side question; why are there so many users? Shouldn't it be just two, the root and the first user?

Thank you!
In Ubuntu, there are some hidden extra users used to better manage system processes. I bet it's the same in Debian.

---

### Post by Carllacan on 2012-12-19
> **zombifier25 said:**
> 
/etc/passwd won't help you, since it stores passwords in hashed forms. 

I actually know my password, I always use the same one for the root user. The problem is with the username. I can recognize it on the passwd list (it's simply my first name) but it won't work on the login.

Thanks for that guide, anyway, I'll take a look at it.

---

### Post by snowpine on 2012-12-19
The root user in Debian is named 'root'. :)

But you can't log into the GUI as root, so try getting to a terminal by pressing Ctrl+Alt+F1, then log in to root there. Once you're logged into a terminal as root, you can reset your user password with:

```
passwd carllacan
```

---

### Post by claudecat on 2012-12-19
If the username is all that has been forgotten, simply check the folder names under /home. There should be separate folders there for all configured users.

---

### Post by Carllacan on 2012-12-19
Ok, I think it is a biggest problem than I had thought. I've already tried shifting to TTY-1 and trying root, but it didn't work. And now I checked the home folder and it is empty.

Does that mean that I have an incomplete installation? If I start the process again, will it repeat everything from scratch?


Thanks for your answers.

---

### Post by perce on 2012-12-19
It is probably faster to reinstall Debian from scratch, but if you prefer to fix the current installation, you can actually become root on your Debian system from inside Ubuntu, provided that Debian's root directory is mounted. I don't remember all the details from the top of my head, but you should look at chroot: [http://www.linux.org/article/view/chroot-access-another-linux-from-your-current-linux-]("http://www.linux.org/article/view/chroot-access-another-linux-from-your-current-linux-")

---

### Post by kiyop on 2012-12-20
> **Carllacan said:**
> I've already tried shifting to TTY-1 and trying root, but it didn't work. And now I checked the home folder and it is empty.
Did you prepare /home partition separately from / partition?
I wonder if your problematic debian failed to mount /home partition.

Anyway, I suggest you reinstalling debian correctly.
> **Carllacan said:**
> If I start the process again, will it repeat everything from scratch?Yes it will, if you correctly manipulate partitions.

---

