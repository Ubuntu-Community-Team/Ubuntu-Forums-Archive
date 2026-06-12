---
title: "How do i change my name?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by MicroChris on 2006-11-19
How can I change my name in terminal? I goofed and it was named chris-desktop

```
chris@chris-desktop:~$
```

---

### Post by K.Mandla on 2006-11-19
I believe you can change that by editing your hostname file. Enter *sudo nano -w /etc/hostname* to rename it. I think it will take effect on reboot.

Someone correct me if I'm wrong here.

---

### Post by taurus on 2006-11-19
You have to edit both /etc/hosts & /etc/hostname.  They both need to have the same name or the network stuff may not work.

---

### Post by K.Mandla on 2006-11-19
Right on. Thanks.

---

### Post by BatteryCell on 2006-11-19
Yea and I dont think that you even have to reboot
```

/etc/init.d/hostname.sh stop
/etc/init.d/hostname.sh start

```
I think that works just the same.

---

### Post by CatKiller on 2006-11-19
It's not just network stuff. **sudo** doesn't work either.

System -> Administration -> Networking -> General -> Hostname
is another way to do it.

---

### Post by ianthepetrock on 2006-11-25
I just edited /etc/hosts and now it wont let me edit etc/hostnames.

It says "Unable to lookup ian-desktop via gethostbyname()"
ian-desktop is the current hostname that im trying to change. It won't let me go back to edit /etc/hosts either. Won't let me use sudo, any thing i can do or do i have to reinstall ?

---

### Post by taurus on 2006-11-25
Boot into recovery mode from GRUB menu and edit your /etc/hostname!

```
nano -w /etc/hostname
```

---

### Post by nekr0z on 2006-11-25
You still have a live-CD, don't you? Boot from your live CD, mount a hard drive, edit the required files and reboot. Or, if you've got a Knoppix CD, use it to boot from, then you have your hard drive mounted automatically.

---

### Post by CatKiller on 2006-11-25
Given that people don't read threads like this **before** they do this, I doubt that this will do much good, but ```
gksudo gedit /etc/hostname /etc/hosts
``` or ```
kdesu kate /etc/hostname /etc/hosts
``` should open both files for editing simultaneously.

```
sudo -s
``` or ```
sudo -i
``` (before you edit either, obviously) should make you root for long enough to edit both of them in nano if you only have command line.

---

### Post by ianthepetrock on 2006-11-25
*ahem* i did it read BEFORE i tried it, but i didn't expect the changes to take affect immediately.

---

### Post by CatKiller on 2006-11-25
> **ianthepetrock said:**
> *ahem* i did it read BEFORE i tried it, but i didn't expect the changes to take affect immediately.

Oh, it wasn't a dig at you or anything.

It's just that this problem's been mentioned a reasonable amount on the forum, and people don't necessarily accept that changing one means that you can't change the other, and then you're buggered. So we could put it in the wiki, or in the "Important Read This" sticky or whatever, and people still wouldn't read them.

It's not just this problem - there are many things that are extremely well-known to the hive mind of the Ubuntu forum, that still come up over and over. I was just putting the solution out there (again) in case it helped someone in the future, as small a chance as that may be.

It's the nature of the beast.

---

