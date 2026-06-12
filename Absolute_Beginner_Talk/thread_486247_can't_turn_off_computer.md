---
title: "can't turn off computer"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Bostonian on 2007-06-27
When clicking the shutdown button in the lop right, the only options are hibernate, lock screen, logout, and switch user.

I can use sudo shutdown, sudo init 0/6, ect, but other people use my computer who I don't want to give the root password to....plus it's a little annoying that turning off my computer is a process...

is there any way to get the reboot and shutdown options in the menu, or any ideas of an easier, password free way to shut down the computer?

---

### Post by SoloSalsa on 2007-06-27
I do not know how to fix that problem, but there may be a way around it.  Log out, and from the login, shut down.  Unless the option is missing from there, too...

---

### Post by tarek on 2007-06-27
are you using beryl or compiz by any chance?

---

### Post by Bohlio on 2007-06-27
same thing here, It doesnt bother me much though, I just log out, then shut down. And I am using Compiz

---

### Post by DSn0wMan on 2007-06-27
This used to happen on my lappy a long time ago. It seemed it was a compiz/ati(fglrx) problem. I think it went away when I swiched to the OSS driver.

---

### Post by tarek on 2007-06-27
I thought  so, Go to: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session")

There is sub topic called: Shutdown and reboot buttons in GNOME you'll find the solution there :)

tk

---

### Post by DSn0wMan on 2007-06-27
Ahh yes. Thanks for refreshing my memory. Thats why the OSS dirver fixed it. I did not need XGL as it has AIGLX.

---

### Post by kevinlang21 on 2007-06-29
where is startxgl.sh? and if i have aiglx, will this solution still work?

Thanks

---

### Post by tarek on 2007-06-29
> **kevinlang21 said:**
> where is startxgl.sh? and if i have aiglx, will this solution still work?

Thanks

startxgl.sh is a file you should create if you use the tutorial. If you don't then the file isn't in your system.

I don't know if it works with aiglx, search beryl wiki, you might find a setup for aiglx.

tk

---

### Post by zerobinary on 2007-06-29
i used to have this problem but the solution is so simple u can't believe in wait a long time for the first shut down maybe a day then i will shut down
and the shut down will get faster and faster

---

