---
title: "Tried installin RealTek drivers, now can't log into gnome session"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by sacedric on 2007-02-13
Sorry about the long subject line. I was trying to get the sound working on my machine, and thought let me check the Asus website for drivers. Sure enough right at the top of the page was "Realtek AC'97 Driver A3.56 for Linux.". Wahoo I thought. So I downloaded the zip file and followed instruction. It seemd to run through some sort of install process but then failed at the very end. So I kept looking around. I noticed that I could not open any more programs and not even a new terminal. So I restarted the machine. Now when I try and login, I get the following printed out to the ~/.xsession-errors file:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bruce"
/etc/gdm/Xsession: Beginning session startup...
/usr/bin/gnome-session: error while loading shared libraries: libasound.so.2: cannot open shared object file: no such file or directory

Any ideas what I messed up?

It recommended I should start a failsafe session and I tried that but had no idea where to go with just the terminal.
Thanks

---

### Post by georgeg54 on 2007-02-14
I have exactly the same problem on an AW9D-MAX, except that I downloaded the linux drivers from the Realtek site, ran the installation as suggested, and now no more gnome.

---

### Post by sacedric on 2007-02-14
Hey georgeg54, I found this when I googled "libasound.so.2 + ubuntu". I am going to try it tonight. 
[http://ubuntuforums.org/showthread.php?p=1887303](http://ubuntuforums.org/showthread.php?p=1887303)
Good luck.

---

### Post by georgeg54 on 2007-02-15
I also found the thread yesterday. I removed libasound, which then removed a lot of other programs, including the desktop. So then I had to reinstall the desktop and the programs that had been removed,. But I now have sound.

---

### Post by sacedric on 2007-02-16
> **georgeg54 said:**
> I also found the thread yesterday. I removed libasound, which then removed a lot of other programs, including the desktop. So then I had to reinstall the desktop and the programs that had been removed,. But I now have sound.

How did you get a list of all the programs that were un-installed from libasound? I started writing them down but could not keep up.

---

### Post by sandeepbharmoria on 2007-02-28
Hi,
      I am new to linux and i was also facing the same problem for libasound.s0.2 and was unable to start the gnome session and it last for two days...!!! But now i have resolved it using a different approach.
             1) I login through KDE
              2) Inserted mine linux drivers cd
             3) installed the alsa drivers using ./install
    and it had taken a little time. it asked me for mine card configuration and also i have configured the card as asked by the wizard.
              I logged off from the KDE and started again the Gnome and ..............now it's,............
                                     working:guitar: 
may this will help you to dignose your problem...

 Thanks
sandeep

---

