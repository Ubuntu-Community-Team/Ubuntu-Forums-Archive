---
title: "[SOLVED] X Server login Window"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by rom82 on 2008-04-05
Hello,

I discovered Ubuntu today so I'm a complete noob!!

I went into the "login window" options, that looked like this (i took this picture on internet):
[IMG]http://kirrus.co.uk/the-kirrus-blog/images/XDMCP_login.png[/IMG]

And thinking I could add a command here to start [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html") every time the system booted, I entered the command: **/opt/lampp/lampp start**

I restarted and now I get a "low-graphics mode" window that basically won't let me go further.

anyone has any idea on how to correct my mistake here?
I think this line should be in some file that I could modify in the recovery mode, so which file? What was the original command by default?

Thanks for your help!

---

### Post by wolfen69 on 2008-04-05
open terminal and
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

i guess you're not wasting any time diving right in and messing up your system!

here are a couple good sites about ubuntu [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) and [www.ubuntuguide.org](www.ubuntuguide.org)
good luck and have fun.

---

### Post by shawnjones on 2008-04-05
To start a process at startup you need to go to ->

System->Prefrences->Sessons

From there you can add a startup command.

Welcome to Ubuntu, good luck and have fun.

---

### Post by rom82 on 2008-04-05
> **wolfen69 said:**
> open terminal and
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

i guess you're not wasting any time diving right in and messing up your system!

here are a couple good sites about ubuntu [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) and [www.ubuntuguide.org](www.ubuntuguide.org)
good luck and have fun.

Hi, thanks for your help, I did this, chose my graphic driver and then rebooted but it didn't change anything, it's still in low-graphics mode :-k
My screen is not broken as I can see the ubuntu logo perfectly when it boots:
[[IMG]http://img388.imageshack.us/img388/7306/img2274xf6.th.jpg[/IMG]](http://img388.imageshack.us/my.php?image=img2274xf6.jpg)

By the way, on this "low-graphics" window, I have 3 options: configure, shutdown, continue. Whichever I choose I'll end up like this (it was already like this before I ran the reconfigure): 
[[IMG]http://img407.imageshack.us/img407/5228/img22731yo0.th.jpg[/IMG]](http://img407.imageshack.us/my.php?image=img22731yo0.jpg)

> **shawnjones said:**
> To start a process at startup you need to go to ->

System->Prefrences->Sessons

From there you can add a startup command.

Welcome to Ubuntu, good luck and have fun.
Thanks mate, it'll be useful once I'll have fixed this problem or probably formatted and reinstalled :)

---

### Post by shawnjones on 2008-04-05
Try using ALT-CTL-Backspace to kill the X server, if you get to a terminal you could type:

X -br -audit 0 

This should restart you X Server, then you can go back and change the command back to where it was before you changed it.

---

### Post by rom82 on 2008-04-05
> **shawnjones said:**
> Try using ALT-CTL-Backspace to kill the X server, if you get to a terminal you could type:

X -br -audit 0 

This should restart you X Server, then you can go back and change the command back to where it was before you changed it.

Ok, so I started in recovery mode, I typed that command but it showed a black screen with the low-graphics mouse pointer in the middle of it (big black cross)! Moving the mouse around was all I could do...

Then I did CTRL+ALT+BackSpace and I went back to that [screwed-up screen]("http://img407.imageshack.us/my.php?image=img22731yo0.jpg")...

BUT I actually found out that this screen is in fact the command line, so even if it doesn't show up what I write, it still knows it as I tried " X -br -audit 0 " and it showed back the black screen...

---

### Post by rom82 on 2008-04-05
YES!

I found how to revert back my changes:
[B]
cd /etc/gdm
mv gdm.conf-custom gdm.conf-custom-NO
cp gdm.conf gdm.conf-custom
reboot[/B]

Thanks to the grep command I could find this file :)
Thanks for your help guys :guitar:

---

