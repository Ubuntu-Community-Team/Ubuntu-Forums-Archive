---
title: "Power Outage Killed Ubuntu!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-20
OK... Last night the power went out right as I was booting (what are the chances of that, eh?) and now, I can't boot into linux at all! Recovery mode doesn't work either... instead I am present with the computer doing lots of command line stuff and then.....

> In order to run fskdisk (or something to that matter, can't remember)... when finished or to terminate press CTRL-D


Here is the problem.... I never set a root password! So, I just press CTRL-D, and it boots to Ubuntu and it does this: 

> In order to run fskdisk (or something to that matter, can't remember)... when finished or to terminate press CTRL-D

                                                       .... Again

So, what can I do to get my linux back up....?


Please let me know shortly, 

-ts51

---

### Post by lazyart on 2007-06-20
I would boot with the LiveCD and see if your home folder is still readable.  If so, copy it off to a flash drive or something and reinstall.  You'll have to reinstall any packages but you'll have your files and settings.

And then buy a battery backup.

---

### Post by lamalex on 2007-06-20
boot into a live cd and run an fsck on your harddrive, probably it just needs checked but there is potentially physical damage. That's at least a start. There probably isn't a need to reinstall, you just need to run fsck from a livecd.

---

### Post by ts51 on 2007-06-20
OK. 

Is there a way to change the root password without booting?

---

### Post by lamalex on 2007-06-20
do you know how to chroot? you could boot into a livecd, chroot your current install, and then set root password.

---

### Post by ts51 on 2007-06-20
> **Iamalex said:**
> do you know how to chroot? you could boot into a livecd, chroot your current install, and then set root password.

I don't know how to chroot.... could you please explain it to me?

---

