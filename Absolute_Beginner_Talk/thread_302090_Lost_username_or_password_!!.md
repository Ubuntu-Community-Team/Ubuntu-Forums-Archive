---
title: "Lost username or password !!"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by beachen on 2006-11-18
Hi,

I am a Linux beginner, and last night I tried to install ubunto 6.06. Well, I run into some problems. After installation I am promped to type in my username and password. For some reason I got this message "Incorrect username or password", however I am pretty sure I am typing the right password/username.

How to I go from here. It seems like I have forgotten my password. Can I create a new one, andhow do I do it?

Thanks, 

- A

---

### Post by frank05 on 2006-11-18
reboot into "rescue mode" by selecting it in the bootloader. it will let you login as root with no password, or it may just give you a root promp. either way just type the follwing:

```

passwd [username]

```

obviously replace [username[ with your username

if you don't know your user name, you can look for it by typing

```

cat /etc/passwd | grep [some-or-all-of-your-real-name]

```

---

### Post by beachen on 2006-11-18
Thanks alot :) 

Very simple, but not that secure, though. Anyways, I can't wait to explore Linux now.

Thanks again
- A

---

### Post by localuser on 2006-11-18
> **beachen said:**
> Anyways, I can't wait to explore Linux now.

I'm not sure if this is what you meant, but you probably don't want to do any exploring while in recovery mode.  Since you are root while in that mode, it may be a bit dangerous.

---

### Post by mcduck on 2006-11-18
> **beachen said:**
> Thanks alot :) 

Very simple, but not that secure, though. Anyways, I can't wait to explore Linux now.

Thanks again
- A

It's just as secure as any computer can be if somebody gets physical access to the machine..

But if you feel you need to make this harder, it's possible to set a password for Grub. :)

---

### Post by samden on 2006-12-04
I have got exactly the same problem, but on an iMac G3 (ubuntu 6.06.1). I can't figure out how to follow the instructions given here on this computer at all, there is nowhere during the boot process that appears to correspond to what you describe here. If you have any suggestions, please follow this link to my thread in the PPC forum and tell me your thoughts. Thankyou.

My thread: [http://www.ubuntuforums.org/showthread.php?t=312398](http://www.ubuntuforums.org/showthread.php?t=312398)

---

