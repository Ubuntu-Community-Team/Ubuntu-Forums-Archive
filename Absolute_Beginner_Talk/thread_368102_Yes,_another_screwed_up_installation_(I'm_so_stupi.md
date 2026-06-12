---
title: "Yes, another screwed up installation (I'm so stupid)"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by ZhaoMein on 2007-02-22
Alright. So, my Ubuntu installation was going along fine. I had the partitions correct, the bootup sequence just right, and I was all ready to get to the final parts of my installation.

So when I go to log on to Ubuntu 6.10 to finish the installation...I find out that I forgot the username/password that I used.

Is there a way to bypass this and finish the installation? Or do I have to uninstall/reinstall Ubuntu. Most importantly, HOW DO I DO IT?:confused:

---

### Post by Bachstelze on 2007-02-22
> **ZhaoMein said:**
> So when I go to log on to Ubuntu 6.10 to finish the installation...I find out that I forgot the username/password that I used.

There's something I don't get here. When you login, the installation is already finished. Anyway, to recover your username, boot in recovery mode and when you're at the command prompt, do

```
cat /etc/passwd | grep 1000
```

that will tel you your username, then you can set a new password for it with

```
passwd username
```

---

### Post by geezerone on 2007-02-22
Would that not be a security risk as anyone could change a password in recovery mode?

---

### Post by netkid91 on 2007-02-22
You need physical access to the machine to do so however, and in recovery (AKA single-user) mode most if not all network daemons (SSH, etc...) are disabled, meaning you aren't exposed while in it.  Nothing to really worry about, and if you are, you are obviously knowegable enough to figure out how to edit your grub.conf, delete the recovery kernels from the list and disable the GRUB command shell without a password.  Most people would never have to worry, I personally leave them there for these very reasons.

---

### Post by Bachstelze on 2007-02-22
Yes, recovery mode needs physical access to the machine. And someone with physical access can do whatever he wants on a system, single-user mode or not.

---

### Post by geezerone on 2007-02-22
I can see that by using a "live cd" one could edit the menu.lst file anyhow to access recovery mode so really the BIOS password is the only real security and padlocking your case :)

---

