---
title: "Obnoxious hard drive clicking"
date: 2011-07-21
forum: Any Other OS
---

### Post by el_koraco on 2011-07-21
Crossposting with Fedora forums, since i'm getting no replies there. 

My HD is making clicking noises on F15. I'm able to reset it using hdparm with 


```
#hdparm -B254 /dev/sda

```

I've added it to /etc/rc.local, so it starts at boot, and I'm not having the issue. However, when the computer resumes from suspend, the settings are reversed, so I have to enter the command each time to stop the clicking. Is there a way to remedy that, so that i don't have to enter the command on each resume?

Also, I'm dual booting with Maverick, and Maverick's grub is handling the boot. Maybe that's the reason for the clicking in the first place?

---

### Post by el_koraco on 2011-07-22
bump?

---

### Post by jeffathehutt on 2011-07-22
Does Fedora use pm-utils?  If so, see [this link]("https://wiki.archlinux.org/index.php/Pm-utils#Creating_your_own_hooks") for some ideas that might work. :)

---

### Post by el_koraco on 2011-07-23
Hey, that's a good idea! Edit: A kind man helped me out at the Fedora forums, so I'm marking this as solved.

---

