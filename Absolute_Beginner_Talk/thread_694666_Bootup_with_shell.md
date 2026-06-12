---
title: "Bootup with shell?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by jonathanlukens on 2008-02-12
Hi all,

I have just installed Ubuntu on a Dell XPS 200.  Installation went by without a hitch; however, when I restarted and booted Ubuntu for the first time, bootup stalled on the boot scripts, and then said [OK].  Then I got a [B], and then [C] or [D], depending on what arrow key I pressed.  I hit enter, was asked for a password, then entered the password I had assigned to my user.  It said incorrect password, then asked for the machine's account name, then the password, and then in let me into shell.  I was under the impression that I would be taken directly into a shiny GUI?  I don't know Linux shell AT ALL... please help!

Thanks,
Jonathan

---

### Post by taurus on 2008-02-12
Did you use the desktop CD or the server CD when you installed it?  What happens when you run this command from a prompt, after you have logged in?

```
startx
```

---

### Post by jonathanlukens on 2008-02-12
Thank you for responding so quickly!!

I used the server CD.  when I ran that command, it asked me to install xinit, which I did.  I then got the following response when I ran startx again: 
xauth: creating new (etc.)
xauth: creating new (etc.)
xauth: creating new (etc.)
x: cannot stat etx/x11/x (no such file or directory), aborting
xinit: server error.

---

### Post by taurus on 2008-02-12
If you installed the server version, then there is no X and no window manager of any kind.  Therefore, you need to install it before you can run it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Jimcanoa on 2008-02-12
In any case, why did you install ubuntu server instead of the desktop one? What are you planning on doing with it? You can install any server that you want in the desktop edition. In fact the sole advantage of the server edition is that it won't install many unnecesary desktop environment programs for a server, therefore, installing a desktop environment defeats the purpose of using the server edition.

---

### Post by jonathanlukens on 2008-02-12
Thank you,

I now have the desktop working!  Very exciting.
I didn't realize that there was no window manager for the server edition, and I thought it would be so nice to have all those servers installed automatically (this is going to be a web development machine).  Now I just have to learn how to install programs in Linux...

---

### Post by taurus on 2008-02-12
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by emarkd on 2008-02-12
Installing programs is usually much simpler that in windows - so much so that many people try and make it harder than it should be.  Here's two good resources:

[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by jonathanlukens on 2008-02-12
Perhaps this should be a separate thread, but as long as everyone is being so helpful and friendly...
As mentioned, this computer is going to be a development box.  I seem to have successfully installed the Linux no-ip client.  I now want to configure Apache HTTP server and get a database running, etc.  Under System>Services, I can see Apache, PostgreSQL, and a bunch of other stuff.  However, I cannot seem to locate them on my file system.  Hints?
Thank you everyone for being so helpful.

---

