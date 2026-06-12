---
title: "Change Repository Indexes form CDROM to Internet Download"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Lunz on 2007-10-02
How do I Change Repository Indexes or the software source from CDROM to Internet Download?

[IMG]http://i226.photobucket.com/albums/dd269/lunzx/Screenshot.png[/IMG]

---

### Post by mindtrick on 2007-10-02
Untick the CD tick sources you want, close it. In the main screen of Synaptic hit Reload button.

---

### Post by Lunz on 2007-10-02
It still read the cdrom as default, i already unticked

[IMG]http://i226.photobucket.com/albums/dd269/lunzx/Screenshot-1.png[/IMG]

---

### Post by mindtrick on 2007-10-02
Try this? 
[http://becomingaccie.blogspot.com/2007/07/could-not-get-lock-varlibaptlistslock.html](http://becomingaccie.blogspot.com/2007/07/could-not-get-lock-varlibaptlistslock.html)

---

### Post by bodhi.zazen on 2007-10-02
close synaptic and update manager.

Open a terminal

Enter :```
gksu gedit /etc/apt/sources.list
```

Comment out (put a # at the start of) the line referring to your CDROM

Save and exit.

Re-start synaptic or Add/remove programs

---

### Post by Lunz on 2007-10-02
> **mindtrick said:**
> Try this? 
[http://becomingaccie.blogspot.com/2007/07/could-not-get-lock-varlibaptlistslock.html](http://becomingaccie.blogspot.com/2007/07/could-not-get-lock-varlibaptlistslock.html)

It works,many-many thanks you..:popcorn::popcorn::popcorn:

---

### Post by Lunz on 2007-10-02
> **bodhi.zazen said:**
> close synaptic and update manager.

Open a terminal

Enter :```
gksu gedit /etc/apt/sources.list
```

Comment out (put a # at the start of) the line referring to your CDROM

Save and exit.

Re-start synaptic or Add/remove programs

Thanks to you too....:popcorn:

---

