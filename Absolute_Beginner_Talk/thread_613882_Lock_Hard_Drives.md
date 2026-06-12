---
title: "Lock Hard Drives?"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by GeorgiaBoot on 2007-11-15
Okay so I install Ubuntu a couple days ago and just yesterday installed 7.10. When I installed Ubuntu I installed it on my external hard drive and did not touch my internal hard drives because they have Windows XP on them. When I did the install I unplugged the internal HD's because I did not want it to touch them. Now that everything is up and running I want to make sure Ubuntu does not touch those internal hard drives. I don't want it to right anything to them, not even look in them. So is there any way to lock the Hard drive so Ubuntu won't touch them?

Thanks

---

### Post by Inxsible on 2007-11-15
> **GeorgiaBoot said:**
> Okay so I install Ubuntu a couple days ago and just yesterday installed 7.10. When I installed Ubuntu I installed it on my external hard drive and did not touch my internal hard drives because they have Windows XP on them. When I did the install I unplugged the internal HD's because I did not want it to touch them. Now that everything is up and running I want to make sure Ubuntu does not touch those internal hard drives. I don't want it to right anything to them, not even look in them. So is there any way to lock the Hard drive so Ubuntu won't touch them?

ThanksIf you do not mount the hard drives then you wont even see them, forget about writing to them.

and given that you installed Ubuntu after unplugging the internal HDD's ubuntu installer would not have put any entries in the fstab. So you should be safe.

---

### Post by GeorgiaBoot on 2007-11-15
What do you mean don't mount them? After the installation process I plugged back both hard drives in the system. Ubuntu sees them I just don't want to accidentally click on them somehow and mess them up. 

Thanks

---

### Post by overdrank on 2007-11-15
> **GeorgiaBoot said:**
> What do you mean don't mount them? After the installation process I plugged back both hard drives in the system. Ubuntu sees them I just don't want to accidentally click on them somehow and mess them up. 

Thanks

HI and some good info here
[http://ubuntuforums.org/showthread.php?t=609485&highlight=edit+fstab](http://ubuntuforums.org/showthread.php?t=609485&highlight=edit+fstab)

---

### Post by Inxsible on 2007-11-15
Use the understanding fstab link in my signature. It gives a lot of info about how to set up drives etc.

---

