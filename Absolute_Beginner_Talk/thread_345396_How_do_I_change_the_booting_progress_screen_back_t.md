---
title: "How do I change the booting progress screen back to Ubuntu once installed Kubuntu?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by kpham.p on 2007-01-24
Hi all,

I’ve installed and using Ubuntu for a while now, I decided to install kubuntu desktop on top of it to have both Gnome desktop and KDE Desktop Env, by using “sudo aptitude install kubuntu-desktop” command.  The problem is that, the Booting screen has replaced by Kubuntu, as well as the splash screen and the login screen.  But I'd like to keep the original Ubuntu Stuff, on boot up and login.

I’ve modify the /etc/X11/default-display-manager file to use GDM instead of KDM, and it works. I’m able to see the Login screen and my default Display manager is now Gnome.

I’m wondering is there any way that I can change the booting progress screen back to Ubuntu instead of kubuntu?

Many Thanks,
Kpham.p

---

### Post by JamieC on 2007-01-24
Open a new terminal window and run the following:
```

sudo cp /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`

```

Please post the output, too.

---

### Post by kpham.p on 2007-01-24
Thanks JamieC, for your quick reply.  I'm at work right now, but i'll try it ASAP when I get home and I'll Post back.

thanks again.
kpham.p

---

### Post by JamieC on 2007-01-24
You're welcome, as long as you don't get any output along the lines of "splash not found" it should be fine. Good luck!

---

