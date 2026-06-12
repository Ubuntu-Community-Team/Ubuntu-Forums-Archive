---
title: "Root issue"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by G_Stewart on 2007-02-23
I tried to find the answer within the posts and didn't find one, so...
OK, I ran SUSE, Mandrake and RedHat, in all of them you could log in as root using one of the bootloaders. On my Ubuntu system I cant. Why? Also, I have Kpackage installed, and when I try to load something (RPM or Deb) it tells me my root password is invalid.
When I load from the command line using SUDO, it works fine. Now, I can hear it already, just use the command line. I don't like it, I am a GUI guy all the way.
Help (if I haven't ticked you off:lolflag: )

---

### Post by taurus on 2007-02-23
Then use gksudo/kdesu for GUI apps.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fusiachi on 2007-02-23
You can login as root graphically.  It's not recommended.

As such, it's not a default setting.

---

### Post by G_Stewart on 2007-02-23
How do I use KDESU? Do I need to list the program I want to unpack or is KDESU a program in and of itself?

---

### Post by taurus on 2007-02-23
What exactly are you trying to install?  If you know a little more, perhaps I can show you the exact command to run to install it.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by G_Stewart on 2007-02-23
Ymessenger

---

### Post by taurus on 2007-02-23
What's the exact name of that program, especially the extension?

---

### Post by Maestro23 on 2007-02-23
> **G_Stewart said:**
> Ymessenger

Did you d/l the .deb from the Yahoo site?

---

### Post by G_Stewart on 2007-02-23
Here's what confuses me. I am using Kpackage to unpack the RPM (the deb wouldn't work, needed like 20 dependencies) it asks for the root password and I type it in and it just keeps requesting it.

Aaaarggggh!

---

### Post by steve.horsley on 2007-02-23
Ubuntu leaves the root account locked, for security reason. As Taurus says, you should use sudo to prefix commands that need root permissions, and this asks for your password, not the root password. You can get a full root command prompt with **sudo su**.

You should launch GUI apps with **gksu progname** or **kdesu progname**. In Gnome, you can create a launcher by right-clicking the desktop and entering the above commands or by right-clicking the Ubuntu logo and choosing the edit the menus. I don't know about KDE but it must be fairly similar.

---

### Post by G_Stewart on 2007-02-23
Thanks, I'll try that.

---

### Post by taurus on 2007-02-23
You mean something like ymessenger.rpm!  Then, you need alien to convert it to .deb before you can install it with dpkg command.

```
sudo aptitude update 
sudo aptitude install alien
alien ymessenger.rpm
sudo dpkg -i ymessenger.deb
```

---

### Post by G_Stewart on 2007-02-23
That did it... wooo hooo, thanks all.

---

### Post by Maestro23 on 2007-02-23
> **G_Stewart said:**
> That did it... wooo hooo, thanks all.

Good deal man.:)

---

