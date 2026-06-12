---
title: "How to Copy a CD"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by mvdberg112 on 2008-03-11
I've a bootable CD for Ubuntu and one for XP Pro. For both I want to make a backup copy, which should be and work exactly the same as the original.
How do I do that with Ubuntu?
I have Ubuntu 7.10, a DVD-RW, blank CDs and use Gnome Desktop. I know that in Places there is an option CD/DVD Creator. But I have difficulty using it, let alone making a one to one copy.

Thanks in advance.

---

### Post by jcwmoore on 2008-03-11
```
mkisofs -r NAMEOFFILE.iso /media/cdrom0
```

this code will make an ISO copy of your cd (that is mounted in cdrom0) to your current directory (the home directory by default)

---

### Post by sandysandy on 2008-03-11
> **mvdberg112 said:**
> I've a bootable CD for Ubuntu . want to make a backup copy, which should be and work exactly the same as the original.
How do I do that with Ubuntu?
I have Ubuntu 7.10, a DVD-RW, blank CDs and use Gnome Desktop. I know that in Places there is an option CD/DVD Creator. But I have difficulty using it, let alone making a one to one copy.

Thanks in advance.

have a look at these links for burning Ubuntu CD.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

regards

---

### Post by bumanie on 2008-03-12
> sudo apt-get install k3b
It is a good copying program and easy to use.

---

