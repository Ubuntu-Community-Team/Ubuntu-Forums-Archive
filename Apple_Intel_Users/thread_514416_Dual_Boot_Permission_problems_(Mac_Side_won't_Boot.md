---
title: "Dual Boot Permission problems (Mac Side won't Boot!)"
date: 2007-07-31
forum: Apple Intel Users
---

### Post by Yoshiwars on 2007-07-31
After mounting the Macintosh HD in Ubuntu on my Macbook and changing the permission on the drive the Mac side won't boot. So I was hoping there was a way of putting it back without having to restore the drive?

---

### Post by Torajima on 2007-07-31
> **Yoshiwars said:**
> After mounting the Macintosh HD in Ubuntu on my Macbook and changing the permission on the drive the Mac side won't boot. So I was hoping there was a way of putting it back without having to restore the drive?

You could try restarting from the OSX system disc, and then running "Repair Disk Permissions" in Disk Utility.

---

### Post by Yoshiwars on 2007-07-31
anything that can be done in ubuntu? because My disks are at my house and I'm gonna be at my uncle's till way later today. I can't write to the mac partition in Ubuntu anymore.

---

### Post by cyberdork33 on 2007-07-31
you can attempt to boot in single-user mode

---

### Post by ronocdh on 2007-07-31
> **Yoshiwars said:**
> anything that can be done in ubuntu? because My disks are at my house and I'm gonna be at my uncle's till way later today. I can't write to the mac partition in Ubuntu anymore.
Torajima's suggestion is IMO the best route. I think it'd be worth the wait to make sure the job is done right. That said, you should be able to edit permissions on the OS X partition from within Ubuntu by running **sudo nautilus** and right-clicking on any folders for which you want to modify the permissions. Be careful with that, though.

---

### Post by cyberdork33 on 2007-07-31
> **ronocdh said:**
> Torajima's suggestion is IMO the best route. I think it'd be worth the wait to make sure the job is done right. That said, you should be able to edit permissions on the OS X partition from within Ubuntu by running **sudo nautilus** and right-clicking on any folders for which you want to modify the permissions. Be careful with that, though.

I think that's what he has already done, thus the situation.

---

### Post by ronocdh on 2007-07-31
> **cyberdork33 said:**
> I think that's what he has already done, thus the situation.
AIUI, it's completely possible to "undo" any permission changes, but I understand if the post was a bit redundant. Can you explain (for my benefit) what you mean by booting in single user mode in OS X?

---

### Post by russo.mic on 2007-07-31
I think what you'd have to do is from ubuntu, change the permissions back to the user in OS X, which I don't think is possible.  So, I don't think there is a way in Ubuntu to repair the permissions.  Wait till you get the disks.

Ditto, what do you mean by single user mode?

---

### Post by cyberdork33 on 2007-07-31
Well, it is tough to do with refit, but you can hold CMD+s while booting to start in single user mode. Since refit stops right before the kernel is loaded, you have to select to boot OSX and VERY VERY quickly get that CMD+s combo and you will boot without any graphics and come to a commandline. It usually takes me a few tries before I can get it. there will be instructions to fix your filesystem, and how to mount it with read/write privs.

[http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh343.html](http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh343.html)
[http://en.wikipedia.org/wiki/Single_user_mode](http://en.wikipedia.org/wiki/Single_user_mode)
[http://www.westwind.com/reference/OS-X/commandline/single-user.html](http://www.westwind.com/reference/OS-X/commandline/single-user.html)

Yay UNIX!

---

### Post by Yoshiwars on 2007-08-01
the disk utility worked off the install disks. Thanks!

---

### Post by ronocdh on 2007-08-01
> **cyberdork33 said:**
> Well, it is tough to do with refit, but you can hold CMD+s while booting to start in single user mode. Since refit stops right before the kernel is loaded, you have to select to boot OSX and VERY VERY quickly get that CMD+s combo and you will boot without any graphics and come to a commandline. It usually takes me a few tries before I can get it. there will be instructions to fix your filesystem, and how to mount it with read/write privs.

[http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh343.html](http://docs.info.apple.com/article.html?path=Mac/10.4/en/mh343.html)
[http://en.wikipedia.org/wiki/Single_user_mode](http://en.wikipedia.org/wiki/Single_user_mode)
[http://www.westwind.com/reference/OS-X/commandline/single-user.html](http://www.westwind.com/reference/OS-X/commandline/single-user.html)

Yay UNIX!
Informative, thanks for posting this! Yoshiwars, congratulations on getting your system back.

---

### Post by cyberdork33 on 2007-08-01
> **ronocdh said:**
> Informative, thanks for posting this! Yoshiwars, congratulations on getting your system back.

Still off topic, but there are few other modes you can boot in too, such as verbose mode (you guessed it, CMD+v) that will show all the system messages scroll by instead of the white apple.

---

