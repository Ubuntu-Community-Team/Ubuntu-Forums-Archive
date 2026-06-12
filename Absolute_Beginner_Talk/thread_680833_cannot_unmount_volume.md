---
title: "cannot unmount volume"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-01-28
Hi All,

When I try to eject my CD from the CD drive, I am encountering the following error message:

"Cannot unmount volume
An application is preventing the volume 'Backup-F,D' from being unmounted."

also when I try the following in terminal, it shows like this:

srikrishnan@srikrishnan-desktop:~$ sudo unmount /media/cdrom0
[sudo] password for srikrishnan:
sudo: unmount: command not found

What can I do to solve this problem?

Thanks in Advance,
Srikrishnan

---

### Post by bumanie on 2008-01-28
I'm not very up with mounting/unmounting etc., but I beleive the command in terminal is umount not **un**mount. If the rest of your command is correct, umount should work.

---

### Post by srikrishnan on 2008-02-02
Hi,

Thanks for your response I will try and let us inform

Regards,
Srikrishnan

---

### Post by jan quark on 2008-02-02
bumanie is right 

the command is** umount**

ubuntu has an in-build security to unmount devices only then when no data is being transmitted from or to them, perhaps you should just wait a sec,

I am guessing do not know how long you have waited...

---

### Post by mali2297 on 2008-02-02
You can try to find out which program that stands in the way. Type
```

ps waxf

```
to see which program that is being called below "mount /cdrom". Then kill it with
```

pkill name_of_program

```


> **jan quark said:**
> 
ubuntu has an in-build security to unmount devices only then when no data is being transmitted from or to them, perhaps you should just wait a sec,

I am guessing do not know how long you have waited...

Five days, it seems. :-)

---

### Post by Nythain on 2008-02-02
yeah, it sounds like you are either A. in the partition in terminal or a file browser/manager, or B. you could possibly be running an app on that partition???

---

### Post by srikrishnan on 2008-02-02
Hi All,

Thanks for all your replies,

Actually I have closed all my open applications, still I was not able to eject my CD. I was waited for that more than 10 mins at last I reboot my system.

Any how I have the opportunity to learn various commands from you all. I hope those are all very necessary and useful in future.

Thanks,
Srikrishnan

---

