---
title: "anoyed"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by stevennp on 2007-05-07
Can't install any packages.  keeps coming up with errors relating to sudo not allowing it.

---

### Post by mustang on 2007-05-07
Hi steven,

can you please post the exact command you're using and the exact result you get from it?

---

### Post by taurus on 2007-05-07
It would be nice if you describe a little more about the error message and what did you run?  Then, it won't be so annoyed.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install **package_name**
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by fakie_flip on 2007-05-07
Post your exact error messages here.

---

### Post by stevennp on 2007-05-07
Sorry 4 being so vague...It's when Totem tries to automatically download a codec i get an error messege sayin that sudo wont allow it

---

### Post by stevennp on 2007-05-07
Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '48234820' '--set-selections-file' '/tmp/tmpuLEwoA' as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by taurus on 2007-05-07
What happens when you run these two commands, using the same password that you log in with?

```
sudo aptitude update
sudo aptitude upgrade
```

And for codecs, here's a link:  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by sailor2001 on 2007-05-07
synaptics  win32 codecs   first enable restricted repositories

---

### Post by stevennp on 2007-05-07
ok.  typed in those commands and now it does not do anything.  you click on apply to install the codec and it just goes back to the player and  says that the codec is requires

---

### Post by zvacet on 2007-05-07
system>administration>software properties>chek all boxes and reload.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

And just in case type in terminal

```
cat /etc/apt/sources.list
```

and post it here

---

### Post by jrlii on 2007-05-07
I haven't had any luck running video with Totem. Since I installed the codecs from the restricted archive Ogle has worked quite well.

IIRC I used the instructions at:

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

To install the codecs.

I've had the impression that the install plug-in feature in Totem does not work unless you are logged in as root, which isn't really a good idea. . .

---

### Post by fakie_flip on 2007-05-07
> **jrlii said:**
> I haven't had any luck running video with Totem. Since I installed the codecs from the restricted archive Ogle has worked quite well.

IIRC I used the instructions at:

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

To install the codecs.

I've had the impression that the install plug-in feature in Totem does not work unless you are logged in as root, which isn't really a good idea. . .

I recommend that you install totem-xine from Synaptic. It will say that it is going to remove totem-gstreamer. Don't worry about that. It is completely fine. Now almost any video will play in Totem. It is what I use.

---

