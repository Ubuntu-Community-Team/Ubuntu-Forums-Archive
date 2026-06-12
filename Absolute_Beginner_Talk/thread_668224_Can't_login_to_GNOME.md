---
title: "Can't login to GNOME"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2008-01-15
So I start my computer up, everything looks good. I can get to the GNOME login screen as usual and type in my name and password. But as soon as I hit Enter after typing my password, GNOME seems to hang or something. The little password dots fade a bit, as if Ubuntu's trying to log in, but nothing happens.

I tried going down to the Options/Settings button and selecting restart, but nothing happened. So I did Ctrl+Alt+Backspace and I got back to a loading screen where it seemed to be hanging on "Running local boot scripts (/etc/rc.local)". I also notice that the "Kernel events manager" had failed to load.

I used a LiveCD to peek at my rc.local and there's just a bunch of comments and then the line "exit 0".

The only cause I can think of is that I was using sysv-rc-conf to turn off some services (using [this guide]("http://www.linuxlove.org/2007/12/16/comprehensive-linux-system-services-list-explanation-and-recommendation/")) before I rebooted. I also removed my extra virtual terminals via [this guide]("http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php"). Maybe I turned something off I wasn't supposed to?

Thanks a ton!

---

### Post by RSLxH on 2008-01-15
> **hackle577 said:**
> So I start my computer up, everything looks good. I can get to the GNOME login screen as usual and type in my name and password. But as soon as I hit Enter after typing my password, GNOME seems to hang or something. The little password dots fade a bit, as if Ubuntu's trying to log in, but nothing happens.

I tried going down to the Options/Settings button and selecting restart, but nothing happened. So I did Ctrl+Alt+Backspace and I got back to a loading screen where it seemed to be hanging on "Running local boot scripts (/etc/rc.local)". I also notice that the "Kernel events manager" had failed to load.

I used a LiveCD to peek at my rc.local and there's just a bunch of comments and then the line "exit 0".

The only cause I can think of is that I was using sysv-rc-conf to turn off some services (using [this guide]("http://www.linuxlove.org/2007/12/16/comprehensive-linux-system-services-list-explanation-and-recommendation/")) before I rebooted. I also removed my extra virtual terminals via [this guide]("http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php"). Maybe I turned something off I wasn't supposed to?

Thanks a ton!

You have most definitely switched of a service that you shouldn't have. 

Run sysvconf (From the terminal: Not Gui like sysv-rc-conf) and restart the daemons on the list from that guide and try again.

---

### Post by hackle577 on 2008-01-15
I booted into recovery mode and tried to run "sysvconf" it says it can't be found. I tried to sudo apt-get install it and there isn't a package by that name.

Am I missing something obvious?

---

### Post by mikeyphi on 2008-01-15
> **hackle577 said:**
> I booted into recovery mode and tried to run "sysvconf" it says it can't be found. I tried to sudo apt-get install it and there isn't a package by that name.

Am I missing something obvious?

The package name is sysvconfig

---

