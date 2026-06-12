---
title: "How to Remaster Debian GNU/kFreeBSD ?"
date: 2012-08-31
forum: Any Other OS
---

### Post by Haghiri75 on 2012-08-31
Hi. 
I want to make a remastered Debian GNU/kFreeBSD. 

How can I remaster my Debian GNU/kFreeBSD ? ( May I use [remastersys]("http://remastersys.com")?)

Thanks.

---

### Post by lykwydchykyn on 2012-08-31
Remastered from what, exactly?  The installer CD, or a Live CD of some kind?

---

### Post by Haghiri75 on 2012-08-31
Debian GNU/kFreeBSD testing installer CD :)

---

### Post by lykwydchykyn on 2012-08-31
You can try remastersys, but I don't know that it'd work.

Are you just wanting to add custom packages to the installer?  I wonder if debian livehelper might be of use here.

You might check the options here:  [http://wiki.debian.org/DebianCustomCD/](http://wiki.debian.org/DebianCustomCD/)

Usually if it's a debian-supplied solution, it works on all supported platforms.

---

### Post by Haghiri75 on 2012-08-31
thanks buddy. 
i want to change defualt DE (KDE to GNOME ) and install many packages (:D) , i need to write an installer ( on C and GTK+).

---

### Post by lykwydchykyn on 2012-08-31
If you're writing your own graphical installer, you could maybe use livehelper to create a custom debian live disc with your installer on it.

---

### Post by Haghiri75 on 2012-08-31
> **lykwydchykyn said:**
> If you're writing your own graphical installer, you could maybe use livehelper to create a custom debian live disc with your installer on it.
I create a GTK+ Based GUI for debian gnu/kfreebsd text installer (blue screen :D) and I try to compile it on Debian GNU/kFreeBSD :)

---

### Post by Haghiri75 on 2012-09-02
I tried to create it with Remastersys but remastersys doesn't work successful . 
I'll try simple-cdd package from debian official repositories :)

---

