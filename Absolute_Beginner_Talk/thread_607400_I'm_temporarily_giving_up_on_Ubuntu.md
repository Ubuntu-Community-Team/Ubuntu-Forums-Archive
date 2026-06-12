---
title: "I'm temporarily giving up on Ubuntu"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by naceguy122 on 2007-11-08
I'm going to try Mandriva and hopefully learn enough to get back to Ubuntu eventually. I just have one quick question. If I install Mandriva over Ubuntu (currently by itself on my second hard drive), will it automatically remove the Ubuntu boot files from my dual boot, or should I do that manually before the install? Sorry for the semi-off-topic post, but the Mandriva forums have no active members, these are much better. 

By the way, you don't have to post lots of stuff about why I shouldn't leave. I gave Ubuntu a shot, and it's not right for me right now. Mandriva may not be either, but I'm going to try.

---

### Post by Perpetual on 2007-11-08
When you install Mandy, it will prompt you for the type of boot loader (lilo or grub) and where to install it.  If you have a single drive, the default location will overwrite your mbr and you will be fine.

Come on, stay, stay, stay!  :) Are you going Mandriva kde or gnome?

Edit: I also prefer the [MandrivaUsers.org Portal]("http://http://mandrivausers.org/").

---

### Post by ubnewbie2 on 2007-11-08
> **naceguy122 said:**
> I'm going to try Mandriva and hopefully learn enough to get back to Ubuntu eventually. I just have one quick question. If I install Mandriva over Ubuntu (currently by itself on my second hard drive), will it automatically remove the Ubuntu boot files from my dual boot, or should I do that manually before the install? Sorry for the semi-off-topic post, but the Mandriva forums have no active members, these are much better. 

By the way, you don't have to post lots of stuff about why I shouldn't leave. I gave Ubuntu a shot, and it's not right for me right now. Mandriva may not be either, but I'm going to try.

There are no boot files in the MBR, other than grub. It's menu and config are in the /boot/grub directory, as I undertsand it. 

If you install Mandriva in the same partition as Ubuntu used to be in, I am sure it will format the partition first, so all the grub config files from ubuntu will be gone, then Mandriva will set up grub (or lilo?) to boot to itself.  

I think it will all be fine.

---

### Post by Sef on 2007-11-08
> f I install Mandriva over Ubuntu (currently by itself on my second hard drive), will it automatically remove the Ubuntu boot files from my dual boot, or should I do that manually before the install?

It should overwrite the Ubuntu boot files and  install a boot manager.  

> Sorry for the semi-off-topic post, but the Mandriva forums have no active members, these are much better. 

Absolute Beginners states that it is "The perfect starting place to find out more about computers, Linux and Ubuntu," so there was no problem with you posting your question here.

> By the way, you don't have to post lots of stuff about why I shouldn't leave. I gave Ubuntu a shot, and it's not right for me right now. 

GNU/Linux is about choice.  Use the distro that is right for you.

> Mandriva may not be either, but I'm going to try.

Yes you have to give it a shot and see if it is for you.   You can always go into [Other OS Talk]("http://ubuntuforums.org/forumdisplay.php?f=147") and post your question there.

---

### Post by naceguy122 on 2007-11-08
> **Perpetual said:**
> When you install Mandy, it will prompt you for the type of boot loader (lilo or grub) and where to install it.  If you have a single drive, the default location will overwrite your mbr and you will be fine.

Come on, stay, stay, stay!  :) Are you going Mandriva kde or gnome?

Edit: I also prefer the [MandrivaUsers.org Portal]("http://http://mandrivausers.org/").

KDE. and i'll have to check out that other forum. i should be back, i like Ubuntu, but for now its just not for me.

thanks for the help!

---

