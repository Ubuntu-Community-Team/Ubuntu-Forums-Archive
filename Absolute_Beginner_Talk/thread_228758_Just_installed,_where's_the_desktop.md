---
title: "Just installed, where's the desktop?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by c_323_h on 2006-08-03
I just installed Ubuntu, choosing the LAMP server option. After it has finished installing, I reboot it and a command prompt (black screen like Microsoft's C prompt) comes up. It asks me for my user name and password. So I type it in but it doesn't take me to a desktop or any kind of user interface. It just goes to the next line. How to I get to the desktop if there is one? I will try to post a screenshot.

---

### Post by bensexson on 2006-08-03
The LAMP server does not have X windows by default.  If you want X try: sudo apt-get install ubuntu-desktop.

---

### Post by c_323_h on 2006-08-03
Okay, I did that then it says: 

Please insert the disc labeled 'Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20069531)' in the drive '/cdrom/' and press enter

Is this not the CD  installed from? This is the only CD I have.

---

### Post by Sammi on 2006-08-03
Does your CD not work?

And are you connected to the internet? If so then the apt-get command should try to fetch the ubuntu-desktop files from the official ubuntu repositories on the net. But then again I'm no expert.

---

### Post by -deadcats on 2006-08-03
You installed the Server version of Ubuntu. In general, most true Server environments run sans a GUI desktop.

So, as has been suggested, you can apt-get the ubuntu-desktop, GDM, etc., or you can download and install the Non-Server CD/DVD, then apt-get the LAMP packages. Your choice.

regards,
-dc

---

### Post by carlosqueso on 2006-08-03
> **c_323_h said:**
> Okay, I did that then it says: 

Please insert the disc labeled 'Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20069531)' in the drive '/cdrom/' and press enter

Is this not the CD  installed from? This is the only CD I have.

That is the CD....BTW, are you or can you be connected to the internet?

---

### Post by gizmoarena on 2006-08-03
why dont you just simply re-install the OS with GUI desktop option?

---

