---
title: "Did something dumb. (I think)"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by triplenine on 2007-02-01
Ok. in the process of a problematic install of 6.10 on a Dell e1405 (this is important:D ) I ended up using the alt install CD and finalized my install, after having to reconfgure the X configuration files - but that is another story.

I was unable to log into the GUI and cannot remember if I added an administrative user/password during the install - had I done so I would have used a password that I always use for my Linux system. I just don't remember being prompted to do so. Regardless, I went in and added a user so I can log on to Ubuntu, but the user has no administrative functions and I need to get access to networking and other functions so I can fight with my network cards (e1405 remember?)

I guess that my question is: Should I reinstall or is there a way to get my newly added user, which will be my default, root/administrative access?

Thanks,
999

---

### Post by bodhi.zazen on 2007-02-01
> **triplenine said:**
> Ok. in the process of a problematic install of 6.10 on a Dell e1405 (this is important:D ) I ended up using the alt install CD and finalized my install, after having to reconfgure the X configuration files - but that is another story.

I was unable to log into the GUI and cannot remember if I added an administrative user/password during the install - had I done so I would have used a password that I always use for my Linux system. I just don't remember being prompted to do so. Regardless, I went in and added a user so I can log on to Ubuntu, but the user has no administrative functions and I need to get access to networking and other functions so I can fight with my network cards (e1405 remember?)

I guess that my question is: Should I reinstall or is there a way to get my newly added user, which will be my default, root/administrative access?

Thanks,
999

You can boot to recovery mode and add your new user to the admin group.

Then reboot and you should be good to go ...

---

### Post by ComplexNumber on 2007-02-01
> **triplenine said:**
> Ok. in the process of a problematic install of 6.10 on a Dell e1405 (this is important:D ) I ended up using the alt install CD and finalized my install, after having to reconfgure the X configuration files - but that is another story.

I was unable to log into the GUI and cannot remember if I added an administrative user/password during the install - had I done so I would have used a password that I always use for my Linux system. I just don't remember being prompted to do so. Regardless, I went in and added a user so I can log on to Ubuntu, but the user has no administrative functions and I need to get access to networking and other functions so I can fight with my network cards (e1405 remember?)

I guess that my question is: Should I reinstall or is there a way to get my newly added user, which will be my default, root/administrative access?

Thanks,
999
menu -> system -> administration -> users and groups. add that user to the admin group.

---

### Post by steve.horsley on 2007-02-01
> **bodhi.zazen said:**
> You can boot to recovery mode and add your new user to the admin group.


To achieve this, boot into recovery mode and use the command:
**adduser steve admin**
but using your user name not mine, of course.

---

### Post by triplenine on 2007-02-01
I will give it a try...rebooting in 3...2...1...

---

### Post by triplenine on 2007-02-01
Thanks...
I ended up using usermod -g admin USRNAME
that did it.

---

### Post by ComplexNumber on 2007-02-01
> **triplenine said:**
> Thanks...
I ended up using usermod -g admin USRNAME
that did it.
oh right. from your first post, i thought that you meant that you still have 1 user that can use sudo.

---

