---
title: "ubuntu 7.10 fails to boot"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by sam198923 on 2008-04-04
I installed Ubuntu a few days ago, and it worked for about five hours before it stopped. My computer wont boot up from BIOS. BIOS reads


[18.886160]  PCI: BIOS BUG #81[49435000]. 
Loading, Please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/4f83678b-e6b4-409a-a1c2-oca3a42de648) =sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/4f83678b-e6b4-409a-a1c2-oca3a42de648
kinit: No normal image, doing normal boot...

Ubuntu 7.10 Sam tty1
sam login:
Password:


After i type in my login, it asks for my password. It wont let me type in my password. Is my login and my password two different things? i cant remember choosing anything for login besides my name.
Is there a way i can reinstall ubuntu either from the root screen or from Bios?
I need my computer to work, please help.

---

### Post by joshrobinson on 2008-04-04
restart your computer, when it says hit whatever button to enter grub menu, hit it, then click recovery mode

when you get to the command prompt put in this code

```


grep x:1000 /etc/passwd | cut -d: -f1

```
this will print out your username

now use this command
```


passwd username

```
where it says username, put the username that the first command put out, and this will let you set a new password

```
reboot now
```

this will reboot you, now login at the tty1 screen with your user and password(you wont see your password as you enter it, no ***'s or letters but its entering), then try typing
```
startx
```

---

### Post by fela on 2008-04-04
> **joshrobinson said:**
> now login at the tty1 screen with your user and password(you wont see your password as you enter it, no ***'s or letters but its entering), then try typing
```
startx
```

yes, that can be pretty misleading for new users, but it's actually a feature (to stop people from getting your password by looking over your shoulder)

and PS. the last command. i thought it went (as root) `/etc/init.d/gdm start` ?

---

### Post by sam198923 on 2008-04-04
thanks joshrobinson, it worked. Is there anyway of fixing the bug that you know of. I think it is making my multimedia applications not work. I cant get youtube to work or any songs on my computer to work.

---

