---
title: "Public PC"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by flatblack on 2007-07-02
Hello!

I'd like to use ubuntu on some of my older PCs.  The purpose of these PCs would be to create a "public" pc.  The goal is to have a PC that users can abuse, and via some mechanism, we be able to reset the PC back to a "clean" state.

That make any sense?  Is that possible?

Thanks!

---

### Post by gigaferz on 2007-07-02
i think to get back to the original settings  you can use the alternate cd install, so after a month  of  use, you could  reinstall again t
he same could be used in windows via system restore or if is too messed up cause of the malware you can do it  with bart pe (if they did not provide an xp cd) or the original cd,

---

### Post by cogadh on 2007-07-02
If you don't plan on users being able to install software or make any system-wide changes, you could create an account with limited access, then just delete that account when it gets too cluttered.

---

### Post by Rocket2DMn on 2007-07-02
Giving an account limited access should prevent anybody from seriously messing things up.
You can prevent users from using sudo by editing the file /etc/sudoers , therefore preventing them from acting as a superuser in order to screw stuff up.

---

### Post by st33med on 2007-07-02
I heard something like this. Any files that weren't originally installed on it are deleted, otherwise known as a "Deep Freeze".

Also, by 'old' computer... How old and what make/model?

---

### Post by cogadh on 2007-07-02
Here's a radical suggestion: Just run the live CD, that way every time you reboot, it's a brand new system. Users can do anything they want to the system, including installing software, and it won't matter. You just reboot and its all gone.

---

### Post by loserboy on 2007-07-02
I just got a dellbuntu and they just put an image on a seperate partition, and it works just like a restore, I don't know the details but theres an option in GRUB that lets you boot that partition and it automatically finishes the restore.... matter of fact i'm about to test it out here in the next few days.  I'm pretty sure theres a way to lock grub so no one could accidentally mess with it

---

### Post by gigaferz on 2007-07-03
yeah, that is a good idea!!

Can i ask the ubuntu masters here how would you set up something like that, i mean, Ive destroyed windows several times, and so far ive done the same with ubuntu ,kubuntu etc....but is more convenient to have it on a hard drive.

  I know i am asking a lot here but if that process was kinda automatic would be nice..

It could be included for one of the next releases, and done during the installation.

---

### Post by ugm6hr on 2007-07-03
Couldn't you do your install, set up all the hardware, and then use partimage to create a complete "clean" backup.

I've never had to use partimage, but I gather it's pretty easy, and allows images to be stored on removable media or on the HD itself.

That would work, wouldn't it?

---

