---
title: "How do I boot into terminal with no X Windows."
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by chrispche on 2008-01-08
At the very last runlevel. Rebooting through recovery through root doesn't do it. I need to go further. I need a terminal just before GDM loads. Can this be done?

---

### Post by aktiwers on 2008-01-08
Can you press CTRL+ALT + F1 after it booted?

A liveCD will also be able to do it.

---

### Post by gate on 2008-01-08
Well, off the top of my head: 1. Why before GDM loads? after GDM loads you can hit CTRL-ALT-F1 to get a terminal, otherwise, you could disable GDM temporarily from the bootup scripts and start it when you have done what you need.
   

   To be honest, by the sound of your post you probably know most of that. You could insert a custom boot script in the runlevels right before GDM starts....

---

### Post by PeterJS on 2008-01-08
You could use update-rc.d to disable gdm and then reboot.
```

sudo update-rc.d gdm remove

```
And then to re-enable gdm
```

sudo update-rc.d gdm defaults 13 01

```

---

### Post by chrispche on 2008-01-08
OK why I'm doing this is because I have downloaded the Nvidia drivers for my card that require a terminal installation with out X Windows loaded. Now I have figured out how to stop GDM loading and going straight to terminal. Now the Nvidia drivers are asking me if libc is installed. What's that and how do I install it?

---

### Post by PeterJS on 2008-01-08
Libc is the fundamental library that C programs use to interact with the system. I can gaurentee you that you've got a copy, as if you didn't you wouldn't be here asking about it. Have you tried using the drivers in the repository?

---

### Post by aktiwers on 2008-01-09
I posted here how to install the Nvidia drivers
[http://ubuntuforums.org/showthread.php?t=657713](http://ubuntuforums.org/showthread.php?t=657713)

In post number 7.

If you are missing the libs, just install them:
```
sudo aptitude install libc6 libc6-dev
```
```
sudo aptitude install build-essential linux-headers-$(uname -r);
```

Then follow my post number 7 from that link and it should work.

---

