---
title: "Issues with installing / Updating! Mystery!"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Phjil on 2008-03-26
Hello Ubuntu Forums,

Now then... this is probably something very simple, but bear with me. 
I took the leap of faith into Linux last night, installing 7.10 onto my laptop. The install was quick and all was good. Updates were available (all 338 of them) so I just let it run and left it over night

This morning, it was all updated, and it requested a restart.

Restart

Login

Oh... where's Ubuntu. No more do I have the ubuntu environment. No brown desktop, not menu bar, just a blue screen with a button launcher in the top right corner and some icons (floppy drive, Deleted Items, File System) and nothing else.

Where's what I installed?!?!?
Help!

---

### Post by kesman on 2008-03-26
So do you get past login screen? Do you get any error message popups?

---

### Post by Phjil on 2008-03-26
OK, I think that just about says it all...
Seems to me that it's giving me the Xfce environment?
I'm sure that's wonderful, but it's not what I bargained for.

All suggestions received with great thanks.
Phjil

---

### Post by kesman on 2008-03-26
You can select the desktop environment in the screen where it asks for your username and password, under sessions menu. Select gnome.

---

### Post by Phjil on 2008-03-26
Ah... found that.
Sadly, that doesn't work. I select Gnome, and OK and then I get the log off / switch user / suspend, turn off etc. Click cancel, and I go back to the same place!

!!

---

### Post by kesman on 2008-03-26
I have never seen something this odd :D Are you sure you didn't download **Xubuntu** instead of **Ubuntu**? The main difference in these two are that Ubuntu runs with Gnome, Xubuntu with xfce. In any case, you should be able to install the normal ubuntu desktop from terminal. If you cannot access terminal in the XFCE environment, then you can press ctrl+alt+f2 in the login screen to open a second TTY, and log in with your username and password from there. Note that your password isn't shown when you type it, this is normal.
After this, run:
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

after installing, type
```

sudo shutdown -r now

```
to restart, and now you should have a working Gnome.

---

### Post by Phjil on 2008-03-26
Thanks for that!
Yes, it's a distro disk from a magazine, so it's definitely Ubuntu.
However, I seem to have fixed this issue by putting the disk back in and re-installing the system... and it all works fine. I must have done something wrong the first time round...

Thanks for your help. I will no doubt be back for more when I need it.
Cheers

Phjil

---

